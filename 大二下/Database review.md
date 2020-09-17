drop table <name>

alter table <name> add/drop <attributes>

select (distinct/all/*) <attribute> from <tablename> (as X) where <clause>

**String operations**

match the string "...in..."

`like '%in%'`





ordering the tuples
    order by <attributes> (desc) 

is null

Aggregate Functions
    avg() , min() , max() , sum() , count()
    having clause

Nested Subqueries

Subqueries in the Where Clause
    <Some> Clause
    <All> Clause

Empty Relations
    <exists>
    <not exists>

Subqueries in the From Clause
<With> Clause (create new template tables)
Subqueries in the Select Clause
Scalar subquery 

$\color{lightblue}{Modification\ of\ the\ Database}$

**Insertion**  
  `Insert into <table> values ();`

  `Insert into <table> select () from <table>`

**Deletion**

  `delete from <table> where <whereclause>`

**Updates**

  `update <table> set <new values> where <clause>`

**Case Statement for conditional updates**

    update <table> set <attributes> = case
    when <cluase> then <clause> else <clause> end

**Updates with Scalar Subqueries**



$\color{lightblue}{Ch4\ Intermediate\ SQL}$

* ### **Join Expressions**

  usually used in the **from** clause

  **Right/Left/Full** Outer Join  


* Views

  * allow updates only on simple views.

   `create view v as <query expression>`//query expression is any legal SQL expression. View name is represented by *v*.

* Transactions

  * Atomic transaction
  * Isolation from concurrent transactions
  * Transactions begin implicitly

* Integrity Constraints

  *  **not null**
  *  **primary key**
  *  **unique**
  *  **check(p)**, where **P** is a predicate
     *  `create assertion <assertion-name> check <predicate>`
  *  Cascading Actions
     *   set null
     *   set default
     *   on delete cascade
     *   on update cascade

* SQL Data Types and Schemas

  * Built-in Data Types : date, time, timestamp, interval
  * **Index Creation**
    * `create index <index-name> on <table>(attributes)`
  * User-Defined Types
    * `create type <datatype> as <predicate>`
  * Domain
    * `create domain <domain-name> <basic-type> constraint...`

* Authorization

  `grant <priviilege list> on <relation name or view name> to <user list>`

  `revoke <privilege list> on <relation name or view name> from <user list>`

  * \<user list> is : a user-id ; **public** ; a role
  * Authorization on parts of the database
    * Read、 Insert、 Update、 Delete
  * Authorization to modify the database schema
    * Index、 Resources、 Alteration、 Drop
  * Privileges in SQL
    * select insert update delete all privileges
  * Roles 
    * `create role <role-name>;`
    * privileges can be granted to roles
    * Roles can be granted to users, as well as to other roles



##  Ch7 Entity-Relationship Model

* Design Phases
  * Is to characterize fully the data needs of the prospective database users.
  * Design Approaches
    * Entity Relationship Model
    * Normalization Theory
* Outline of the ER Model
  * Entity and Relationship
    * An entity (have attributes) is an **object** that exists and is distinguishable from other objects.
    * An entity is represented by a set of attributes.
      * Attribute types 
        * Simple and Composite
        * Single-valued and Multivalued
        * Derived
    * A **relationship** is an association among several entities.

*  Constraints
  * Mapping Cardinality Constraints
    * one to one: 
    * one to many
    * many to one
    * many to many
  * Participation
    * total and partial participation (all or some entities)
  * Keys
    * super key -> candidate key -> primary key
* Redundant Attributes
  * Attributes appears in both entity sets.
* E-R Diagram
  * Weak Entity Sets : does not have a primary key
    * primary key : primary key of strong entity + discriminator
  * Symbols in E-R Notation![image-20200807133831012](C:\Users\Echo-\AppData\Roaming\Typora\typora-user-images\image-20200807133831012.png)![image-20200807134016490](C:\Users\Echo-\AppData\Roaming\Typora\typora-user-images\image-20200807134016490.png)
* Design Issues
  * when to use ...
    * entity sets vs. attributes
    * entity sets vs. relationship sets
    * binary versus n-ary relationship sets
    * placement of relationship attributes
* Extended E-       R Features
  * Specialization (Top-down)
  * Generalization (Bottom-up)
  * ISA relationship also referred to as **superclass - subclass** relationship
  * Constraints
    * disjoint
    * overlapping
    * completeness (total / partial)
  * Aggregation
* Design Process
  * Method 1
    * 确定实体类型
    * 确定联系类型
    * 连接实体和联系
    * 确定实体和联系的属性
    * 确定实体类型的码
  * Method 2
    * 确定实体类型
    * 确定实体属性
    * 确定联系类型和属性
    * 连接实体和联系
    * 加上实体和联系的属性，并确定实体类型的码
* Reduction to Relational Schemas 





## Ch8 Relational Database Design

#### 数据异常

* 数据冗余
* 插入异常
* 删除异常
* 更新异常



#### 关系模式

R<U,D,Dom,F>

R<U,F> 表名，属性集合，U的数据依赖集



#### 数据依赖：

* 函数依赖 (Functional dependency)

  任意t~1~、t~2~∈r, 如果t~1~[X]=t~2~[X]，有t~!~[Y]=t~2~[Y]，则称X决定函数Y，或Y函数依赖于X，记作X->Y。

  ​	语义范畴概念。反映了语义完整性约束

  ​	与时间无关，与属性之间的练习类型有关

  * 
    * 平凡/非平凡函数依赖：决定子集
    * 完全/部分函数依赖：是否由所有属性决定
    * 传递函数依赖

* 多值依赖



#### 范式判定：

##### Armstrong公理

* 逻辑蕴含
  * 自反律(Reflexivity)
  * 增广律(Augmentation)![image-20200812013623996](C:\Users\Echo-\AppData\Roaming\Typora\typora-user-images\image-20200812013623996.png)
  * 传递律(Transitivity)
  * 合并律
  * 伪传递
  * 分解
* 函数依赖集闭包：在关系模式$R<U,F>$中为$F$所逻辑蕴含的函数依赖的全体叫作**$F$的闭包**，记为$F^+$
  * 判断$X\rightarrow Y$是否能由$F$推出
  * 判断属性集合$X$是否为超码

* 属性集闭包：$F$是$U$上的一组函数依赖，$X \subseteq U$ ,$X_F^+ = \{A|X\rightarrow A\ \ \ 能由F根据Armstrong公理推出\}$，$X_F^+$称为属性集$X$关于函数依赖集$F$的闭包
* 无关属性(extraneous attribute)
* 正则覆盖(canonical cover)   $F_c$：不含无关属性，函数依赖左半部唯一

#### 模式分解 ：

**保持函数依赖**分解和**无损连接**分解

* 无损连接性(Lossless join)：模式分解后的自然连接结果相等

  * 保证不丢信息，不一定能解决数据异常

  * 若$R$的分解为$\rho=\{R_1,R_2\}$，$F$为$R$上的函数依赖集合，则lossless join 的充要条件为

       ​                                                      $R_1\bigcap R_2\ \rightarrow R_1或R_2$

* 函数依赖(preserve function dependency)



#### 范式

通过模式分解将低级范式转换为若干个高级范式（规范化）

主属性（非主属性）：候选码中的主属性

* 1NF：关系中每一分量（entry）不可再分
* 2NF：每个非主属性完全依赖与R的码（消除非主属性对码的部分依赖）
* 3NF：任何非主属性不传递依赖与码（算法：图8-12）
* BCNF：若有$X\rightarrow Y$ ，则$X$是超码 (算法：图8-11) 
* 4NF
* 5NF





## Ch11: Indexing and Hashing

speed up 

also is a kind of data

* Basic Concepts
  * search-key | pointer
  * Evaluation Metrics
    * Access types supported efficiently
    * Access time
    * Insertion time
    * Deletion time
    * Space overhead



#### Ordered Indices

* 
  * **Primary**(clustering) index: 建立在有序文件上的有序字段的索引
  * Secondary Indices: 辅助索引(dense Index)
  * **Dense** Index: records every search-key value 
  * **Sparse** Index: contains index records for only some search-key values.
    * 分块存储，以块为单位读取传输，选取每块第一条search-key作为Index
  * Multilevel Index
    * 多级索引小，可常驻内存，减少I/O次数
  * Updates
    * Deletion
    * Insertion

* B^+^-Tree Index

  ​	Pointer|search-key

  * root to leaf : the same length
  * node : n/2 - n children

* Hashing indices

  * Static Hashing
    * bucket size: block (having overflow bucket)
    * space utilization (50%-80%)
  * Dynamic Hashing
    * Extensible Hash Tables 
      * hash function h(k) is  a b(large enough) bits binary sequence, first *i* bits represents the current number of buckets
    * Liner Hash Tables
      * 只有当桶的填充度达到超过某个比例后桶数才开始增长
      *  $r\leq 1.7n\ \ \ r为记录数，n为桶数$  

* Comparison of Ordered Indexing and Hashing

* Bitmap Indices

  * 适用于多值查询

* Index Definition in SQL

* Multiple-Key Access







## Ch12: Query Processing

### Overview

query

Parsing and translation

Evaluation

Optimization

* 减少中间运算结果

expression tree

execution plan

### Measures of Query Cost

**disk access**

* number of seeks : $t_S:\ time\ for\ one\ seek$ 
* number of blocks read/written (write is greater than read) :  $t_T:\ time\ to\ transfer\ one\ block$ 
* cost :  $b* t_T + S* t_S$ 

### Selection Operation

file scan : A1(linear search) 

* normal selection : $cost\ estimate = b_r\ block\ transfers + 1\ seek$
* selection on a key attribute : $cost = (b_r/2)\ block\ transfers + 1\ seek$

Index scan

* A2(primary index, equality on key) single : $cost = (h_i+1)*(t_S+t_T)\ \ \ h_i:树高$ 
* A3(primary index, equality on nonkey) Retrieve multiple records : $h_i*(t_S+t_T)+t_S+b*t_T$ 
* A4(secondary index, equality on nonkey) 
  * single : $cost = (h_i+1)*(t_S+t_T)$ 
  * multiple : $cost = (h_i+n)*(t_S+t_T)$ 
* A5(primary index, comparison) : $h_i*(t_S+t_T)+t_S+b*t_T$ 
* A6(secondary index, comparison) : $cost = (h_i+n)*(t_S+t_T)$ 

complex selections

* A7(conjunctive selection using one index)
* A8(conjunctive selection using composite index)
* A9(conjunctive selection by intersection of identifiers)

### Sorting

preliminary sorting 

merging

$b_r$ pages, $M$ memories, $b_b$ Buffer size: read/write b~b~ blocks at a time, 

$log_{M-1}(b_r/M)$ : 归并次数, $2\lceil b_r/b_b\rceil$ : 每次归并的寻道次数

$Total\ I/O\ cost=2b_r+2b_r*\lceil log_{M-1}(b_r/M)\rceil$ 



### Join Operation 

$n_r,n_s : 记录数, b_r,b_s : block 数$ 

* Nested-loop join : $ t_T*(n_r*b_s+b_r)+t_s*(n_r+b_r)$ 
* Block nested-loop join : 内存分给外 留一内。 $I/O\ cost:b_r+b_s*\lceil b_r/(M-1)\rceil$  
* Indexed nested-loop join : $b_r(t_T+t_S)+n_r*c$ , $c$ : 遍历索引并取出所有元组的代价
* Merge-join : 先排序 $t_T*(b_r+b_s)+t_S*(\lceil b_s/b_b\rceil+\lceil   b_r/b_b\rceil)$
* Hash-join : 分而治之(能连接的一定能散列到相同的桶)  散列到能放入内存 BNL

### Other Operation

### Evaluation of Expressions

Materialization : 创建临时表给出结果     cost有中间写操作代价

Pipeline : 上传给父操作







## Ch13 Query Optimization

algebra 

physical

Generating Equivalent Expressions

​	Equivalence Rules

$V(A, r)$: number of distinct values that appear in $r$ for attribute $A$; same as the size of $\prod A(r)$.

selection size estimation

 



## Ch14: Transaction

### concept

​	a *unit* of program execution that accesses and possibly updates various data items.



system failure

concurrent

ACID

* Atomicity requirement : 原子性，要么都执行，要么都不执行
* Consistency requirement : 一致性，一致的数据库，可能有短暂的不一致，但当事务结束时一致
* Isolation requirement : 独立性，串行化处理，让事务并发处理，共同执行，互不影响
* Durability requirement : 持久性，对数据库造成持久性的影响



Transaction State

* active
* partially committed 部分提交，成功执行（不一定对数据库造成影响->failed
* committed 对数据库造成持久性影响
* failed
* aborted 终止状态
  * kill 回滚到还没发生这个事务的状态
  * restart 



concurrent executions

​	increased processor and disk utilization

​	reduced average response time 

Schedule 调度

a sequences of instructions that specify the chronological order in which instructions of concurrent transactions are executed

Serializability 串行

* conflict serializability : 
* view serializability

precedence graph 优先图 : 有环 冲突可串行化

**recoverable** schedules

​	cascading rollbacks

​	cascadeless schedules







## Ch15: Concurrency Control

### Lock-Based Protocols![img](file:///C:\Users\Echo-\AppData\Local\Temp\SGPicFaceTpBq\20372\03BD97BC.png)            你配![img](file:///C:\Users\Echo-\AppData\Local\Temp\SGPicFaceTpBq\20372\03BDD300.png) 🐎

exclusive

shared

**Two-Phase Locking Protocol** 可能死锁、级联回滚，能保证可串行化

* **strict** : its exclusive locks

* **rigorous** : all locks

Lock Conversion : phase 1 : 可获得![img](file:///C:\Users\Echo-\AppData\Local\Temp\SGPicFaceTpBq\20372\03BA590C.png) shared 可升级 exclusive; phase 2 : 可释放![img](file:///C:\Users\Echo-\AppData\Local\Temp\SGPicFaceTpBq\20372\03BA8AF9.png)  exclusive 可降为shared



Lock manager(lock table)



deadlock handling

* prevention
  * wait-die non-preemptive
  * wound-die preemptive
  * timeout-based schemes
* Detection
  * use  wait-for diagram



Timestamp-Based Protocols   赋值最大的时间戳

​	W-

​	R-





## Ch16: Recovery System

**Transaction failure**

* logical errors
* system errors

**System crash**

**Disk failure**



### Recovery Algorithm

 before

after

* recovery and Atomicity 写回由数据库缓存管理决定
  * log-based recovery
    * start <t~i~ start>
    * write <T~i~, X, V~1~, V~2~>写之前V~1~，之后V~2~
    * Immediate-modification : 随时可写磁盘
    * transaction commit <T~i~ commit>: 提交日志被稳定输出到稳定存储器
  * shadow-paging

Undo 恢复旧值

​	complete $<t_i\ abort>$

Redo 写为新值

checkpoint 之前commit的已反馈至磁盘



write-ahead logging **WAL**



Database Buffering

​	no-force policy

​	steal policy : 随时 可在active时提交

buffer management

​	real main-memory

​	virtual memory



remote backup systems