# 1. MySQL查询架构
![](http://oetw0yrii.bkt.clouddn.com/18-7-9/67650560.jpg)
1. 如果 SQL 命中缓存, 直接返回结果
2. 经过解析器和预处理器对 SQL 语句进行处理，最终由查询优化器生成执行计划。类似于 JVM 加载 Class 文件的过程，最终会生成和底层预定的协议格式。
3. 执行SQL返回结果集合

# 2. 建立索引的目的
1. 提高查询效率: 底层索引维持了树结构，可以很快捷的根据查询条件进行数据查找。
2. 约束作用(IOT): 比如唯一性约束用来限制不受主键约束的列上的数据的唯一性，用于作为访问某行的可选手段，一个表上可以放置多个唯一性约束。唯一性约束在支付系统、高并发业务场景中发挥了重要作用，可防止生成多条帐户信息。
3. 控制数据分布: `InnoDB` 中索引和数据是一起存储在文件系统中的，所以不同的索引建立方式可能存在数据分布问题。

# 3. 常见索引算法
## 3.1 B+树
### 3.1.1 B+树的特性
1. B+树 的特点是能够保持数据稳定有序, 其插入与修改拥有较稳定的对数时间复杂度;
2. B+树 中分支结点有m个关键字, 其叶子结点也有 m 个;
3. B+树 非叶子节点的关键字只起到索引作用, 实际的关键字存储在叶子节点;
4. B+树 的分支结点仅仅存储着关键字信息和子女的指针, 也就是说内部结点仅仅包含着索引信息;
5. B+树 需要通过索引找到叶子结点中的数据才结束，也就是说 B+树 的搜索过程中走了一条从根结点到叶子结点的路径。

### 3.1.2 B+ 树插入数据规则