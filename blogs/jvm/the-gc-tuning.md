# 1. GC 调优思路

    针对特定场景, 特定目的去做.

对 GC 调优, 主要关注:
- 内存占用
- 延时
- 吞吐量
大多数情况下, 侧重于其中的一两个目标

调优思路总结:
1. 理解应用需求和问题, 确定调优目标.
2. 掌握 JVM 和 GC 的状态, 定位具体的问题, 确定真的有 GC 调优的必要. 可以通过 `jstat` 等工具查看 GC 等相关信息, 可以开启 GC 日志, 或者利用操作系统提供的诊断工具等, 比如通过追踪 GC 日志, 就可以查找是不是 GC 在特定时间发生了长时间的暂停, 进而导致了应用响应不及时;
3. 选择的 GC 类型是否符合我们的应用特征, 如果是, 具体表现在哪里, 是 Minor GC 过长, 还是 Mixed GC 等出现异常, 还可以考虑切换 GC 类型, 如 CMS 和 G1 都是更侧重于低延迟的 GC 选项;
4. 通过分析确定具体调整的参数或者软硬件设置;

# 2. 调优建议
1. 尽量升级到较新的 JDK 版本, 很多问题升级 JDK 就可以解决;
2. 掌握 GC 调优信息收集途径, 掌握尽量全面, 详细, 准确的信息, 是各种调优的基础
3. 如果发现 Young GC 非常耗时, 很可能是新生代太大了, 可以考虑减小新生代的最小比例, 这样可以降低延迟, 但会影响吞吐量;
4. 如果是 Mixed GC 延迟较长, 部分 Old GC 会被包含进 Mixed GC, 可以减少一次处理 Region 的个数.