# 个人主页
学习资源笔记汇总及学习日志。

> WARNING：本仓库所有 `.md` 文档使用 [Typora](<https://www.typora.io/>) 软件编写，部分内容（包括但不仅限于公式）可能无法在 GitHub 上正常显示！！！

## 学习日志

- 2019.09.01：近来陆陆续续也是看了一些线代/矩阵理论的东西，主要是马同学的 [线性代数系列博客](<https://www.matongxue.com/columns/3/>)，算是大开眼界了。此外还有知乎上的 [矩阵求导术（上）](<https://zhuanlan.zhihu.com/p/24709748>)& [矩阵求导术（下）](<https://zhuanlan.zhihu.com/p/24863977>)。身为一个 AI 界菜鸡码农，不求像数学系大佬们一样“徜徉在数学的海洋中无法自拔”，但对线代/矩阵理论和概率统计有相当程度的认识还是很有必要的。另，数学部分笔记也上传至仓库 [Joee1995/about-math](<https://github.com/Joee1995/about-math>)。
- 2019.08.14：语义搜索项目子任务 - 评论数据中的特定事件检测（尚未完成），衍生代码库 [Joee1995/eng_text_norm](<https://github.com/Joee1995/eng_text_norm>)，一个英文文本数据规范化工具。
- 2019.08.10：因为接下来要做语义搜索/知识图谱相关的项目，所以快速过了一些相关的基础知识以及一些论文，算是准备工作。主要包括：[W3Cschool - XML 教程](<https://www.w3cschool.cn/xml/?>)，[W3Cschool - RDF 教程](<https://www.w3cschool.cn/rdf/?>)，[W3C - RDF 的 SPARQL 查询语言](<https://www.w3.org/TR/rdf-sparql-query/>)，[W3Cschool - MongoDB 教程](<https://www.w3cschool.cn/mongodb/?>) 以及 [thunlp/KRLPapers](<https://github.com/thunlp/KRLPapers>) 总结的论文。基本都还没有全部刷完，只看了基础的部分，相关笔记已经上传至新建仓库 [Joee1995/semantic-search](<https://github.com/Joee1995/semantic-search>)，然后作为子模块引入本仓库。

## 仓库结构

本仓库文件结构如下：

```
.
|--- about-math         # 数学学习资源笔记
|--- about-ml           # 机器学习资源笔记
|--- environment        # 学习环境的搭建记录
|--- learning-tools     # 一些高效学习工具的笔记
     |--- bspwm
     |--- docker
     |--- vim
|--- methodology        # 一些学习方法论的笔记
|--- semantic-search    # 语义搜索资源笔记
     |--- notes
|--- static             # 静态资源文件
     |--- images
|--- README.md          # 当前文件
```

> ATTENTION：为了避免仓库过于庞大，除了环境搭建、学习工具和学习方法论，其他部分将另建仓库然后作为子模块引入本仓库。

## 快速开始

本仓库包含子模块，运行以下命令获取完整仓库：

```
$ git clone https://github.com/Joee1995/homepage.git
$ cd homepage
$ git submodule init
$ git submodule update
```

或者采用更简单的方式：

```
$ git clone --recursive https://github.com/Joee1995/homepage
```

## 欢迎交流

![communication-qr-code_36759691-a392-46c8-bd8f-e1c60ae58905](./static/images/communication-qr-code_36759691-a392-46c8-bd8f-e1c60ae58905.jpg)
