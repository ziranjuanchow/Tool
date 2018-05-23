
## 公式

强制换行 \\\

**空格**
数字之间的空格会被忽略。   
\quad 代表当前字体下一个汉字的空白距离    
\qquad 代表当前字体下两个汉字的空白距离   
矩阵里面数字之间加上 & 来区分元素。   

**公式书写**

行内数学模式将公式排版在一个段落中，使用方式为`\(...\)` 、`$...$`和`\begin{math} ... \end{math}`.

行间数学模式一般用于较长的数学方程或希望单独显示的公式，使用方式为`\[...]`和`\begin{displaymath}...\end{displaymath}。

如果需要对行间公式进行编号，可以使用 equation 环境

**向量** 单个字符上的小箭头用`\vec`， 由A到B的向量用命令`\overrightarrow` 和`\overleftarrow` 指定。

参考文章：怎样用LaTeX优雅地打印数学的一切

> https://www.jianshu.com/p/f5d475d6904e

**Environment环境**

所有的环境，都是起于 \begin{环境名称}，止于 \end{环境名称}，这两个指令
之间的文稿都会被作用，而且，环境之内还可以套用其他不同的环境。
LaTeX 文稿的内文，其实就是包在一个 \begin{document} 和 \end{document}
这个 document 环境当中

环境举例：

	cases大括号{}
	matrix矩阵
	bmatrix 矩阵带[]显示

LaTex的公示如下：   

	\sum _{x}=x^{2}+y^{3}_{i}  

但是MarkdownPad2 里的 MathJax包 支持的公式如下：

	$$ \sum \_{x}=x^{2}+y^{3}\_{i} $$
前后需要加 $$  
_前面要加\  [MarkdownPad2 需要，Typora 不需要]
\前面也要加转义符\  

####公式右边手动编号

x^n+y^n=z^n  \eqno{(1)} $$

####公式后面自动编号：

\begin{equation}
x^n+y^n=z^n
\end{equation}

> http://blog.sina.com.cn/s/blog_4419b53f0101baiw.html

#### 上下可输入文字的箭头

宏包amsmath 提供了两个可以伸长的单箭头符号

\xleftarrow[下方公式]{上方公式}  和

\xrightarrow[下方公式]{上方公式}

只支持公式 和 英文...

然后其他样式的 箭头 参考下面文章：

> http://blog.sina.com.cn/s/blog_5e16f1770100l6cv.html

#### 绝对值，直接两边打 |,e.g.|x|

#### **字母上面加符号 波浪线 横线 角号**

加^号 输入\hat{}  或 \widehat{}

加横线 输入 \overline{} 或者 \bar{}  这个好像只能给单个字母加上横线。

加波浪线 输入 \widetilde{}

加一个点 \dot{要加点的字母}加两个点\ddot{要加点的字母}



##文字

设置字体大小，加粗，加下划线，变斜体

> http://blog.sina.com.cn/s/blog_5caa94a0010106ut.html



#### **加粗**  \textbf{}

使用高亮，需要包

#### **下划线** \underline{}

#### **文章标题：**

\title{文章的标题}

\author{}

\date{}										% 空缺时将不会显示时间。

\maketitle

####多级标题自定义样式：

> https://zhuanlan.zhihu.com/p/32712209

\section{}

\subsection{} 

\subsubsection{} 

####带（1）的 开头 

​	$ \left( 1 \right) 

####空格, 字符后面打\

a\

#### 插入项目符号和编号

不带序号

\begin{itemize}

\item 

\end{itemize}

带序号

\begin{enumerate}[step 1]

\item good morning...

\item good morning....

\end{enumerate}

> http://blog.sina.com.cn/s/blog_3fe961ae0101eoht.html



## 矩阵显示

里面记录了6种矩阵符号，以及如何一行写好几个矩阵

> https://jingyan.baidu.com/article/f3e34a128c53aef5ea653542.html

带有省略号矩阵的实现

> http://blog.csdn.net/xiaokun19870825/article/details/50829496

分块矩阵中的虚线表示[下面这个网址真强大]

> http://www.biwako.shiga-u.ac.jp/sensei/kumazawa/tex/form012.html

下面需要下载一个包。

> http://blog.sina.com.cn/s/blog_5e16f1770100h7uc.html



矩阵对齐：

\left[ \begin{array} {cccc:l}

\end{array} \right]

{cc}表示array这个表格中有两列，每一列都是中心对齐。其他的还有 r(right) l(left) 



## 画图

使用pgfplots 扩展包



学习

> http://aandds.com/blog/tool-pgf-tikz.html





####绘制 有向图 到 latex 文件里面

####通过dot2lex分析出 latex 里面的 dot 代码块，然后去调用 graphviz 运行dot 代码块， 再生成 latex 画图代码，再把 latex画图代码 插回 原来的文档中，替换 掉 dot 代码，这时再编译 原来的latex文件。

01 先安装 graphviz  ,正确安装流程：

>http://blog.csdn.net/lanchunhui/article/details/49472949

02 用一个单独封装的 dot2lex 包，因为原始版本是用python2.7调用的，装了3.0的都没法玩了，下面是完整流程。

> https://tex.stackexchange.com/questions/62651/graphviz-and-latex-gives-blank-pdf

然后最后只能通过 CMD命令行 来编译。

pdflatex --shell-escape myfile.tex



缺点：因为 python2.7 不支持中文，所以在 latex 文档 里面出现的所有中文，都被 dot2lex 替换成 乱码了....

解决方式，如果想在 latex 里面 绘制有向图，同时避开乱码问题，新建一个 latex文档，专门用来画有向图，然后单独用 dot2dex编译这个文件, 编译完后会生成一个 XXX-dot2tex-fig1.tex 格式的文件，里面的代码 就是 latex 的绘图库 tikz的代码，把这段代码贴到想要 绘制有向图 的文件中去就可以了。



缺陷2：想在dot代码里面有中文，就是有向图的点或者边 有中文 显示，这就麻烦了。得另外想办法了。dot2lex反正是不可能用了。



###绘图软件生成 latex 代码

都扯淡

一种画有向图的技术：

> http://leungwensen.github.io/blog/2017/a-technique-for-drawing-directed-graphs.html



在线graphviz,生成图片后，截图保存，然后latex导入图片：

> http://www.webgraphviz.com/

上面是使用DOT语言的。

digraph G {
  "1" -> "2"[label="1"]
  "2" -> "3"[label="2"]
  "1" -> "3"[label="3"]
  "1" -> "4"[label="4"]
  "3" -> "4"[label="5"]
}	

###latex导入图片：



####查看 latex 安装了哪些宏包

texmf/tex/latex 下面都是宏包
texmf/doc/latex 下面都是对应的文档



Windows 下如果用 TeX Live，可以用TeX Live Manager 查看。在开始菜单的 TeX Live 2017 -> TeX Live Manager 打开，载入软件仓库，选中要安装的宏包，点安装按钮。



##编译器+编辑器选择

**编译器：TeXLive**

去国内镜像网址下比较快，清华大学和中国科技大学的镜像站。

- <https://mirrors.tuna.tsinghua.edu.cn/CTAN/systems/texlive/Images/texlive2017.iso>
- <https://mirrors.ustc.edu.cn/CTAN/systems/texlive/Images/texlive2017.iso>

然后挂到虚拟光驱上，打开，执行 install-tl-windows.bat 或者 install-tl-advanced.bat 开始安装。最好右键选择管理员模式打开。

安装前，有个需求配置界面，里面点开定制，把其他语言包都点掉不安装。这样所需磁盘空间 能从 5GB减少到4GB。

安装完成后，还需要手动配置环境变量，在高级系统设置的环境变量页面中，系统变量里面找到 PATH，并在末尾添加“;C:\texlive\bin\win32”,然后重启电脑。

**编辑器：TeXstudio**

去官网下载，安装就好。

><http://texstudio.sourceforge.net/>

**显示中文：**

在正在编辑的文档中添加 \usepackage{ctex}命令

添加完usepackage命令后直接编译文档。TeXstudio会自动下载相关包

此时右下角 如果是 UTF-8编码，中文会是乱码，改成GBK即可。

如果一定要用UTF-8编码：

把TeXstudio默认的编译器从PdfLaTeX改为XeLaTeX，编译即可。更改方法是：菜单——选项——设置TeXstudio——在默认编译器那儿：选择XeLaTeX





## Typora 如何分屏显示

看到网上介绍的方法，左边 用sublime打开文件,右边用Typora 打开相同文件。

然后左边编辑完后，ctrl+s保存后，右边自动会刷新显示。哈哈哈。

> https://www.douban.com/note/648901938/





## makdownpad2显示LaTex

【最新结果：开始用 typora 了。 makdownpad2 必须要按F6来网页格式预览，不能实时预览。】

参考资料
>http://www.cnblogs.com/sevenir-code/p/5654180.html

在使用MarkdownPad2时，需要插入数学公式，但live preview失效，记录一下修改过程：

在MarkdownPad中，点击"Tools > Options > Advanced > HTML Head Editor"，这个是自定义头文件。添加下列内容：

<script type="text/javascript"  
　　src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML">
</script>

	实测：上面这种在线调用包的方法已经失效。
	得下包到本地才行了。

或者可以下载MathJax包到本地，解压到硬盘，同理添加：   
**MathJax包下载地址**：
>https://github.com/zohooo/jaxedit/releases

<script type="text/javascript" 
    src="D:/softwares/MarkdownPad 2/jaxedit-0.30/jaxedit-0.30/library/mathjax/unpacked/MathJax.js?config=TeX-AMS-MML_HTMLorMML">
</script>

可以按F6 preview, （F4改变预览位置，F5是否显示预览， F6浏览器预览， F11全屏）

但在用MarkdownPad2直接转成pdf时，发现转出的文件存在问题，不能显示出公式，只显示Latex公式代码，同时页边距也不正常。可以通过下面方法解决：

F6  preview后，在浏览器选择打印，就可以输出pdf了。


## 在线编辑LaTex，并看效果

在线使用JaxEditor:
>https://zohooo.github.io/jaxedit/

LaTex 公式可以从下面的链接里查到
>http://latex.codecogs.com/eqneditor/editor.php

使用须注册,估计生成PDF要收费。
>https://cn.sharelatex.com/

## 在线手写公式，自动生成Tex

左边手写，右边显示Tex公式，还有函数图象显示，学习如何写公式很方便
>https://webdemo.myscript.com/views/math.html#

## 学习方式
just do it,Learn by doing
>https://www.zhihu.com/question/38686577


