##　B树
### B树的特性
显示中的数据往往是大量的，一般主存装不下，这就意味着必须把数据结构存放在磁盘上。而磁盘是机械运动，它的速度主要依赖磁盘转动和移动磁头的时间。一次磁盘访问大约花费40万条指令的执行时间。所以磁盘访问的代价是很高的，为了节约磁盘访问我们更愿意进行大量的运算。二叉查找树磁盘访问次数与二叉树的高度相关，一般是在O（logN）次左右，如果能够增加树的分支数就可以降低树的高度，从而减少了磁盘访问的次数。所以B树就是是一棵M阶的树，保证只有少数的磁盘访问。

B树（一般就是指B- 树）有以下特性：
 
 1. 每个结点最多有m个分支；根节点不是叶子结点则至少有2个分支，而除根和叶子结点的其他节点至少有 m/2 向上取整个分支。
 2. 有n个分支的节点有n-1个关键字，它们互不相等且按递增顺序排列。
 3. 各个底层节点都是叶子结点，它们处于同一层。叶子结点是失败节点，是查询失败到达的位置。
 4. 节点中的指针Pi为指向子树根的节点，且指针P(i-1)指向子树种所有结点的关键字均小于Ki，但都大于K(i-1)。

B树采用了多路查找方式。 因为节点内部的关键字是有序地，在结点进行查找的时候除了顺序查找之外，还可以用折半查找提高查询效率。

### B树的插入
B树的插入总是发生在叶子结点上，在插入过程中有可能破坏B树的特性，比如新关键字插入使得结点中关键字的个数超出规定个数，此时进行结点的拆分。

### B树的删除

一般是删除关键字，在结点中删除关键字的过程可能破坏B树的特性，比如关键字个数少于规定个数（[m/2] -1），此时如果兄弟节点的关键字大于节点最少关键字数是，向兄弟节点借关键字。否则采用结点合并的方式。
