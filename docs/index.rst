*******************
Sphinx 入门学习文档
*******************

.. contents:: 目录

.. note::

  文档已同步到 Read the Docs 网站，点击 `此链接 <https://sphinx-learning-jet.readthedocs.io/zh-cn/latest/>`_ 查看。

*****
介绍
*****

Sphinx 是一种用于生成文档的工具，特别是用于编写和生成软件文档。它支持多种标记语言，如 reStructuredText (reST)，并提供了一种结构化的方式来组织和展示文档内容。Sphinx 最初是为 Python 文档而开发的，但它也被广泛用于其他项目和编程语言的文档。

通过 Sphinx，可以创建具有一致风格和结构的文档，包括自动生成的索引、交叉引用、代码注释的自动提取和其他功能。它通常与版本控制系统（如 Git）一起使用，以便在代码和文档之间保持同步，并支持在线和离线浏览。

Sphinx 的文档可以输出为 HTML、PDF 等格式，使其适用于多种输出需求。这使得 Sphinx 成为开发者和项目组织者管理和分享文档的强大工具。

*************************************
reStructuredText 与 Markdown 的区别
*************************************

1. **语法**

  - reStructuredText (reST): 使用标记和缩进来表示结构，如标题、列表和引用。它支持更多的文档元素和复杂结构。
  - Markdown (MD): 使用简洁的符号表示结构，如井号（#）表示标题，星号（*）表示列表。Markdown 的语法更加轻量。

2. **功能**

  - reStructuredText (reST): 具有更丰富的功能，支持生成目录、索引、自动代码注释提取等功能。适用于大型和复杂的文档项目。
  - Markdown (MD): 注重简洁性，不提供像 reST 那样复杂的功能。适用于较小规模、简单的文档和在线写作。

reST 更适合大型文档项目，特别是需要生成复杂文档结构的软件文档。MD 则更适合简单的写作和在线协作。

*********
学习链接
*********

.. _makeOnline:

- **知乎**：https://zhuanlan.zhihu.com/p/264647009，*建议学习*。文章讲述了如何安装 Sphinx、新建项目、启动项目、常用 reST 语法、将项目部署到 `Read the Docs <https://about.readthedocs.com/>`_ 网站（一个线上免费文档托管项目）等。
- **ReStructuredText 快速教程**：https://rst-tutorial.readthedocs.io/zh/latest/index.html，*建议学习*。文章讲述了 reST 的常用语法，若想要观看源码，点击页面右上角的 Edit on GitHub。
- **Sphinx 官方网站**：https://www.sphinx-doc.org/en/master/。网站为英文，包括了入门教程、安装 Sphinx、详细的文档等内容。
- **reST 官方网站**：https://docutils.sourceforge.io/rst.html。网站为英文，包括了用户文档（User Documentation，入门教程）、参考文档（Reference Documentation，reST 语法规范）等。
- **reST 规范**：reStructuredText Markup Specification。网站为英文，文章讲述了 reST 标记语言详细的技术规范。

*********
构建文档
*********

构建为 HTML 文档
=================

1. **线上文档**：参考 :ref:`知乎 <makeOnline>` 的文章，将文档项目上传到 GitHub 等线上代码仓库，并部署到 Read the Docs 网站。
2. **本地文档**：项目目录下执行命令 ``sphinx-autobuild source build/html``，可以访问本地文档。

构建为 PDF 文件
================

1. **使用 Overleaf 网站线上构建** （电脑不需要安装 LaTeX 环境）

  - 在项目根目录下执行 ``make help`` 查看帮助文档，执行 ``make latex`` 在 *build* 目录下生成 *latex* 目录，将 *latex* 目录压缩成 ZIP 文件。
  - 进入 `Overleaf 网站 <https://www.overleaf.com>`_ ，点击 *New Project* 按钮 -> *Upload Project* 按钮上传 ZIP 文件。
  - 进入网站项目，点击 *Download PDF* 按钮下载 PDF 文件。 

2. **本地构建**

  - 安装 LaTeX 环境：Ubuntu 或者银河麒麟操作系统下，执行 ``sudo apt install texlive-full``。该命令会安装所有 LaTeX 相关的包，包含了大量的工具、宏包、字体和配置文件。
  - 在项目根目录下执行 ``make latexpdf``，文档生成在 *build/latex/\*.pdf* 下。

***************************
如何使用 Read the Docs 网站
***************************

网站介绍
=========

推荐使用 `Read the Docs 网站 <https://about.readthedocs.com/>`_ 来搭建在线文档。该网站能够实时自动构建文档，可以设置文档版本号。此外，`sphinx-rtd-theme` 主题相较于 PDF 更适用于 HTML。

把项目上传到 GitHub
===================

- 新建 `.gitignore <https://github.com/jetyang98/sphinx-learning/blob/master/.gitignore>`_ 文件。

  .. code-block:: text

    .vscode
    build

- 执行 ``git init`` 初始化为 Git 项目，``git add .``, ``git commit -m "init repo"`` 提交文档代码。
- 在 GitHub 网站新建一个仓库，把项目推送到 GtiHub。命令类似如下：

  .. code-block:: bash
      
    git remote add origin https://github.com/jetyang98/sphinx-learning.git
    git branch -M master
    git push -u origin master

注册 Read the Docs 网站并添加配置文件
======================================

- 注册一个网站账号，并将其与 GitHub 账号关联，以便能够访问 GitHub 仓库。
- Read the Docs 网站的默认源码目录为 *docs*，使用命令 ``git mv source docs`` 将 *source* 目录修改为 *docs*。
- docs 目录下，添加 Python 依赖文件 `requirements.txt <https://github.com/jetyang98/sphinx-learning/blob/master/docs/requirements.txt>`_。

  .. code-block:: text

    Sphinx==7.2.6
    sphinx-rtd-theme==2.0.0

- 根目录下，添加 Read the Docs 配置文件 `.readthedocs.yaml <https://github.com/jetyang98/sphinx-learning/blob/master/.readthedocs.yaml>`_。

  .. code-block:: yaml

    # .readthedocs.yaml
    # Read the Docs configuration file
    # See https://docs.readthedocs.io/en/stable/config-file/v2.html for details

    # Required
    version: 2

    # Set the OS, Python version and other tools you might need
    build:
      os: ubuntu-22.04
      tools:
        python: "3.12"
        # You can also specify other tool versions:
        # nodejs: "19"
        # rust: "1.64"
        # golang: "1.19"

    # Build documentation in the "docs/" directory with Sphinx
    sphinx:
      configuration: docs/conf.py

    # Optionally build your docs in additional formats such as PDF and ePub
    formats:
      - pdf
      # - epub

    # Optional but recommended, declare the Python requirements required
    # to build your documentation
    # See https://docs.readthedocs.io/en/stable/guides/reproducible-builds.html
    python:
      install:
        - requirements: docs/requirements.txt

- 提交新的代码到 GitHub，在 Read the Docs 网站导入该项目，网站会根据配置文件自动构建 HTML 文档。

管理文档版本
==============

Read the Docs 网站能够根据 GitHub 仓库的分支和标签生成不同版本的文档，管理员可以选择公开哪些分支或者标签下的文档。

- 项目根目录下执行 ``git tag 1.0.0``，新建一个标签，``git push --tags`` 将标签推送到 GitHub 网站。
- Read the Docs 网站下点击 *Versions* 标签查看 1.0.0 版本是否激活（只有激活的版本才会显示在文档中），激活的版本会自动构建并生成 HTML 文档。
