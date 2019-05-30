# ppyython
python学习提炼（基于《python学习手册》第四版）
==========
*************************************(学习第一天)
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
  
  
*************************************(学习第二天)
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
  ---
  
  然后就是解释为什么比如这一段
  
  squares = []
  
  for x in [1,2,3,4,5]:
      squares.append(x ** 2)
      
  squaress
  
  能简化成 squares = [x ** 2 for x in [1,2,3,4,5]] 这种写法了，除了这是python中常用的写法这种废话外，更主要的原因是，诸如for循环之类的东西都是真正通用的迭代工具，遵守python中的迭代协议，什么叫迭代协议，他说以后会详细讲（我靠。。。）。
  
  所以我个人暂时简单理解为，列表、字典等等这些基础核心的数据类型，包括字符串，都符合它所谓的迭代协议，所以在使用for循环这种迭代工具的时候，只要你遵照它的逻辑和格式，那么系统会自动为你写的代码进行迭代操作，你比如 str = [x * 2 for x in 'abc'] 就会分别把abc字符串进行拆分，分别进行* 2操作。
  
  
  Python的一条重要原则：代码的简单和可读性优先于性能
  ---
  
  （吐槽：这本书现在经常看到的一句话就是，你将在稍后的章节中详细了解xx的详细内容。。。!!(╯' - ')╯︵ ┻━┻ ）
  
  字典部分拾遗----在字典中添加不存在的键时，还是要求同时存在映射值的，如果单纯想从已存在的字典中获取没有映射值的键，依然不可以（这么骚的操作学不来）
  
  
  元组
  --
  
  元组区别于列表，表达式为（），而不是中括号，它形似列表，但是性质却和字符串相似，一旦创建之后，不可以改变其中的元素。然而字符串可以append拼接，这位不可以拼接。它不如列表常用，但在某些场景下正是它的这种不可变性会比列表方便。（你要问哪些场景，他说本书稍后部分细说）
  
  
  剩余部分还有一些文件、其他核心数据类型，感觉介绍都介绍了，他总来一句稍后再说，就很气，个人这部分感觉可以暂时跳过，看多了反而更乱
  ---
  
  基础概览部分结束
  ---
  
  
  正式进入到详解部分
  ===
  
  数字部分详解
  ---
  
  依然没啥好说的，数字操作还是以来操作符表达式，基础的加减乘除以及数值精度、分数小数等迅速略过，这部分即使实在不会，百度也很清楚，旁枝末节不需要。
  
  
  
  
  *********************(不知道能不能坚持一个星期的 学习第三天)
  ---
  
  
  数字部分书中额外引出了集合set这个概念，还是要记录一下。set相比于列表和字典，它是无序也无映射的，它本身叫集合，有一些数学上的特性，比如可以对两个集合进行数学计算中交集，并集的这种操作，操作符就是&，|之类的来表示交并。set同样支持迭代for循环这些操作（打印出的结果也是无序的），不过想要直接索引或者slice这种操作也是不行的，因为它本身是无序的。
  在python3.0中，set的表达方式有了优化，可以直接像字典一样用｛｝，只是没有了键值映射而已。总结就是：
  
  列表[1,2,3,4,5],打印出来还是这样，有序能改
  
  字典{'a':1,'b':2,'c':3,'d':4,'e':5}，打印要通过键来映射值，没有顺序
  
  元组(1,2,3,4,5)，打印出来是有序的，但只读不能改
  
  集合{1,2,3,4,5}，数学意义上的元素集合，经常应用于去重之类的操作，无序，唯一，不能改
  
  集合有一个骚操作就是，比如我有一个列表list1 = [1,1,2,3,4,4,5,5],我想进行去重操作可以直接set(list1),结果变为{1,2,3,4,5},其实可以直接
  list(set(list1))这样就直接去重后返回一个新的list列表了。
  
  
  动态类型介绍***
  ---
  
  这章开头就来了干货，详细阐释了为什么python中a = 3这种操作可以直接被系统判断为数字类型，而不用像java中需要int a = 3 来声明变量类型。
  
  就像把大象装进冰箱需要三步这种'常识'来说，这一过程也分为三步：
  
  1，变量创建，当代码第一次给变量a赋值时才创建（我理解为我们代码中单纯写了a = 3，这时候解释器内心毫无波动），这一过程发生在python代码运行之前的检测；
  
  2，变量类型，在检测并给a赋值之前，a可以被赋予任何类型，字符串，数字，亦或是其它，只有当它在某时某刻引用了某个确定的对象时，它才确定了类型；
  
  3，变量使用，当变量a出现在表达式中需要参与计算的时候，它会立刻被它引用的那个对象所代替（我理解为这时候算引用并被赋值），那么变量a就算被赋值。
  
  更简便一点地说就是：1，创建一个对象是3； 2，创建一个变量名为a； 3，将变量a指向到3，原话为将a与对象3连接。 这里边的a和3分别占用一块内存。
  理论上讲，如果我们这样写a = 3,b = 3，这两个对象3分属不同内存，但python内部作了优化，缓存了不变的对象对其复用（这个例子并不严谨，对于小数字可以缓存，但对于一些复杂的对象，一般就不会复用，相当于两个对象）。
  
  原话：从技术上讲，对象有更复杂的结构而不仅仅是有足够的空间表示它的值那么简单。每一个对象都有两个标准的头部信息：一个类型标识符去标识这个对象的类型，以及一个引用的计数器，用来决定是不是可以回收这个对象。
  ---
  
  这里书中用了一个非典型的python代码来阐述一个事实：类型属于对象，而不是变量（我自己脑补叙述这句话为类型是由对象决定的，跟变量没有半毛钱关系）
  
  a = 123
  
  a = 'python'
  
  a = '456'
  
  a开始是数字，现在又被变为字符串，然后又被赋值为456，这在python中的逻辑是没有问题的可以执行。这就更加能理解了，变量是引用对象的，指针指向何种类型的对象，那么变量就被赋值为何种类型的值。（跟了谁，就会变为它的形状了，我已经默默把车门焊死了，谁都别想下车）
  
  所以在我看来，上边三行代码，更严谨点来说，不应该说a被赋值为123，被赋值为'python',更应该说变量a指向了整数类型的对象123，a指向了字符串对象'python'。这样为什么python中不用声明变量类型这种问题就全都释然了。
  
  那么int，str这些操作真的完全没有了吗，这就是上边加黑大字说的，每一个对象都有两个标准头部信息，其中一个就记录对象的类型，到底是int还是str，已经都记录好了，所以我们自己写代码就不需要声明了，python的灵活性在这里体现。
  
  依然如上边三行代码，在123和python都被放弃引用后，如果它们没有被其它变量引用，python内部会自动把它们回收来达到释放内存的效果，这得益于头部信息的第二个--计数器，当计数器为零时，内部会认为当前对象已无用，自动将其释放到自由空间中去。（我自动脑部以下对话）
  
  123：可恶！已经到极限了吗，计数器归零，这就是我全部的实力了吗？岂可修，不甘心！
  
  'python'：呵呵，杂修要有认清现实的觉悟，你已经被取代了！
  
  （系统声：当前计数器已归零）
  
  'python':纳尼？！
   
  456：都是弟弟。。。
  
  咳咳，继续。。。
  --
  
  共享引用
  
  如果我 a = 3,b = a 这样写，a是指向对象3的，那么当把a赋值给b时，通过上边的python逻辑，在外边看，是a被赋予了3，而b被赋予了a，实际上，两个变量最终都指向3，相当于a告诉b，哥们，我是指向它的，你要想变的和我一样帅，你也应该指向它。
   
  然后，a想变的更帅了，它要 a = 4, 如果我们明白了指向关系，那么很容易知道，这时的b并没有随着a变为4，依然是3。
  
  原话：给一个变量赋一个新的值，并不是替换了原始的对象，而是让这个变量去引用完全不同的一个对象。
  --
  
  然而凡事都不是那么绝对的，我们总会想办法折磨自己。
  
  试想如果我们引用的是一个对象集合呢？ list1 = [1,2,3], list2 = list1 ,这样操作后，list2毫无问题的也会指向列表对象[1,2,3],但如果我这时候后继续写代码list1[1] = 666 ,然后接着打印list2,结果和我们想象的不一样，list2跟着改变了，[1,666,3]，其实这个也很好理解，list1和list2同样指向的是三个整数对象的列表合集这个大的对象，我们通过列表可以更改的特性改变了索引中的某个值，但对于整个列表这个对象来说并没有改变，依然被两个变量所引用，所以我们在以后写代码的时候要注意改变一个变量时，所带来的其他变量的改变。
  
  当然要解决引用的问题，就是复制（copy），或者无参数的切片（slice[::]）,略过不表。
  
  到此，动态类型结束，这是python中的重要概念，可以说大部分运作都是基于这个来的，多看多理解。
  
  
  *********************(放开我 我还能继续学 学习第四天)
  ---
  
  字符串详细
  ---
  
  字符串的一些基本操作略过
  
  这里书中对for循环的遍历简单来做了一个解释，结合之前python变量和对象的知识点，很容易理解python中的for循环了。比如str = 'xyz'  for a in str: print a 相当于指定了a这个变量去一步一步去指向这个字符串（或者说序列）中的每个字符（元素），每指向一次，执行打印。也就是说用a变量每次都重新赋予新的对象，这样理解起来就很容易了。
  
  这一部分作者也在反复强调充分了解python的变量和对象的这种指向关系，这会一直影响到之后的学习。
  
  字符串的切片这里也详细介绍了切片的工作原理，当我们[x:y:z]来切割字符串的时候，在切割之前，系统会自动判断你所切割的这一部分，并将他生成新的对象，这也就解释了为什么之前想要真正复制原来的对象可以借助切片了，因为当你用默认写法[:]来这样切割原字符串时，系统会创建出一个新的对象，和原字符串一模一样。
  
  作者也吐槽为什么从左边索引是0，而从右侧来计算偏移就是从-1开始，因为没有-0这种说法嘛233。
  
  之后就是字符串的一些常见方法，方法本身都是为了实现各种目的而进行的操作，理解不理解先了解就可以，不过他也在反复强调，大部分或者说就默认情况下，操作字符串后都是生成了新的对象，即使像replace这种叫做替换操作的方法也并不是真正的替换。但是若当我们突然要操作大量连续的字符时，重新生成一个新的对象对于代码的性能也是会有影响的，这里有个技巧就是，先将字符串‘打散’为一个个字符，然后用list列表来接收它们，因为列表是可以进行索引位置的任意修改的，这样就是某种意义上的在原有对象上进行修改了，改完之后可以join方法将列表中的字符重新合并。但明眼人一看就有疑问，这用列表接收，也是生成新的列表对象了啊，我个人理解列表这种结构因为其本身支持扩展和修改的特性，是要比生成新的字符串对象来进行相关操作要快的，极端点的情况，假设你要对很长的一段字符串进行切片操作，需要将该字符串中的一些关键信息提取后进行重组，那么这种单独的合并就不如在列表中完成提取后一次性用join重组来的快。
  
  格式化------这一部分详细介绍了格式化这个常用的操作方法，格式化在python中可以简单粗暴地已一行代码输出一串代码，不用像其他一些语言分开操作。
  
  %d，%s具体例子略过。
  
  原话：请记住，格式化总会返回新的字符串作为结果而不是对原有的字符串进行修改，如果需要的话，可以分配（新建）一个变量名来保存。
  ---
  
  然后就是很爽的{}.format的这种格式化，更加直观也好用，比如这样写print('{0}+{1}={2}'.format(1,2,3))执行完后就是1+2=3，可读性很强。
  
  格式化部分还是有好多高级操作的，但是点到为止，看多了会没有获得感。
  
  >>> import sys
  
  >>> 'My {1[spam]} runs {0.platform}'.format(sys,{'spam':'laptop'}) 
  
  >>> 'My laptop runs win32'
  
  就比如这种，导入sys模块，format括号中的索引0和1分别是sys和一个字典，前边的两个{}格式可以直接用索引0和1来获取各自的值和方法(platform是sys的一个获取属性的方法，我的电脑是32位的，所以打印出结果就是win32)
  
  
  
  *********************(肯定不是第五天的 学习第五天)
  ---
  
  更多更复杂的格式化高级操作我主动略过了，只是简单看了一下，有的能理解有的需要花时间来看，感觉还是跳过一些为好，细节上抠的太多，总是会丧失学习的兴趣，或者说会有挫败感，也不知道这么做对不对，但能保持兴趣来学习还是最重要的。
  
  对于%和{}.format的两种格式化，作者在写这一版的时候，刚刚发布python3.1的测试版，从作者的叙述上来看，作者更倾向于建议多使用新的格式化方法即{}.format，他有理由相信未来这种方法可能会替代%号的格式化方法，因为这种表达方式更加利于学习，新人易懂。不过通过我看各种论坛或者学习网站关于python3以上的学习教程，%这种还是百分之百出现在学习中的，所以应该是没有发生%被完全废弃，被新的方法替代的情况。不过我也很喜欢{}这种格式化方法，因为对于我这种菜鸟来说真的很棒。
  
  通常意义下的类型分类
  ---
  
  三种：数字（整数，浮点等）、序列（字符串、列表、元组等）、映射（字典）（集合暂时自成一体）
  
  在python中，除了数字是可以计算没问题之外，字符串，列表，元组都是可以像比如用+来进行加法（合并）运算的，操作的对象生成的结果也是自动判断的，两个列表合并那肯定是列表，两个元组合并自然也是元组，对象类型将会告诉python去执行什么样的任务。
  
  字符串告一段落
  ---
  
  列表和字典
  ---
  
  列表常见操作中最绕不开的就是for循环，所谓的迭代，在python中，常常一句代码就可以完成其他语言五六行的操作，可谓高效。
  
  常见写法list1 = [x+2 for x in [1,2,3,4]] 输出结果为[3,4,5,6]。通常情况下我们会先创建一个空列表，然后用for将原列表进行迭代计算，再用空列表去拼接原来计算后的列表，而现在python直接一步到位都做到了，效率很高。
  
  还有常见的map操作，list(map(abs,[-1,-2,0,-3,5]))。
  
  依然需要强调，当改变列表中的某个元素时，其他引用该列表对象的变量会同时改变。
  
  字典。。。
  
  
  *********************(居然可以坚持到第六次学习的 学习第六天)
  ---
    
  除列表外，字典是python中另外一种灵活的内置数据结构类型，最大的特点是通过键来存取值。
  
  字典的一些常规方法略过，着重提一下解析，依然是一句代码就可以创建一个字典对象比如这样：dic = {x : x + 1 for x in range(5)}
  
  学习过程中有一个值得注意的小插曲是使用.keys()这个方法获取键的时候，在python早些版本的时候，用这个方法获取的对象直接就是列表，而在3.x以后，这个方法获取的是叫做dict_keys这么个类型，为什么能注意到这个点，因为在尝试书中这部分举例的时候，我是提前用powershell敲过的，得出来的确实也是报错，之后书中也提到了这一点，在3.0之后，用.keys()得到的是一个可迭代的对象，并不是真正的列表，想要获得列表，可以用list()，将这个迭代对象变为列表，即list(dict.keys())，这样就得到键的列表了。不过我在自己本机操作的时候，用了list()这个方法后依然报错，后来不用win10中自带的powershell，用pycharm又运行了一遍，这次就没问题了，我百度了半天我出现的这种问题，换过了各种描述方式，没有找到信服的回答，所以暂定为我自己电脑的问题（编译工具的锅）。
  
  （上边这种情况有点钻牛角尖了，当一种编译工具出问题应该果断换另一个试试）
  
  对于字典，不要字面上去想象它的形象是键值一一对应，映射的这种，把它想象成是一种乱序的列表更好，列表有序，用索引位置来取值，字典无序，键就是另一种索引，用它来取值。（不过还是看个人理解，字典中可以用不存在的键添加新的键值关系，而列表却不能用不存在的索引来创建新的元素，强迫症警告）
  
  还有个有意思方法是get(),当获取没有的键是，返回的None，避免了代码错误，很贴心。
  
  关于书中python3.0中字典部分的用法例子略过，不过这些用法在创建字典时确实简洁高效，放几个创建字典的例子：
  
  D = {k:v for (k,v) in zip(['a','b','c'],[1,2,3])}
  
  D = {x : x + 2 for x in [1,2,3,4]}
  
  D = dict.fromkeys(['a','b','c'],0)
  
  D = {k:0 for k in ['a','b','c']}
  
  原话：在python3.0中，字典的keys，values，items都返回视图对象，而在python2.6中，它们返回实际结果列表。视图对象是可迭代的，这就意味着对象每次产生一个结果项，而不是在内存中立即产生结果列表。除了是可迭代的，字典视图还保持了字典成份最初的顺序，反映字典未来的修改，并且能够支持集合操作。另一方面，它们不是列表，并且不支持像索引和列表sort方法这样的操作，打印的时候它们也不显示自己的项。
  ---
  
  
  元组、文件及其它
  ---
  
  
  *********************(真的坚持到了一个星期的 学习第七天)
  ---
  
  元组在看详细介绍之前我感觉应该没啥太多的内容，它和列表好多东西可以说是重合的，除了自己不能改变其中的元素，它本身还是支持合并，切片这些操作的。
  
  为什么有了列表还要元组，作者马上也在书中给出了回答，也就是元组的这种不可变的特性，这种特性可以确保元组对象在被各种不同的变量引用时不被修改，从而保证了其完整性，我们在学习过列表后很清楚知道这是怎么回事了。
  
  文件这种类型提供了可以存取python内部文件的一种方法。
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
