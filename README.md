# 数据库系统原理与实现 db_impl_course

数据库系统原理与实现是华东师范大学数据学院开设一门数据库系统课程。

授课人[胡卉芪](https://faculty.ecnu.edu.cn/_s37/hhq2/main.psp), Github Link: https://github.com/dase314。

课程主要内容是当下数据库内核实现中的关键技术，主要包括存储，查询，事务，高可用四个方面。

## 课程内容

| Time | Content | Reading | Lab |
|------|---------|---------|-----|
| W1   | 课程介绍 | [课程简介、系统研究关注的内容、性能指标、课程要求][1] | [**Lab 1(W1):配置实验环境、编译并调试代码**][2] |
| W2   | 存储-传统数据库 | [KVS的接口与设计需求][3]，[B+tree][4],  [COW-B+tree][5]，[Page Structure，Database Buffer][6], [Cache Policy (i)][7]，[ii][8]，[Implement LRU—Cache][9] | [**Lab 2-1(W2):实现数据库Drop Table功能**][10] |
| W3   | 存储-Bitcast结构 | [Bitcast][11], [Log-structured store][12] | [**Lab 2-2(W3):向数据库中增加DATE字段**][10] |
| W4   | 存储-LSM-tree架构存储 | [Skiplist-LevelDB][13]，[LSM-tree structure & LevelDB][14]，[More about Compaction][15] | [**Lab 3-1(W4):在缓冲区中实现LRU淘汰算法**][16]<br/> [**Lab 3-2(W5):实现缓存管理器**][16] |
| W5   | 存储-并发索引 | [Memory Consistency Model][17]，[Concurrent Linklist(Lock coupling，Optimistic Read,Lazy Delete)][18]，[Concurrent Index][19] | [**Lab 5-1(W8):并发链表实现**][20] |
| W6   | 存储-其他 | [Memory Allocation][21]，[Snapshot][22], [Bloomfilter][23]，[Second Index][24]，[Compression][25], [Design Considerations for Database storage][26] | |
| W7   | 查询-执行引擎 | [SQL执行过程][27]，[火山模型][28] | [**Lab 4-1(W6): 实现多表查询功能**][29]<br/> [**Lab 4-2(W7): 聚合函数**][30] |
| W8   | 查询-算子实现 | [Join Algorithms，Grace Join，External Sort][31] | |
| W9   | 查询-查询优化器 | [Query Optimization][32] | |
| W10  | 事务-异常与隔离级别 | [Serializablity(i)][33], [Serializablity(ii)][34]，[Conflict Serializable][35], [Recoverability-Emory][36]，[Transaction Anomaly,Isolation Levels][37], [分布式一致性与隔离级别的关系][38] | |
| W11  | 事务-并发控制(一) | [2PL，S2PL，Basic Timestamp][39] | [**Lab 5-2(W10-W11):2PL算法实现**][40] |
| W12  | 事务-并发控制(二) | [OCC， MVCC，Snapshot Isolation][41] | [**Lab 5-3(W12):OCC算法实现**][42] |
| W13  | 事务-日志管理 | [日志与缓冲区关系][43]，[ARIES][44] | [**Final Project:实现 Order By 功能**][45] |
| W14  | 高可用-数据库备份，Raft(一) | [Raft Summary][46]，[Raft Paper][47] | |
| W15  | 高可用-Raft(二) | Reading: 见上 | [**Lab 6(W14-W17):实现Raft算法**][48] |
| W16  | 高可用-分布式一致性与Basic Paxos(一) | [Distributed consensus revised-Heidi Howard][49] | |
| W17  | 高可用-分布式一致性与Basic Paxos(二) | Reading: 见上 | |
| W18  | 分布式数据库主要技术扩展(MPP、分布式事务等) | Reading: 待补充| |

## 扩展内容： 可选

| Time | Content | Reading |
|------|---------|---------|
| E1   | Distributed Database Architecture | Reading: Share-noting, Share-data. Cloud Database |
| E2   | Storage | Reading: Data Partition, Consistent Hashing |
| E3   | Storage | Reading: More On LSM-tree |
| E4   | Transaction | Reading: Distributed Concurrency Control |
| E5   | Transaction | Reading: Atomic Commit |
| E6   | Consensus | Reading: There is more on consensus |
| E7   | Transaction+Consensus | Reading: Paxos Commit |
| E8   | Query | Reading: Exchange, Map-Reduce, Massive Parallel Execution |

## Reading List

PingCap整理的数据库论文：[PingCap整理的数据库论文][50]

---

[1]: https://github.com/dase314/dase314.github.io/blob/main/files/W1-Intro.pptx
[2]: https://spiky-sugar-cac.notion.site/Lab1-9af502d8216848d29a101e4749e04f95
[3]: https://github.com/dase314/dase314.github.io/blob/main/files/W2-KVS%E6%8E%A5%E5%8F%A3.pptx
[4]: https://www.geeksforgeeks.org/introduction-of-b-tree/?ref=lbp
[5]: http://www.bzero.se/ldapd/btree.html
[6]: https://github.com/dase314/dase314.github.io/blob/main/files/W4-BufferPool.pptx
[7]: https://www.geeksforgeeks.org/page-replacement-algorithms-in-operating-systems/
[8]: http://www.mathcs.emory.edu/~cheung/Courses/355/Syllabus/9-virtual-mem/SC-replace.html
[9]: https://github.com/dase314/dase314.github.io/blob/main/files/LRU.pdf
[10]: https://spiky-sugar-cac.notion.site/Lab2-Drop-Table-DATE-7580ea9d0cf748459d8ce327baee6384
[11]: https://github.com/dase314/dase314.github.io/blob/main/files/W2-Bitcast.pptx
[12]: http://blog.notdot.net/2009/12/Damn-Cool-Algorithms-Log-structured-storage
[13]: https://github.com/dase314/dase314.github.io/blob/main/files/skiplist-leveldb.pdf
[14]: https://github.com/dase314/dase314.github.io/blob/main/files/W2-LSM-tree.pptx
[15]: https://github.com/dase314/dase314.github.io/blob/main/files/MoreAboutCompaction.pdf
[16]: https://spiky-sugar-cac.notion.site/Lab3-LRU-d0438c03f465463e86d456dd33e01706
[17]: https://en.wikipedia.org/wiki/Linearizability
[18]: https://github.com/dase314/dase314.github.io/blob/main/files/W6-CC4OLL.pdf
[19]: https://github.com/dase314/dase314.github.io/blob/main/files/W6-CC4BplusTree.pdf
[20]: https://github.com/advancedalgebra/CC4OLL
[21]: https://github.com/dase314/dase314.github.io/blob/main/files/memory_allocator.pdf
[22]: https://github.com/dase314/dase314.github.io/blob/main/files/snapshot.pdf
[23]: https://en.wikipedia.org/wiki/Bloom_filter#:~:text=A%20Bloom%20filter%20is%20a,a%20member%20of%20a%20set.
[24]: https://github.com/dase314/dase314.github.io/blob/main/files/secondaryIndex.pdf
[25]: https://devopedia.org/database-compression#:~:text=While%20most%20compression%20algorithms%20are,techniques%20used%20in%20database%20applications.
[26]: https://github.com/dase314/dase314.github.io/blob/main/files/DesignConsideration.md
[27]: https://github.com/dase314/dase314.github.io/blob/main/files/query_overview.pdf
[28]: https://github.com/dase314/dase314.github.io/blob/main/files/Vocano%20Model.pdf
[29]: https://lightning-cheque-89b.notion.site/890c1ff52ba84a2e80d78def3d95dbf9
[30]: https://lightning-cheque-89b.notion.site/2ae475e71b884e3895e7009ae56de168
[31]: https://github.com/dase314/dase314.github.io/blob/main/files/join.pdf
[32]: https://en.wikipedia.org/wiki/Query_optimization#:~:text=Query%20optimization%20is%20a%20feature,SQL%20language%20to%20relational%20algebra.
[33]: https://github.com/dase314/dase314.github.io/blob/main/files/serializability%20i.pdf
[34]: https://github.com/dase314/dase314.github.io/blob/main/files/serializability%20ii.pdf
[35]: https://github.com/dase314/dase314.github.io/blob/main/files/conflict_serializability.pdf
[36]: https://en.wikipedia.org/wiki/Recoverability_(database)
[37]: https://github.com/dase314/dase314.github.io/blob/main/files/Isolation_Levels.pdf
[38]: https://www.researchgate.net/publication/221486507_The_Relationship_Between_Consistency_Levels_and_Isolation_Levels_in_Transactional_Systems
[39]: https://github.com/dase314/dase314.github.io/blob/main/files/2PL_and_S2PL.pdf
[40]: https://spiky-sugar-cac.notion.site/Lab5-2PL-cb9f6ac208af4d3196c94bede8e7e75e
[41]: https://github.com/dase314/dase314.github.io/blob/main/files/OCC_MVCC_Snapshot_Isolation.pdf
[42]: https://spiky-sugar-cac.notion.site/Lab5-OCC-Snapshot-423d71aa062440b7b5c669087cce9ae5
[43]: https://github.com/dase314/dase314.github.io/blob/main/files/log_buffer.pdf
[44]: https://github.com/dase314/dase314.github.io/blob/main/files/ARIES.pdf
[45]: https://spiky-sugar-cac.notion.site/Final-Project-d56af7af066d4f0b8966327efc6c4b26
[46]: https://github.com/dase314/dase314.github.io/blob/main/files/raft%20summary.pdf
[47]: https://github.com/dase314/dase314.github.io/blob/main/files/raft.pdf
[48]: https://spiky-sugar-cac.notion.site/Raft-Algorithm-9680aa1da7e04f2f8ed48501e93be9ef
[49]: https://github.com/dase314/dase314.github.io/blob/main/files/distributed-consensus-revised.pdf
[50]: https://github.com/pingcap/awesome-database-reading-list
