# [译] 把一个库开源，你该做些什么

- date: 2013-08-06
- begin: 2013-07-06 16:49
- tags: 翻译, 开源

----------------------

原文地址: [On Open Sourcing Libraries](http://williamdurand.fr/2013/07/04/on-open-sourcing-libraries/)

[简要概括：TL;DR](#tl-dr) ([Too long; didn't read](http://en.wikipedia.org/wiki/Wikipedia:Too_long;_didn't_read))

把一个库<a class="footnote-reference" href="#note-1">[1]</a>开源非常简单，仅需几秒钟。你所需要做的仅仅是把公共仓库(public repository) 托管 (hosted) 在网上([GitHub](https://github.com/), [Bitbucket](https://bitbucket.org/),等等)吗？不是的！事实上，如果你 **想把你非常酷的库公开，并加以悉心照料**的话<a class="footnote-reference" href="#note-2">[2]</a>，这对每个人都是件好事。来看看我们该怎么做。

##README的编写

<code>README</code>文件在你的项目中 **占据首要地位**。你的项目必须包含它！这个文件必须包含库的 **名字**和一个关于它(简短的) **描述**。把 **描述**这一章节当作是 **电梯游说** (elevator pitch，在乘电梯的30秒内清晰准确地向客户解释清楚解决方案)。

然后是编写 **使用**章节。尽可能详细地用文字、代码片段、截图或者GIF格式的图片，来描述如何使用你的库。这个就是你项目的 **文档**, 你的库很多时候也同样如此, 这将会是你唯一提供的文档。 

先写 **使用**指南这部分并不是一个随意的选择。<code>README</code>文件应该能吸引读者(blow your reader's mind)，这样他们就会使用你的库并为它做出贡献(或许不会)。

第三小节必须写 **安装**方法。这个小节以*用户*的角度说明怎样快速安装你的库。如果有多种安装方式，首先介绍你认为最好的方式，然后才是(介绍)其他的。

你可以添加一个 **依赖**章节，例如， *依赖X的Y版本（Depends on X version Y）* 。这个章节是可选的，可以不写。

第四个必须编写的小节是 **贡献**。尽管它可以使用一个<code>CONTRIBUTING</code> 文件代替。说明 **怎样折腾你的库(how to hack your library)**，怎样报告bugs，或者怎样提交特性请求(submit feature requests)。这方面介绍一定要详细。 **说明规则**，让收到的请求合并中避免评论每一行<a class="footnote-reference" href="#note-3">[3]</a>，指引贡献者使用恰当的工具(Point contributors to the right tools )，比如linters 或者 compilers。

你还必须添加一个 **测试**章节。说明 **怎样安装测试套件**，怎样运行功能测试(functional tests)，以及需要安装的工具。

如果你使用第三方的东西，或者打算列出贡献者(当然这个也可以写在 **作者**章节)，那就添加一个 **信用(Credits)**章节。这个章节是可选的，可以不写。

最后还要记住，添加一个 **许可证**章节!

模板如下([Markdown](http://wowubuntu.com/markdown/) 语法)：
	
	project-x     <-------- 一级标题 (项目名字)
	=========
    
    project-x is a better way to achieve this and that, by leveraging the new API,
	blablabla.
	project-x用更好的方式实现某某功能，通过使用高效的新API，此处省略N个字。
	
	## Usage(使用)     <-------- 二级标题
	...

	## Installation(安装)
	...

	## Requirements(依赖)
	...

	## Contributing(贡献)

    See CONTRIBUTING file.
	查看 CONTRIBUTING 文件。

	## Running the Tests(执行测试)
	...

	## Credits(信用)
	...

	## License(许可证)
		
	project-x is released under the MIT License. See the bundled LICENSE file for 
	details.
    project-x 依据 MIT许可证发布。详细请看捆绑的 LICENSE 文件。

正如你所看到的, 我在模板里介绍了两个文件: <code>LICENSE</code>(许可证)和<code>CONTRIBUTING</code>(贡献指南)。 **贡献**这一小节的内容用一个文件<code>CONTRIBUTING</code>代替了。<code>LICENSE</code>(许可证)这个文件里包含了你项目选择的许可证，但你应该选用哪个许可证呢？

##许可证

我不想把所有的许可证都一一对比，你可以访问[tl;drLegal](http://www.tldrlegal.com/)这个网站，它用易懂的话(simple words)向你介绍实用的(useful)开源许可证相关信息。

我倾向于使用 [MIT许可证](http://www.tldrlegal.com/license/mit-license)，因为它非常自由(liberal)。我这里的建议是 **参考下你的社区**，选择最恰当的一个。比如说，在Symfony2 (一个PHP框架)社区，大多数相关的项目或者bundles 都是以MIT许可证发布的。而Java 的项目经常以Apache许可证2.0(Apache License 2.0)发布的。

根据最近的报道(reports)，[大多数 GitHub上的项目没有一个开源许可证](http://www.theregister.co.uk/2013/04/18/github_licensing_study/)。这是不好的(bad)！你必须得有许可证，即使是[啤酒软件许可证](http://zh.wikipedia.org/wiki/%E5%95%A4%E9%85%92%E8%BB%9F%E9%AB%94)([Beerware license](http://en.wikipedia.org/wiki/Beerware))。

正如[Hacker News](https://news.ycombinator.com/item?id=5990836)所提到的，[精心(carefully)选择你的许可证](https://news.ycombinator.com/item?id=5992270)。并且，[不要用你自己做的许可证或者仅仅声明这个项目属于公共领域 (Public domain，简单来说作品已属于全人类)。公共领域在国际上的确不是准确定义的概念，意味着不同国家会有不同的理解](https://news.ycombinator.com/item?id=5992428)。

即使你现在有一个文档完善的库和一个许可证，还是没有“征服世界”(dominate the world)<a class="footnote-reference" href="#note-4">[4]</a>。下面，我给出一个概览，介绍在开源项目中我认为重要的东西。

##写自动化测试(Write Tests & Automate)

我们可以通过开源项目写优美的代码，因为这里没有截止期限，也没有“客户”。记住，你项目展示了你能够做什么。作为一个开发者， **你的库就是你的名片**。

**写大量的测试**！如果没有提供一个测试套件，怎么去期望别人能为你的库做出贡献呢？因此, 写测试, 和使用 [Travis CI](http://zh.wikipedia.org/zh-cn/Travis_CI)。 添加一个 <code>.travis.yml</code> 文件，描述怎么样运行你的测试。这也是另一种方式写如何运行测试的文档。

在你的<code>README</code>文件里也添加一个[状态图片](http://about.travis-ci.org/docs/user/status-images/)(status image)。

留意一下(Take a look at)在线工具，例如PHP和JavaScript使用[Scrutinizer](https://scrutinizer-ci.com/) , 或者 [Puppet Linter](http://www.puppetlinter.com/)。尽量使其自动化。

##标准化(Be Standard)

在你的库中 **使用恰当的工具(right tools)**是非常重要的。再看一下你的社区，然后选择大家常用(tend to use)的工具。在用PHP写的程序里，大家都用 [Composer](http://getcomposer.org/) 作为管理依赖关系的工具(dependency manager)。不要浪费时间去用PEAR或者其他工具，就用Composer。如果是一个Node.js库，在[npm](https://npmjs.org/)上注册它。Ruby 的开发者，请把你的库作为[gem](http://guides.rubygems.org/make-your-own-gem/)发布(distribute your library as a gem)。C#的开发者，请使用[NuGet](http://nuget.org/)。

另一个例子，在Symfony2里，在<code>Resources/doc</code> 里添加文档是一个好的做法(good practice)。这是个惯例。 **不要重复出现你的文档**，而是在你的<code>README</code>文件里添加一个快速跳到文档的链接。

##管理问题(Issues)和版本发布(Releases)

[GitHub](https://github.com/)，[CodePlex](http://www.codeplex.com/)，或者其他你喜欢的，他们都提供了追踪问题(issue tracker)的工具，请使用它！

如果你使用GitHub，不要浪费时间在Wiki上。我从来没有发现一个适当的工作流程(decent workflow)。用<code>README</code>文件作为你的文档，或者万一(in case)文档量很大(extensive documentation)的时候使用[Read The Docs](https://readthedocs.org/)来做托管。使用 GitHub Issues 来管理里程碑，并用标签对问题进行分类。

还有，尝试尽快回复所有的问题...但[be careful, and manage your time](http://williamdurand.fr/2013/02/20/burnout/)。对人友好，花时间帮助新来的人。非常值得去学习[如何维护一个成功的开源项目](https://medium.com/p/aaa2a5437d3a)。

另一个建议是，定期地打上版本标签来进行发布(to release often by tagging versions periodically)。谈起版本, 请关注(follow) [Semantic Versioning Specification](http://semver.org/)。

然后，用<code>CHANGELOG</code>(更改日志)这个文件来帮助用户识别出你做出的更改。如果你不向后兼容，写一个<code>UPGRADE</code>(升级)文件介绍说明如何升级。

## 你需要反馈！

我[开源大量项目](https://github.com/willdurand?tab=repositories)最主要的原因是，可以从用户的反馈中学到很多东西。所以你需要反馈，我需要反馈，每个人都需要反馈！在Twitter，Hacker News等等上分享你的项目。让全世界都知道！人们必须知道你的项目并不是因为它很出色，令人难忘，而是因为人们可以评论它。

使用 GitHub pages 为你的项目创建主页，如果你愿意还可以买个域名，

还记得"征服世界"的计划吗？你要实现这个目标几乎需要到的，我们永远不知道。

## 雇人(Hire People)

一旦你"征服世界"，招收别人(enroll new people)<a class="footnote-reference" href="#note-5">[5]</a>来帮助你非常重要这是非常棒的体验。这样会给你更多的时间来搞其他开源项目(也可以说是征服另一个世界的计划) :-)  	

## 总而言之

让一个库开源不仅仅是发布源代码。你还需要再做一些事情来让别人更容易更愉快地使用它。为项目写文档展示了你的教学能力，这样就可以找到恰当的词来表达你的想法。当然，还说明了你在用心地做这件事。

不要忘记在你的库里面添加测试，如果你在工作中不方便，回家再做。还有别忘了许可证，别找借口！

开源项目真的非常酷，但是要避免[非我发明症](http://zh.wikipedia.org/wiki/%E9%9D%9E%E6%88%91%E6%89%80%E5%89%B5)(Not Invented Here (NIH) Syndrome)。尽可能地做贡献，而不是再开创一个已有的开源项目，重复造轮子。 

## <a name="tl-dr"></a>TL;DR

你的库或者项目：

- 必须有一个<code>README</code>文件，内容包括名字，描述还有以下章节： **使用方法**， **安装指南**， **贡献规范**， **如何测试**和 **许可证**；
- 必须有一个显眼的许可证(MUST have a license that is visible)；
- 必须能测试(MUST be tested);
- 必须标准化或者符合你社区的惯例；

你：

- 需要反馈；
- 必须待人友善；
- 应该招人(enroll people)。

顺便说一下：如果你发现排版错误和错别字。请[派生(fork)和修改它](https://github.com/colin4124/colin4124.github.com/edit/master/_source/content/2013-08-06-on-open-sourcing-libraries-cn.md)。非常感谢！
本文以[Creative Commons Attribution-ShareAlike 3.0 Unported License](http://creativecommons.org/licenses/by-sa/3.0/)许可证发表。

####译注：

1. <a name="note-1"></a>I use "project" as a synonym of "library",My blog post focuses on libraries as Open Source projects, rather than "projects" like products (applications). 原作者的开源项目主要是库，所以这篇文章对其他类型的开源项目同样适用。

2. <a name="note-2"></a>原文：add some love to your new shiny library you just made publicly available. 
    - love = take care of 
    - shiny = well, shiny is... shiny, something which is cool, and beautiful

3. <a name="note-3"></a> 原文： **Explain the rules** to avoid commenting every single line in Pull Requests you receive.

4. it's a joke, 这是个玩笑。

5. <a name="note-4"></a> 作者原话：enroll = hire (more or less), but it's not because of the previous sentence. You don't hire people "for real" (like a company would do I mean) 因此我把 enroll 译作 招收

