## Introduction

#### The phase of a compiler

**Font End**

* Lexical analysis 
* Syntax analysis
* Semantic analysis
* IR generation

**Back End**

* IR optimization 
* Code generation
* Optimization

![image-20200808151835483](C:\Users\Echo-\AppData\Roaming\Typora\typora-user-images\image-20200808151835483.png)



## Lexical

Be familiar with the expression of R.E.. Know the difference of R.E. and C.F.G, can translate each from the other. While given a R.E, know how to draw the NFA and DFA, and how to minimize it. 

#### Regular Expressions

#### NFA

#### DFA

#### Construction of Scanner



## C.F.G

#### Context-Free Grammar

#### Derivation and Reduction

* Derivation : rightmost and leftmost(canonical derivation 规范推导)
  * left-sentential form and right-sentential form (最左/右句型)

#### Parse tree

* 将叶子节点从左至右排列后得到一个句型

#### Abstract syntax tree

#### Ambiguous grammar

* 一个文法可以为某个语句生成多颗语法分析树

* 同一个句子有多个最左推导或多个最右推导

* Eliminating Ambiguity

  * Eliminating left recursion

    * e.g. $A\rightarrow A\alpha\ |\ \beta$

    $A\rightarrow \beta A'$
    
    $A'\rightarrow \alpha A'\ |\ \epsilon$
    
  * Left factoring
  
    $A\rightarrow \alpha \beta_1\ |\ \alpha \beta_2$
  
    $A\rightarrow \alpha A'$
  
    $A'\rightarrow \beta_1\ |\ \beta_2$
  
  

## Top-Down Parsing

#### LL(1)grammar

Production  $A\rightarrow \alpha\ |\ \beta$    satisfies the following 

1.  At most one of $\alpha$ and $\beta$ can derive empty string
2. The FIRST set of $\alpha$ and $\beta$  are disjoint sets
3. SELECT set are disjoint sets

#### LL(1)parsing

#### Construction of Recursive-descent parsing

#### Computing First set and Follow set

* First set : $FIRST(\alpha)$为$\alpha$能推导出来的串的首符号集合
* Follow set : $FOLLOW(A)$为$A$后边的终结符号集合
* Select set 

## Bottom-Up Parsing

#### LR(0)parsing

#### SLR(0)parsing

#### Right sentential form

#### Viable prefix

#### Handle

每次规约的符号串称为“句柄”	



## Semantic

SDD

#### dependency graphs  

#### Algorithms for attribute computation

* Dependency Graphs and Evaluation Order
* Synthesized and Inherited Attributes
* The Computation of Attributes During Parsing

#### Attribute grammar

attributes and attribute equations

**attribute** : is any property if a programming language construct

​	associated with the grammar symbol (terminal or nonterminal)

**attribute equations** : semantic rules 语义检查，比较的规则

<img src="C:\Users\Echo-\AppData\Roaming\Typora\typora-user-images\image-20200813175805086.png" alt="image-20200813175805086" style="zoom: 50%;" />

#### Synthesized and Inherited attributes

 

## Intermediate Code Generation

#### Intermediate code generation for basic structures : Three-address code

#### TAC for control structure

#### TAC for expression



