# 计算机组成原理课程设计总结

- date: 2015-03-25 15:02
- tags: 课程设计

--------------------------------------------

## 课程设计简介



## 心得体会

计算机组成原理课程设计的动手阶段，咧威几乎用完十天的工作时间<a class="footnote-reference" href="#note-1">[1]</a>才能完成。这次课程设计过程中极大锻炼了我耐心,以及学会如何权衡之后再做出相应的妥协。

咧威在连线这个阶段就摔过很多跟头。第一次的时候，用了两个小时排错，最后才发现是连线的插头错位了。写测试程序的时候，都用单步运行的模式进行调试。这是调程序最耗时的办法，必须沉得住气，静下心去分析每条微代码是怎么运行的。
 
 设计指令集的时候，考虑到咧威的方案最多只能形成16个微操作的入口地址，而咧威的设计有17个指令。咧威采用的办法是在某个入口地址里用分支实现多条指令。这样做的好处是节省控存空间，但坏处是，整合在同一入口地址的指令，会多执行一条进行译码的微指令，使得CPI的值增大。
 
在课程设计过程中，咧威得到了很多同学的帮助，没有他们的指教，咧威会走更多的弯路，也不可能在规定的十天时间之内完成，在此感谢他们。

总而言之，在连续高强度的工作时间里，咧威遇到很多错误，有粗心的连线错误，也有算法本身的错误。为了排除这些错误，咧威选择了最有效，但也最费时的方法，分析每条微指令是怎么执行的，极大考验了咧威的耐性,也发现了自己考虑问题不够全面，做事不够细致的不足之处，今后咧威会多加注意，努力完善自身的不足之处。


####脚注：

1. <a name="note-1"></a>大概连续工作七八天（没具体记录，略遗憾），每天11个小时。本来安装老师要求，是连续工作十天，每天11个小时。最后由于上课和考试，用零碎的时间段补完两三天的工作时间，凑够 110个小时。

2. <a name="note-2"></a>原文：add some love to your new shiny library you just made publicly available. 
    - love = take care of 
    - shiny = well, shiny is... shiny, something which is cool, and beautiful

3. <a name="note-3"></a> 原文： **Explain the rules** to avoid commenting every single line in Pull Requests you receive.

4. it's a joke, 这是个玩笑。

5. <a name="note-4"></a> 作者原话：enroll = hire (more or less), but it's not because of the previous sentence. You don't hire people "for real" (like a company would do I mean) 因此我把 enroll 译作 招收
