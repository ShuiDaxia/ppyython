# ppyython
python学习提炼（基于《python学习手册》第四版）
==========
学习第一天
----------
  今天开始记录以兴趣使然地想学习python然后并不知道用来做什么来学习python的笔记。
  坑人的java培训班还是有点用的，至少努力学习过java语法后，看其他语言的基础知识不会完全懵逼。
  
  python基础还是挺容易懂的，只要别说什么专业语句，底层实现啥的，我上来也能轻松打印hello world。
  
  python内置对象，强语言动态，不用int，string，直接自动判断类型，省心，天生内置对象让程序员..哦不..是程序运行更简单，更有效率，所以请优先使用。
  
  学习顺序----->核心数据类型------表达式------完整语句------模块--------程序
  --
  
  常用的核心数据类型 数字、字符串、列表list、字典dict、元组（高达雾）tuple、集合set（java里集合明明叫list，好乱），函数模块类另算。
  
  以上这些核心数据类型都是在python中高效创建的，有特定的语法来生成，在python中可以说啥都是对象，就不用在现实里找了，人生苦短，我选python。
  
  感觉学这些编程语言还是看多少学多少，至于内部具体怎么实现的，以后再说，前期要 粗糙 而 系统 地学。
  
  数字部分略（可把我牛逼坏了）
  ---
  
  字符串
  ---
  
      字符串很有意思，它可以看成若干字符的集合，例如 str = '520meiduixiang', 那么打印s[0],s[2]等等是可以单独取出str中的字符的。
      它的反向索引也很有意思，s[-1],s[-2]这样写就可以从后往前提取了，而且它自带的切片（slice）用来切割提取字符串非常棒，格式是[x:y:z],
      xyz分别为数字，x表示从索引x开始，y表示到y索引的前一位，z表示每隔几个取字符，如果我们写str[2:5:2],那么打印出来就是0e,如果是
      str[:5:]，没写的表示默认，也就是从0索引切割到索引5的前一位，并且没有跳跃，结果打印就是520me。
      
      上边这个我可以玩上一整天。这个切片非常方便，真是居家旅行必备，内置方法，比正则执行有效率。
  
  字符串也可以直接‘+’，表示合并。想把两个字符合并，给他们做加法吧，str+',yemeiqian',打印后就是520meiduixiang，yemeiqian 真的是个悲伤的故事呢。
  
  数字表加，字符表合并，多态。
  
  但需要注意的是，数字，字符串还有以后要接触的元组都是不可变的，虽然上边一顿切片操作，python内部是帮我们建立的新的字符串来生成结果的，我们不可能对本体进行操作，比如这样，str[3] = y ，再这样str[4] = o ，最后再这样 str[5] = u,以上骚操作是不可以的， 你在执行第一步的时候就会报错，你试图想改变什么，但是还是需要认清现实（手动滑稽），至于什么find，replace，split这些操作也不会改变原字符串，这是替身攻击。
  
  这一块包括数字和字符串还有个常用的骚操作，格式化输出，数字一般用%d（十进制），浮点是%f，字符串是%f，这些都不用强记，活学活用，百度我有。
  
  比如我要这样写 print('s%' % 'xianzhuantashigeyi'), 那么打印出来的就是xianzhuantashigeyi。
  
  还有format写法，这个也非常好用，可以直接把输出格式当作模版，print('{0} {1}'.format('hello','world'))，那么直接可以打印出名句了，0和1表示字符串格式的替换顺序。
  
  列表
  ---
  字符串某种意义上可以当成加了限制的列表，而真正的列表是序列的一种，有序且没有固定大小，每个索引可以分别放数字、字符串、甚至列表，就像一个有顺序的仓库，每件物品都被索引标上了编号。
  
  列表也可以像字符串一样支持索引、拼接以及切片的操作，跟其他语言的集合一样。
  
  列表可以进行一些特定操作，append、pop（类似del）、insert、remove、sort、reverse，和字符串不同的是，这些会直接改变原列表的内容。
  
  python中也有类似于java中数组越界异常的错误提示，所以超出列表索引不会自动增加列表的长度，而是会报错。（毫无节制地去要求别人改变，是不会有好结果的）
  
  列表是灵活的，支持多层嵌套，类似于多元数组，而且不限于列表嵌套列表，可以列表嵌套字典，字典里再嵌套列表（666）。
  
  
学习第二天
-----
书接上回

  这书到这引出了列表解析这么个东西，我个人觉得这对于真正0基础人来说有点懵逼，它定义了M = [[1,2,3],[4,5,6],[7,8,9]],这么一个相当于二位数组的列表，实际上它提到了要把它看成3x3这样的矩阵，大概就是这样：
  
  1---2---3
 
  4---5---6
 
  7---8---9
  
  看成正方形矩阵后，它这样写的定义列表变量col = [row[1] for row in M] row 在 M 中进行遍历，实际上是纵向对矩阵进行重新提取形成新的列表，所以row应该是[[1,4,7],[2,5,8],[3,6,9]]这样的结果，所以row[1]就是第二列，结果就是[2,5,8]。
  
  这里跳跃的有点快，书中并没有对他使用for循环遍历做出解释，新人学习的时候没有接触过类似语法的人会云里雾里，还有关于本身这种定义变量后直接写表达式中这种python的常见操作也没有给出合理解释，所以个人认为这部分有些粗糙，列表解析对于以后解析存储网络数据有很大的影响，这部分还是要清晰一些。
  
  
  字典
  ---
  字典和java中的map类似，键值映射，key和value这样，它是python核心基础中唯一的映射类型，长度可大可小，没有固定顺序，依靠键来找值，用{}来表示。
  
  字典创建键值的时候不用考虑索引越界这种东西，你每用一个新的键来创建新的映射值的时候，字典会自动扩展长度，用字典来执行搜索往往是最快的，要不怎么叫字典呢。
  
  这部分作者直接来个数据结构复杂的小例子 rec = {'name':{'first':'Bob','second':'Smith'},'job':['dev','mgr'],'age':40.5}
  
  看似很复杂的数据结构其实拆分来看，想象这是一份简单的工人信息卡，name，job，age不言而喻，键值都是工人信息，当我rec['name']，就提取出了内部的字典，第一工组的bob和第二组的smith，job部分对应的值是具体工种，用列表来存放没有问题，支持扩展，age部分简化了，只有年龄
  
  他举这个例子的目的，让初学者学会用表达式提取结构中的信息不是主要目的，真正的目的是让你了解python中，这些核心数据嵌套是非常灵活的，通过嵌套可以轻松将各种数据糅合在一起，建立复杂的结构，而且这些我们只需要类似rec这样一个表达式就可以很快完成，其中的细节都是python在内部帮我们自动搞定了。而且在你最后一次引用后，它们会自动释放内存，真的又暖又贴心呢（我突然想到如果把语言娘化，python一定是枚软妹了）
  
  原话：从技术上来说，Python具有一种叫做垃圾收集的特性，在程序运行时可以清理不再使用的内存，并将你从必须管理代码中这样的细节中解放出来。在Python中，一旦一个对象被最后一次引用被移除，空间将会立即回收。（妈我渴了，妈我饿了，大概就是这种感觉吧。。。）
  
  
  
  
