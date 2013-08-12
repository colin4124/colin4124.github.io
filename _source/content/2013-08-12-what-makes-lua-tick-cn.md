# 选择Lua语言的九个理由

- date: 2013-08-12 02:14:51
- begin: 2013-08-12 00:51:16
- tags: 翻译

-------------------------

[原文地址：What makes Lua tick](http://lua-users.org/lists/lua-l/2012-04/msg00331.html)

lua:

1. 源码和库都要比许多流行的语言（Python 等等）小至少一个数量级。因为Lua 的源码非常小，简单，如果你想避免增加外部依赖，在你的代码树里只包含整个Lua 实现(implementation)是完全合理的。

2. 非常快。Lua 解释器比大多数脚本语言快得多（同样，快一个数量级并不奇怪），对于一些特定的CPU 架构(x86, ppc)，LuaJIT2 是个非常好的JIT 编译器。使用LuaJIT 经常还能够再加快一个数量级，许多时候，其速度接近C。对于标准Lua，LuaJIT 也是一个“直接”(drop-in)的替代品。

3. 拥有 LPEG。LPEG 是Lua “Parsing Expression Grammar”(解析表达式语法)，无论大或小的任务，它简单，强大和快速的解析的能力都能胜任；它是yacc/lex/hairy-regexps 一个很好的替代品。[我用LPEG 和LuaJIT 写了一个语法分析器(parser)，比我用yacc/lex 快多了，并且容易简单的就做出来了。] LEPG 是Lua 的一个扩展包，但是你值得拥有（它是一个源文件）。

4. 很棒的C 接口，不管是C 调用Lua，还是Lua 调用C ，都会令你非常愉快的。为了链接(interfacing)又大又复杂的C++ 库，可以使用[SWIG](http://www.swig.org/translations/chinese/)(Simplified Wrapper and Interface Generator)，或者是任何众多接口生成器中的一个。（当然也可以用C++ 写简单的C 语言实现的Lua 接口）。

5. 授权自由（类似BSD ），如何你愿意，你可以在私有项目中使用。对FOSS 项目来说是GPL 兼容的。

6. 非常，非常地优雅。它不是lisp，没有基于cons-cells（序对），但明星受到了scheme 的影响，语法简单
(straight-forward) 美观(attractive)。像scheme（至少是早期版本），它趋于“最简化”，但是在与可用性之间取得很好的平衡。对于一些有lisp 背景的人（像我），尽管有些差异，Lua 里大多数东西感到很熟悉，“明智”。

7. 语法简单，美观(attractive)和平易近人。这对于已经是lisp 的用户，这可能不是优势，但如果你想要为普通用户(end-users)写脚本，这就很重要(relevant)。

8. 历史悠久，有专业负责的开发者，在Lua 过去的20年的发展中，展现了他们优秀的判断力。

9. 朝气蓬勃和友好的社区。
