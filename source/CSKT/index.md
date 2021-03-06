---
title: 计算机知识树
date: 2019-05-13 14:42:09
---
[课程资源](https://github.com/Developer-Y/cs-video-courses)
# DS
- Algorithm
  - Greedy
  - Divide and Conque：适用于子问题独立
  - Dynamic Programming：子问题不独立，把子问题解决放入table，然后综合最优解
- [排序](https://github.com/fanjingdan012/JavaDetails/tree/master/sort)
  - 内部排序
    - 冒泡Bubble
    - 选择Select
    - 插入Insert
    - 希尔Shell
    - Quick sort
    - Merge sort
    - Heap sort
    - Binary sort
      - Bucket sort
    - Radix sort
  - 外部排序
    - 直接用virtual memory
    - Merge sort：分成n个文件，再merge
    - replacement selection:heap sort
    - multi-way merge
- Pattern matching
  - 暴力
  - Boyer-Moore
  - KMP
- 数据结构
  - [可视化](https://www.cs.usfca.edu/~galles/visualization/Algorithms.html)
  - Vector
    - Array Vector
      - Extendable Array Vector
    - Linked List Vector
  - List
  - [Queue](https://github.com/fanjingdan012/ds/blob/master/data-structure/src/main/java/queue/Queue.java)
    - `enqueue(Object element)`
    - `dequeue()`
    - `peekLast()`
    - `size()`

  - [Stack](https://github.com/fanjingdan012/ds/blob/master/data-structure/src/main/java/stack/Stack.java)
    - `top()`
    - `push(Object element)`
    - `pop()`
  - Tree
    - 二叉树
      - 术语
        - Complete Binary Tree:变成Array无空白的
        - Full Binary Tree：最后一层全满的
      - 遍历(就是看Visit在中间叫中序，前面交前序，后面叫后序)见[BST code](https://github.com/fanjingdan012/ds/blob/master/data-structure/src/main/java/tree/binary/search/BinarySeatchTreeImpl.java)
        - 深度优先（可以recursive，也可以弄个Stack）
          - Inorder traversal:LVR
          - Preorder traversal:VLR
          - Postorder traversal:LRV
          - Euler Tour Traversal:VLVRV
        - 广度优先（弄个queue）
      - [Huffman Tree](http://homes.sice.indiana.edu/yye/lab/teaching/spring2014-C343/huffman.php)
        - 统计每个字母出现的频率，
          - 次数少的编码长一点（靠近叶子），多的编码短一点（靠近根）
          - 实现压缩
        - 左子树编码0，右子树编码1，保证没有prefix
          - 可以解压缩
        - [代码](https://github.com/fanjingdan012/ds/blob/master/pj2-zip/src/main/java/zip/Zip.java)
      - Heap(Complete Binary Tree)
        - Max Tree：自己比左右孩子都大
        - Min Tree：自己比左右孩子都小
          - [code]([Heap](https://github.com/fanjingdan012/ds/blob/master/data-structure/src/main/java/tree/binary/BinaryMinHeapTree.java)
            - `findMin()`
            - `insert(Comparable x)`
            - `deleteMin()`
        - 可以做成 Priority queue
          - 用来找到第k个大的element
          - Priority queue的其他做法
            - array
            - linked list
            - ordered array
            - ordered linked list
        - 其他heap
          - d-heap
          - leftist Heap
          - Skew Heap
          - Binominal Queue
      - BST(Binary Search Tree),左孩子<自己，右孩子>自己
        - [code](https://github.com/fanjingdan012/ds/blob/master/data-structure/src/main/java/tree/binary/search/BinarySeatchTreeImpl.java)
        - C 先看是不是已经在树里，然后从根节点开始，大的往右塞，小的往左塞
        - R 根节点开始，大的往右找，小的往左找 `find(Comparable x)`
        - D
          - 删除没孩子和一个孩子的，不用说
          - 两个孩子的：把左子树最大的或者右子树最小的顶上来，再把顶包的删掉
        - [Splay Tree](https://fanjingdan012.github.io/2019/05/21/Splay-Tree-and-AVL-Tree/)：一套规则，用于提高BST的读效率，当node s 被读到，就进行splay，也就是说读得多的靠近根：
          - single rotation
          - double rotation
            - zigzag
            - zigzig(弄完还是不平衡的)
        - [AVL Tree](https://fanjingdan012.github.io/2019/05/21/Splay-Tree-and-AVL-Tree/)(Adelson-Velskii-Landis):平衡树
          - balance factor BF(node) = 左孩子高度-右孩子高度=-1,0,1
          - rotation：就是看长出来的树是右孩子的右孩子就是RR，依次类推，
            - single rotation
              - RR rotation
              - LL rotation
            - double rotation
              - LR rotation：zigzag
              - RL rotation：zigzag
    - 多路搜索树Multi-way Search Tree
      - d个孩子的树，内部Node有2到d−1个key-element对 (ki, oi)
      - 最左的孩子都<最左的key，其他子树依次按区间来
      - (2,4)Tree = 2-4 Tree = [2-3-4 Tree](https://fanjingdan012.github.io/2019/05/21/234-Tree-and-Red-Black-Tree/)（有1到3个key）
        - C 先插入，overflow再split，split就是把中间的数字提到parent上，剩下的变成兄弟
        - D 把右边最小的key提上来删掉，
          - 提太多了underflow，自己key空了
            - 左隔壁兄弟也只有一个key，和隔壁兄弟合并，从parent降个key下去
            - 左隔壁兄弟>=2个key，兄弟的key提上去给parent，parent的key降下来给自己
        - =[红黑树](https://fanjingdan012.github.io/2019/05/21/234-Tree-and-Red-Black-Tree/)
      - [B Tree](https://fanjingdan012.github.io/2019/05/21/B-Tree-B-plus-Tree-and-B-star-Tree/):为了适应做index的多路搜索树
  - 图Graph
    - 术语
      - `有向图directed graph (digraph)`/`无向图Undirected graph`：Edge有没有→
      - `Labeled Graph`：Vertex有没有label
      - vertexs are `adjacent`
      - An undirected graph is `connected`
      - `Directed acyclic graph (DAG)`有向无圈图
      - `free tree`:无向，无圈，connected，就是一个tree
      - `Strongly connected directed graph G`:每个节点之间都是全双工
      - `Strongly connected component`
      - `Degree( v ) `v节点上连的edge数，有向图还分`in-degree`,`out-degree`
    - graph的表示
      - Adjacency matrix:`array[v数][v数]`
      - adjacency list：`array[LinkedList]`
    - 遍历Traversal
      - 深度优先DFS
      - 广度优先BFS
      - 拓扑排序Topological Sort（哪些任务先做）
        - recursive
        - 用queue
        - 检测圈

    - [代码](https://github.com/fanjingdan012/ds/tree/master/data-structure/src/main/java/graph/Graph.java)
      - Vertex and Edge CRUD
      - shortest path
    - Minimum Spanning Trees（MST）：A minimum spanning tree of an undirected graph G is a tree formed from graph edges that connects all the vertices of G at lowest total cost
      - Prims Algoritnm
    - Single Source Shortest Path 从一个点出发计算到其他所有点的最短路径
      - weight=1： BFS即可
      - 有weight：dijkstra:从一个点出发计算到其他所有点的最短路径
        - `dijkstra(Vertex start,Vertex end)` return shortest path length，这里代码就只返回一个目标点
        - 就是维护一张vertex，cost，path（从哪个点走）的表，从start开始，遍历其他每个点，把知道的cost填进去，再看从其他点出发所有可到达的点的cost有没有更低的，不断循环直到所有点遍历完。
        - [动画](https://www.cs.usfca.edu/~galles/visualization/Dijkstra.html)
      - weight可以负的:不能求出最短路径:因为负权环可以无限制的降低总花费。
        - Bellman-Ford（动态规划）可以判断有无负权回路（若有，则不存在最短路），时效性较好，时间复杂度O（VE）
          - step1:初始化dist(i),除了初始点的值为0，其余都为infinit（表示无穷大，不可到达）,pred表示经过的前一个顶点
          - step2:执行n-1（n等于图中点的个数）次松弛计算：dist(j)=min( dist(i)+weight(i,j),dist(j) )
          - step3:再重复操作一次，如国dist(j) > distdist(i)+weight(i,j)表示途中存在从源点可达的权为负的回路。
          ```java
          int[] dist=new int[n];
          int[] pre=new int[n];
          
          public void Bellman_Ford(){
            //初始化
            for(int i=1;i<n-1;i++){
              dist[i]=infinit; //TODO
            }//end for
              
            dist[s]=0 //起始点的值  
            
            for (int i=1;i<=n-1;i++){
              for(int j=1;j<=edgenum; j++){
                if(dist(i)+weight(i,j) <dist(j) ){
                dist(j)=dist(i)+weight(i,j);
                pred(j)=i;
              }//end if
              }//end for
            }//end for
            
            //
            for(int j=1;j<=edgenum;j++){
              if(dist(i)+weight(i,j)<dist()j )
                return "有负权回路，不存在最短路径";
            }//end for
            
          }//e
          ```
      - A*算法
        - 作为启发式搜索算法中的一种，这是一种在图形平面上，有多个节点的路径，求出最低通过成本的算法。常用于游戏中的NPC的移动计算，或线上游戏的BOT的移动计算上。该算法像Dijkstra算法一样，可以找到一条最短路径；也像BFS一样，进行启发式的搜索。详细见http://blog.csdn.net/v_JULY_v/article/details/6093380
    - All pairs shortest path
      - dijkstra 用n遍
      - Floyd算法（动态规划）
    - 次最短路径
      - 将最短路径中边在图中去掉，然后再求一次最小生成树

# 数据库
- SQL
  - [index](https://fanjingdan012.github.io/2019/05/21/B-Tree-B-plus-Tree-and-B-star-Tree/)
    - index种类
      - Hash
      - Linear index(memory or disk)就是一串key/pointer,key是顺序排列的，pointer指向具体记录
      - tree
        - B(Balance) tree
        - B+树
        - B星树
    - 分类
      - 唯一索引
      - 主键索引
      - 聚集索引
      - 联合索引：将多个列组合在一起创建索引，可以覆盖多个列。（也叫复合索引，组合索引）, 需遵循最左匹配原则
      - 外键索引：只有InnoDB类型的表才可以使用外键索引，保证数据的一致性、完整性、和实现级联操作（基本不用）。
      - 全文索引：MySQL自带的全文索引只能用于MyISAM，并且只能对英文进行全文检索 （基本不用）
  - truncate删除表中数据，再插入时自增长id又从1开始
  - MySQL
    - show engines
    - select CURRENT_DATE();
    - set profiling = 1; show profiles; show profile for query 临时表ID
    - show status
    - show processlist
    - explain select * from a;
    - int(20)中20的含义，是指显示字符的长度，不影响内部存储，只是当定义了ZEROFILL时，前面补多少个 0
    - 触发器
      - Before/After intert
      - Before/After update
      - Before/After delete
- 事务
  - isolation级别
    - read uncommitted（读取未提交数据）
    - read committed（可以读取其他事务提交的数据）---大多数数据库默认的隔离级别
      - 问题：不可重复读
    - repeatable read（可重读）---MySQL默认的隔离级别
      - 问题：幻读
    - serializable（串行化）
      - 问题：其他线程会挂起
- 特性：ACID
  - Atomicity原子性
  - Consistency一致性
  - Isolation隔离层
  - Durability持久性
- 引擎
  - ISAM
    - 读取快，不占内存
    - 不支持Transaction，不能容错（磁盘崩溃），要经常备份
    - MySQL支持
  - MYISAM
    - ISAM+索引和字段管理。和Innodb不同，MyIASM中存储了表的行数，于是`SELECT COUNT(*) FROM TABLE`时只需要直接读取已经保存好的值而不需要进行全表扫描。
      - 表格锁定的机制
        - 优化并发读写
        - 需要经常运行OPTIMIZE TABLE命令，来恢复被更新机制所浪费的空间
    - 不支持事务，也不支持行级锁和外键，因此当INSERT(插入)或UPDATE(更新)数据时即写操作需要锁定整个表，效率低。
    - MySQL Default
    - 支持全文索引
    - 面向OLAP
    - 缓冲池只缓冲index，不缓冲data
    - 存储引擎表=MYD（data）+MYI（index），用myisampack压缩（用Huffman算法）
    - 单表大小：4GB（5.0以前），256TB（5.0以后）
  - HEAP
    - HEAP允许只驻留在内存里的临时表格。快，但不稳定，在数据行被删除的时候，HEAP也不会浪费大量的空间。HEAP表格在你需要使用SELECT表达式来选择和操控数据的时候非常有用。要记住，在用完表格之后就删除表格。
  - INNODB
    - 默认:
      - 隔离级别：可重复读
      - innodb_locks_unsafe_for_binlog=OFF
      - 采用gap locking
    - 支持事务处理和外来键
    - 行锁设计
    - 支持非锁定读（Oracle也支持），即读不会锁
    - next-key locking策略来避免phantom（幻读）
    - insert buffer
    - double write
    - adaptive hash index
    - read ahead
    - 采用clustered方式，按pk顺序存放，缺省默认pk：6 byte的RowId
    - 面向OLTP
    - 可存储在ibdata*的共享表空间，也可以存放于独立的.ibd文件的独立表空间
      - 共享表空间：某一个数据库的所有的表数据，索引文件全部放在一个文件中，默认这个共享表空间的文件路径在data目录下。 默认的文件名为:ibdata1 初始化为10M。可以将表空间分成多个文件存放到各个磁盘上（表空间文件大小不受表大小的限制，如一个表可以分布在不同的文件上）。数据和文件放在一起方便管理。但是删起来碎片不好清理。
      - 独立表空间：每一个表都将会生成以独立的文件方式来进行存储，每一个表都有一个.frm表描述文件，还有一个.ibd文件。 其中这个文件包括了单独一个表的数据内容以及索引内容，默认情况下它的存储位置也是在表的位置之中。表可能太大
  - BERKLEY
    - 支持事务处理和外来键
  - NDB集群引擎（share nothing）
    - 类似Oracle的RAC集群（share everything）
  - Memory存储引擎，以前叫HEAP
    - 默认用Hash index
  - Archive
  - Federated
  - Maria
    - MyISAM的后续版
    - 行锁
    - 支持缓存数据和index文件
    - 提供MVCC
    - 支持事务
    - BLOB优化
  - Merge CSV Sphinx Infobright
- 缓存
  - 缓存穿透
    - 就是attacker一直查询不存在的数据导致cache miss，就要一直去DB拿，导致DB压力太大挂掉
    - 解决
      - 布隆过滤器(所有数据hash到一个巨大的bitmap里，不存在就直接拦截)
      - 缓存该不存在的结果，设置很短的过期时间(5 min)
  - 缓存雪崩
    - cache设置了相同的过期时间，一瞬间一大波数据同时过期，就要一直去DB拿，导致DB压力太大挂掉
    - 解决
      - 加锁或queue保证单线程写，就没有大的DB压力
      - 在原有expire时间加一个1-5min随机，分散压力
  - 缓存击穿
    - 某数据在某刻很热门，刚好这时候expire，导致DB压力太大挂掉
    - 解决
      - mutex（可以用redis的SETNX或Memcache的ADD设一个mutex key，成功了就算拿到锁，去load db，否则重试 get）
      ```java
      public String get(key) {
        String value = redis.get(key);
        if (value == null) { //代表缓存值过期
            //设置3min的超时，防止del操作失败的时候，下次缓存过期一直不能load db
            if (redis.setnx(key_mutex, 1, 3 * 60) == 1) {  //代表设置成功
                value = db.get(key);
                redis.set(key, value, expire_secs);
                redis.del(key_mutex);
            } else {  //这个时候代表同时候的其他线程已经load db并回设到缓存了，这时候重试获取缓存值即可
                sleep(50);
                get(key);  //重试
            }
        } else {
            return value;
        }
      }
      ```
      - "提前"使用互斥锁(mutex key)
        - 在value内部设置1个超时值(timeout1), timeout1比实际的memcache timeout(timeout2)小。当从cache读取到timeout1发现它已经过期时候，马上延长timeout1并重新设置到cache。然后再从数据库加载数据并设置到cache中。
      - "永远不过期"
        - 就是自己写代码更新数据，可能老数据被访问到
      - 资源保护
        - 用hystrix


- 范式
  - 1NF：每column存一个值
  - 2NF：1NF+实体的属性完全依赖于主关键字（如果依赖一部分，就要分离开来）
  - 3NF：2NF+非键属性都只和候选键有相关性，也就是说非键属性之间应该是独立无关的
  - BCNF：3NF+主属性不能被非主属性决定
- MySQL
- ER Mapping
  - Hibernate
    - N+1问题
  - Mybatis

# CS
- [内存](https://fanjingdan012.github.io/2018/04/11/Memory-Hierachy/)
- 线程
- 并发
  - 对象的共享
    - 可见性
    - 线程封闭
      - ad-hoc
    - ThreadLocal：其实就是个Map
  - 对象的组合
  - 基础构建模块
    - 同步容器类
      - ConcurrentModificationException
      - 隐藏迭代器
    - 并发容器
      - ConcurrentHashMap
      - CopyOnWriteArrayList
    - 同步工具
      - latch
        - CountDownLatch
      - FutureTask
      - Semaphore
        - Mutex=Semaphore（1）
      - Barrier
        - Exchanger
        - CyclicBarrier
        - BrokenBarrierException
        - Volatile
          - Memory Barriers，汇编lock指令（缓存一致性机制）：一个处理器的缓存回写到内存会导致其他处理器的缓存无效
      - Phaser（jdk7）
      - 阻塞队列和生产者消费者模型
    - 任务执行
      - 创建线程
      - Executor框架（生产者消费者）
        - ThreadPool
          - interface
          ```
          public ThreadPoolExecutor(int corePoolSize,
                              int maximumPoolSize,
                              long keepAliveTime,
                              TimeUnit unit,
                              BlockingQueue<Runnable> workQueue)
          ```
          - fixed: corePoolSize = maximumPoolSize
          - workStealingPool
          - singleThreadExecutor: = fixed(1)
          - cached: corePoolSize = (0,Integer.MAX, 60,s)
          - scheduled
          - unconfigurableExecutorService
      - 分支主题
  - 活跃性危险
    - 死锁
    - 饥饿
    - 丢失信号
    - 活锁
  - 性能
    - amdahl定律:processors数对speed up的影响关系
    - 开销
      - 上下文切换
      - 内存同步
      - 阻塞
    - 减少开销
      - 缩小锁的范围
      - 减小锁的粒度
        - 锁分解：一个锁要保护多个相互独立的变量，可以拆成多个，分别保护变量
        - 锁分段：ConcurrentHashMap的实现，使用了16个锁的数组，每人保护Map的1/16(n mod 16)
          - 劣势：取得独占整个对象的锁更加麻烦
        - 避免热点域（比如操作很频繁地用到某个变量）
        - 替代独占锁
          - readWriteLock（读取不加锁，写加锁）
        - 不要用对象池
          - 本来new Object（）不需要同步，用了对象池就要了
  - 测试
  - 锁
    - 公平锁/非公平锁:先申请的先拿到/!
    - 可重入锁:外层拿到的锁内层自动拥有
    - 独享锁/共享锁：ReentrantLock、ReadWriteLock的Write/ReadWriteLock的Read
    - 互斥锁/读写锁：ReentrantLock/ReadWriteLock
    - 乐观锁/悲观锁：CAS/Lock
    - 分段锁
    - 锁的状态：偏向锁/轻量级锁/重量级锁
      - 偏向锁是指一段同步代码一直被一个线程所访问，那么该线程会自动获取锁。降低获取锁的代价。
      - 轻量级锁是指当锁是偏向锁的时候，被另一个线程所访问，偏向锁就会升级为轻量级锁，其他线程会通过自旋的形式尝试获取锁，不会阻塞，提高性能。
      - 重量级锁是指当锁为轻量级锁的时候，另一个线程虽然是自旋，但自旋不会一直持续下去，当自旋一定次数的时候，还没有获取到锁，就会进入阻塞，该锁膨胀为重量级锁。重量级锁会让其他申请的线程进入阻塞，性能降低。
    - 自旋锁spinlock：循环，减少Context Switch，但是消耗CPU
      ```
      while (抢锁(lock) == 没抢到) {}
      ```
    - 记录锁（Record Locks）/Gap Locks：锁定某一个范围内的索引，但不包括记录本身/间隙锁定（Next-Key Locks）：锁定一个范围内的索引，并且锁定记录本身   Next-Key Locks = Record Locks + Gap Locks
    - 条件Condition
- 海量数据
  - hash切分
  - 位图
  - 布隆过滤
  - hash表
  - 堆

# msa
- 分布式事务
  - 2PC反可伸缩模式的
  - X/open XA：一个约定，定义了一个协议是2PC
    - JTA（Java Transaction API）：XA的API定义
      - Atomikos：JTA的实现，适用于一个application instance操作多个数据库，要求数据库支持（mysql，oracle，db2...）
        - prepare-commit/rollback
        - 缺点
          - 性能，要等待所有线程返回yes才能提交
      - TCC:Atomikos提出的一篇论文，还没有实现，得自己写代码
        - try-Confirm/cancel
        - 优点
          - 假设有AB两个操作, 假设A操作耗时短, 那么A就能较快的完成自身的try-confirm-cancel流程, 释放资源. 无需等待B操作. 如果事后出现问题, 追加执行补偿性事务即可.
        - 注意点
          - 事务管理器(协调器)这个节点必须以带同步复制语义的高可用集群(HAC)方式部署.\n事务管理器(协调器)还需要使用多数派算法来避免集群发生脑裂问题.。脑裂：在阶段2中，如果只有部分参与者接收并执行了Commit请求，会导致节点数据不一致。
        - 适用
          - 红包, 收付款业务.
            - 实时性要求高，高度一致性要求
  - MQ
    - mq支持确认消息投递成功rabbitmq， activemq， rocketmq，kafka
    - 消息要求幂等性
    - A发出消息，mq存储消息，B消费，失败可反复投递，三次失败可以通知A回滚
  - LCN分布式框架
  - 3PC
    - CanCommit
    - PreCommit
      - undo和redo信息记录到事务日志中
    - DoCommit
      - 提交释放transaction资源
- CAP(下面三点只能同时保证两点）
  - 一致性(Consistency)
    - 强一致性：更新后，后续读取都得到新值
    - 弱一致性：更新后，可能读到老值。但经过“不一致时间窗口”期后，读取都是新值
      - 最终一致性：属于弱一致性，保证最终所有的访问都是最后更新的值。
        - 因果一致性。如果进程A通知进程B它已更新了一个数据项，那么进程B的后续访问将返回更新后的值，且一次写入将保证取代前一次写入。与进程A无因果关系的进程C的访问遵守一般的最终一致性规则。
        - “读己之所写（read-your-writes）”一致性。当进程A自己更新一个数据项之后，它总是访问到更新过的值，绝不会看到旧值。这是因果一致性模型的一个特例。
        - 会话（Session）一致性。这是上一个模型的实用版本，它把访问存储系统的进程放到会话的上下文中。只要会话还存在，系统就保证“读己之所写”一致性。如果由于某些失败情形令会话终止，就要建立新的会话，而且系统的保证不会延续到新的会话。
        - 单调（Monotonic）读一致性。如果进程已经看到过数据对象的某个值，那么任何后续访问都不会返回在那个值之前的值。
        - 单调写一致性。系统保证来自同一个进程的写操作顺序执行。要是系统不能保证这种程度的一致性，就非常难以编程了。
  - 可用性(Availability)
  - 分区容忍性(Partition tolerance)
  - 应用
    - CA:那就是不要分布式系统
    - CP:宁愿不给返回，也不要返回个错数据
      - Redis
      - HBase
      - Zookeeper
    - AP:可以暂时返回旧数据，保证高可用，实现BASE
  - 证明
    - 如果A和B是两个微服务，A和B的数据库是一样的，要做数据同步，A和B之间断网了，做不了同步，那么就只能
      - 牺牲C，返回一个旧数据
      - 牺牲A，不给返回
- Kubernetes
- 测试
  - montebank
  - pact
- Docker
  - Docker命令
    - docker images
    - docker ps
    - docker run
    - docker search
    - docker logs
    - docker cp
  - 镜像 容器 仓库
- etcd
- BASE（反ACID）
  - 牺牲高一致性，获得可用性或可靠性
- 发布
  - 蓝绿发布：50% 50%
  - 金丝雀发布：5%新的 95%老的
- 监控
  - Dynatrace
- SpringCloud
  - Hystrix
    - 应用场景
      - 服务降级
      - 异常处理
      - 请求缓存
      - 命令，分组，线程池划分
    - 容错原理
  - Zuul
  - Spring Cloud Config
  - Eureka
  - Ribbon
- 分布式缓存

# Java
- JVM
  - [GC](https://fanjingdan012.github.io/2019/04/10/GC/)
  - [JMM](https://fanjingdan012.github.io/2019/04/10/GC/Memory.png)
    - used
    - committed
    - max
    -initial
  - tools
    - jconsole
    - jmap
    - jstat
    - jcmd
    - jvisualVM
    - jmx
      - jmx client
      - jmx bean, program
    - jdb
  - class加载
    - class结构
      - Magic 0xCAFEBABE
      - Version
      - Constant Pool
      - Access_flag
      - This Class
      - Super Class
      - Interfaces
      - Fields
      - Methods
      - Class attributes
- concurrent 包
- lambda表达式
  - stream API
  - stream 原理 TODO

# C
- 存储类
  - auto 默认
  - register 存在寄存器里
  - static 在程序生命周期内一直不销毁，不创建
  - extern 对所有程序文件可见的全局变量的引用
- 指针
  - 普通指针 `int *p`
  - 函数指针 `int (* p)(int, int) = & max; //max 是个函数`
    - 调用： `d=p(a,b);`



# Spring
- Core
  - IOC
    - 控制的什么被反转了？就是：获得依赖对象的方式反转了。
    - [Bean的生命周期](https://czwer.github.io/2018/05/27/%E8%BF%91%E7%9C%8BBean%E5%AE%9E%E4%BE%8B%E7%94%9F%E6%88%90/)
      - Spring容器从XML中发现一个Bean的定义，然后初始化创建它们，使用依赖注入，Spring将这个Bean中需要的属性进行导入。
      - 如果这个Bean实现 BeanNameAware 接口, 工厂将调用setBeanName() 传递Bean的ID。
      - 如果bean实现BeanFactoryAware，工厂将调用 setBeanFactory(), 将自己的实例传给它。
      - 如果这个bean有 BeanPostProcessors 关联，他们的postProcessBeforeInitialization()方法将被调用。
      - 如果这个Bean有一个初始init方法，它将被调用。
      - 最后，如果有关联对象 BeanPostProcessors ，postProcessAfterInitialization()方法将被调用。
    - Bean的作用域scope(内嵌作用域不同的bean：因为动态代理)
      - singleton(default)
      - prototype
      - session
      - request
      - application
      - websocket
  - AOP
    - 静态代理
      - AspectJ
    - 动态代理
      - CGLib
        - [ASM](https://www.ibm.com/developerworks/cn/java/j-lo-asm30/index.html) 
      - JDK Proxy:必须有interface
      - SpringAOP=CGLib+JDK+AspectJ Annotations
        - 是interface就用JDK
    - Compile time weave
      - AspectJ ajc
        - ASM
      - AspectJ 编译后织入
        - ASM
      - JDK静态代理（自己手写Proxy）
    - Load time weave
      - AspectJ ltw
        - Java agent
    - Run time weave
      - Spring CGLib
        - CGLib
          - ASM
      - JDK proxy
    - 注意点
      - [代理对象不能获取Annotation](https://blog.csdn.net/frightingforambition/article/details/78842306)
  - [Transactional](https://czwer.github.io/2018/05/31/Spring%E4%BA%8B%E5%8A%A1%E7%AE%A1%E7%90%86%E5%8E%9F%E7%90%86/)
    - Propogation
      - Use Current Transaction
        - Currently No Transaction
          - just run without Transaction
            - SUPPORTS
          - Create New
            - REQUIRED
          - Throw Exception
            - MANDATORY
      - Create New
        - Currently Have Transaction
          - Suspend
            - REQUIRES_NEW: A{B}, A's connection != B's connection, A rollback->B can still commit, B rollback->A can still commit
      - No Transaction
        - Currently Have Transaction
          - Suspend: A{B}, A's transaction wait for B returns to continue, B runs without Transaction
            - NOT_SUPPORTED
          - Throw Exception
            - NEVER
      - NESTED: A{B}, A rollback->B rollback, B rollback->A can still commit
    - isolation
- Spring boot
- MVC
  - [手写简化逻辑的代码](https://github.com/fanjingdan012/simple-spring-mvc)
  - [IO](https://fanjingdan012.github.io/2019/05/07/csapp-IO)
    - BIO
    - 伪异步IO：就是普通BIO加个线程池
    - NIO
      - Reactor模式
      - Channel管道
      - Buffer
      - Selector
      - Netty 应用了零拷贝技术(Zero-Copy) linux2.1 sendfile(socket, file, len)
      - [io multiplexing](https://devarea.com/linux-io-multiplexing-select-vs-poll-vs-epoll/#.XhQ5tUf7RaQ) 用户需要自己从kernel copy 到user，会阻塞
        - [详解](https://segmentfault.com/a/1190000003063859#item-3-11) 在 select/poll中，进程只有在调用一定的方法后，内核才对所有监视的文件描述符进行扫描，而epoll事先通过epoll_ctl()来注册一 个文件描述符，一旦基于某个文件描述符就绪时，内核会采用类似callback的回调机制，迅速激活这个文件描述符，当进程调用epoll_wait() 时便得到通知。(此处去掉了遍历文件描述符，而是通过监听回调的的机制。这正是epoll的魅力所在。)
        - epoll
          - epoll_create: `int epoll_create(int size)`
          - epoll_ctl 添加，删除，更改 :`int epoll_ctl(int epfd, int op, int fd, struct epoll_event *event)`
          - epoll_wait: `int epoll_wait(int epfd, struct epoll_event * events, int maxevents, int timeout)`
          - 模式
            - level trigger（默认），收听到可以不立即处理
            - edge trigger，必须立即处理，否则以后收不到新消息
        - select
          - `int select(int nfds, fd_set *readfds, fd_set *writefds, fd_set *exceptfds, struct timeval *timeout);`
        - poll
          - `int poll (struct pollfd *fds, unsigned int nfds, int timeout);`
    - AIO(NIO2) 直接实现从kernel copy到user
  - test
    - mockito
      - 实现原理
    - powermock
  - JPA
    - CascadeType
      - ALL
      - PERSIST，MERGE，REMOVE，REFRESH
        - CRUD连着一起做
      - DETACH
        - 删自己的时候如果自己是别人的外键引用也脱离这个引用义无反顾的删掉
    - FetchType
      - LAZY
      - EAGER
  - Mybatis
    - 四大对象
      - Executor
      - StatementHandler
      - ParameterHandler
      - resultHandler
    - SqlSession顶层接口
    - 配置文件源码
  - Dubbo
    - Zookeeper
    - 例子
    - 源码阅读
  - Concurrent

# 软件工程
  - 软件设计原则
    - 单一职责原则SRP：一个类只负责一个领域的相应职责
    - 开闭原则：软件实体应对扩展开放，而对修改关闭
    - 里氏替换原则：所有引用基类的对象能够透明的使用其子类的对象
    - 依赖倒转原则IoC：抽象不应该依赖于细节，细节依赖于抽象
    - 接口隔离原则：使用多个专门的接口，而不是使用单一总接口
    - 合成复用原则Composite：尽量使用对象组合，而不是继承来达到复合目的
    - 迪米特法则Demeter：高内聚低耦合
  - [设计模式23](https://github.com/fanjingdan012/design-pattern)
    - 行为模式11
      - [策略模式](https://github.com/fanjingdan012/design-pattern/tree/master/strategy)
      - 模板方法
      - 备忘录模式
      - [状态模式]()
      - [访问者模式](https://github.com/fanjingdan012/design-pattern/tree/master/visitor)
      - [观察者模式（Observer）](https://github.com/fanjingdan012/design-pattern/tree/master/observer)
        - JedisSentinePool中master挂掉通知
      - [Iterator](https://github.com/fanjingdan012/design-pattern/tree/master/iterator)
      - 责任链模式
      - 命令模式
      - 中介者模式
      - 解释器模式
        - 编译器，运算表达式解析
    - 结构模式7
      - [Adapter](https://github.com/fanjingdan012/design-pattern/tree/master/adapter)
      - Bridge
      - [Composite](https://github.com/fanjingdan012/design-pattern/tree/master/composite)
      - decoration
      - Facade
      - Flyweight
      - Proxy
    - 创建模式5
      - [Factory](https://github.com/fanjingdan012/design-pattern/tree/master/factory)
      - [Singleton](https://github.com/fanjingdan012/design-pattern/tree/master/singleton)
      - Abstract Factory
      - Builder
      - Prototype

# AI
- 遗传算法
  - [code](https://github.com/fanjingdan012/ai-learn/tree/master/genetic-algorithm)
- BP神经网络
  - [code](https://github.com/fanjingdan012/ai-learn/tree/master/BP)
- 粗糙集
  - [code](https://github.com/fanjingdan012/ai-learn/tree/master/rough-set)
- 自然语言处理
- 分类

# 大数据
- Hadoop
  - HBase
    - HRegion
    - HMaster
    - HClient
  - HDFS
    - NameNode
    - DataNode
    - Client
  - Map/Reduce
  - Hive
- Spark
  - components
    - core
    - sql
    - streaming
    - MLlib
    - GraphX
  - RDD(resilient弹性 distributed dataset)
    - 分区partitions
    - 一个函数计算每个分区
    - 分区之间有依赖
    - 可选：对于键值对有一个partitioner（e.g.hash partitioner）
    - 可选：每一个分区有一串优先位置

# [网络](https://fanjingdan012.github.io/2019/05/09/Net)
- 五层协议
  - 物理层
    - 中继器，集线器，双绞线
    - IEEE 802.1A IEEE 802.2~802.11
  - 数据链路层
    - 网桥，以太网交换机，网卡=1.5层
    - FDDI， Ethernet， Arpanet， PDN， SLP, PPP
  - IP
    - 路由器，三层交换机
    - ICMP， ARP， RARP， AKP， UUCP
  - TCP/UDP
  - 应用层
    - DNS等
- web hook 就是个回调函数，允许在收到某消息时顺便做xx事


# 软件过程
- 瀑布
- Agile
- Scrum
  - Backlog Refine
  - Sprint Plan
  - Daily Scrum
  - In-Sprint Inspect
  - Sprint Review
  - Retro
  - Scrum of scrums（TPO APO ...）
- XP极限编程

# 中间件
- 内存数据库
  - redis
    - 连接：`redis-cli -a <password>`
    - 数据结构
      - [cheat sheet](https://gist.github.com/LeCoupa/1596b8f359ad8812c7271b5322c30946)
      - [底层数据结构](https://www.cnblogs.com/jaycekon/p/6227442.html)
      - String
      - Hash
        - hget,hset,hgetall
      - List 左右都开口
        - lpush,rpush,lpop,rpop,lrange
        - Redis list的实现为一个双向链表，即可以支持反向查找和遍历，更方便操作，不过带来了部分额外的内存开销，Redis内部的很多实现，包括发送缓冲队列等也都是用的这个数据结构。
      - Set
        - sadd,spop,smembers,sunion
      - Sorted Set
    - pub/sub
      - subscribe messages news
      - publish messages "Hi"-> will get 1
      - publish news "Great"-> will get 1, if no subscription will return 0

    - transaction
    - redis客户端
      - node: [ioredis](https://github.com/fanjingdan012/ioredis-learn))
      - JedisPool
      - Jediscluster
      - Redis案例
        - 缓存击穿
        - Redis雪崩
    - redis持久化
      - RDB(Redis DB file)
        - default
        - taking snapshots, creating point-in-time copies of the data
        - 灾备
      - AOF(Append-only file)
        - use logs to rebuild the database
        - 速度快
      - redis.(windows.)conf,改了要重启
        - save 900 1 表示900s后如果>=1key变了就save，可以配置
        - appendonly no/yes就开启了RDB和AOF两个
    - [redis集群](https://redis.io/topics/cluster-tutorial)
      - master-slave, redis.(windows.)conf，复制黏贴一个conf文件 ， redis-server redis2.(windows.)conf
        - slaveof 127.0.0.1 6379
        - appendfilename "appendonly2.aof" 别忘了改
        - port 6380 别忘了改
        - 两个会做sync
    - redis.conf
      - CONFIG SET SAVE "60 1"
      - requirepass somepwd(in master)
      - masterauth somepwd(in slave)
      - bind 127.0.0.1/protected-mode yes(两个要配合，一般不要改，如果该一定要设置protected-mode yes不要在公网暴露)
    - [哨兵Sentinel](https://redis.io/topics/sentinel)
      - 每个Sentinel以每秒钟一次的频率向它所知的Master，Slave以及其他 Sentinel 实例发送一个 PING 命令
      - 如果一个实例（instance）距离最后一次有效回复 PING 命令的时间超过 down-after-milliseconds 选项所指定的值， 则这个实例会被 Sentinel 标记为主观下线。
      - 如果一个Master被标记为主观下线，则正在监视这个Master的所有 Sentinel 要以每秒一次的频率确认Master的确进入了主观下线状态。
      - 当有足够数量的 Sentinel（大于等于配置文件指定的值）在指定的时间范围内确认Master的确进入了主观下线状态， 则Master会被标记为客观下线
      - 在一般情况下， 每个 Sentinel 会以每 10 秒一次的频率向它已知的所有Master，Slave发送 INFO 命令
      - 当Master被 Sentinel 标记为客观下线时，Sentinel 向下线的 Master 的所有 Slave 发送 INFO 命令的频率会从 10 秒一次改为每秒一次
      - 若没有足够数量的 Sentinel 同意 Master 已经下线， Master 的客观下线状态就会被移除。
      - 若 Master 重新向 Sentinel 的 PING 命令返回有效回复， Master 的主观下线状态就会被移除。
  - memcached
    - 缓存击穿
- mq
  - rabbitmq
  - rocketmq
  - kafka
    - NIO
    - Zero-Copy
    - 磁盘顺序读写
    - Queue极致使用
- docker
- Nginx
- Zookeeper
  - Client API
  - 应用场景
    - 数据发布订阅
    - 负载均衡服务机制
    - 命名服务
    - 分布式通知协助机制
  - 集群
    - Zab协议
    - 集群数据同步机制
- Tomcat

# Security安全
- 密码学
  - 要求保密性（Confidentiality）和完整性（Integrity），
  - cryptosystem=(E,D,p,K,C)即(Encryption algorithm, Decryption, plaintext, Keys, Cipher texts)
  - Kerckhoffs假设：秘密全藏在密钥里
  - 术语
    - cryptology
      - cryptography：加密
      - cryptanalysis：解密
  - 加密
    - Substitution：替换
    - Transposition：换位置
    - Product：以上两个结合，反复弄
    - input顺序：block，stream
  - Steganography：传输效率低
    - 藏在长message里
    - 看不见的墨水
    - 在噪音图片和声音里隐藏信息
      - 数字水印
      - 伪装保密通信：在普通图片里藏个机密图片之类的
  - 古典加密技术
    - 羊皮传书
    - 藏头诗
    - Caesar：Substitution
      - [code](https://github.com/fanjingdan012/JavaDetails/blob/master/security/src/main/java/crypt/Cesar.java)
      - 改进：Monoalphabetic Cypher替换字母表，理论上有26!种key，但是语言学上说有些字母用得更频繁
      - 再改进：一对多Vigenere，多对一Playfair
      - Polyalphabetic Ciphers：再多一个key来选择用哪个字母表
        - Vigenere Cipher，一串k1k2...kn来决定是Caesar几字母表，每隔n个letter就换字母表
        - One-Time Pad，一次一密绝对安全
    - Transposition：换位置
      - Rail Fence cipher:信息W状写成两行，再按行拼接形成密文
      - Row Transposition Ciphers
    - Enigma:Product
      - [code](https://github.com/fanjingdan012/JavaDetails/blob/master/security/src/main/java/crypt/Enigma.java)
  - 对称Symmetric：加解密一个密钥
    - DES（Data Encryption Standard）
      - Claude Shannon提出用Confusion和Deffusion来构造Substitution-Permutation network（SPN）
      - Feistel cipher实现了SPN
    - AES：DES的改进版
      - [加密模式](https://www.cnblogs.com/starwolf/p/3365834.html)
        - ECB (Electonic Code Book)
        - CBC (Cipher Block Chaining)
        - CTR (Counter)
        - CFB (Cipher Feed Back)
        - OFB (Output Feed Back)
        - [AES-GCM](https://www.jianshu.com/p/29b1ef3f84dc)

  - 非对称Asymmetric
    - RSA
      - [原理解释](https://github.com/fanjingdan012/JavaDetails/blob/master/security/src/main/java/crypt/RSAImpl.java)
      - [数学原理解释](https://cnodejs.org/topic/5bb9c31e15e4fd1923f48d0b)
      - [密钥存储格式](http://github.tiankonguse.com/blog/2017/07/01/ASN1-SRA.html)
      - 攻击方式
        - 暴力头尾+中间
        - 共模攻击：不同public key加密同一个plainText，因为`C=plainMsg^e mod n`，根据"中国剩余定理"可以算出plainText，但不能得到private key，[CTF sample](https://github.com/fanjingdan012/JavaDetails/blob/master/security/src/test/java/crypt/RSAImplTest.java)
        - 密码太短，直接辗转相除，分解质因数
  - 消息认证码
    - MAC(Message Authentication Code)
    - Hash，有些简单hash直接google一下就出来了
      - MD5
        - MD2,MD4(x)
      - SHA
        - SHA-1(x)
        - SHA-256
        - SHA-384
        - SHA-512
      - RIPEMD-160
  - Key
    - PBKDF1/PBKDF2 (Password-Based Key Derivation Function)
- 编码
  - ascii
  - Base64, Base32, Base16
  - 培根密码，AB替换字母
  - 摩尔斯电码
- 综合案例
  - [bitcoin]()
- Identification：这个用户是谁
  - IdP


- Authentication：提供password，token，certificate等来证明这个用户的确是他自己
  - SAML Authentication(Security Assertion Markup Language)
    - 在IdP和SP(Service Provider)之间用Bearer消息来传递Authentication和Role等信息
  - Web Tokens
    - [JWT(JSON Web Tokens)](https://jwt.io/#encoded-jwt)
      - Header
        - "alg": "HS256",  "typ": "JWT"等
      - Payload
        - ROLE,SCOPE,Username等
      - verify signature
        - 可以用hash:HMACSHA256
        - 可以用RSA签名
  - OAuth2
    - 5角色，sample：某app集成wechat
      - 客户端（Client）某app在wechat的开发者中心注册的app
      - 用户代理（User Agent）某app用户的browser
      - 资源所有者（Resource Owner）某app用户（同时是wechat用户）
      - 授权服务器（Authorization Server）wechat的IDP
      - 资源服务器（Resource Server）wechat的数据服务器
  - Kerberos 三头狗
- Authorization：这个用户是不是允许访问这些资源，他是什么role，role含有哪些权限

- OWASP&CTF
  - [web-hacking-101](https://wizardforcel.gitbooks.io/web-hacking-101/content/)
    -
  - C语言
    - buffer overflow
      - 命令行输入0x0：Ctrl+Shift+2
    - printf 格式化字符串攻击
  - sql injection
    - nosql injection
  - 图片
    - common
      - 文件meta
      - StegSolve
    - jpg
      - FFD8~FFD9
        - copy命令
    - png
      - 改高度
    - 小色差
  - xml攻击
  - reverse shell
  - pentest
    - tools
      - ZAP
        - active scan
        - passive scan


# Linux
