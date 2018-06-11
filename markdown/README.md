# 简介

看下面

## 文章的组织形式

译文的文件命名统一规范为：

```
<两位数的章序列> <章名称>/<两位数节序列> 节名称.md
```

如果有小节的话：

```
<两位数的章序列> <章名称>/<两位数节序列> 节名称/<两位数小节序列> 小节名称.md
```

例如：

```
01 Getting started/01 OpenGL.md
或
05 Advanced Lighting/03 Shadows/02 Point Shadows.md
```

## 样式指南

在文档的写作过程中，请遵守我们的[样式指南](https://github.com/Guang1234567/RootNotebook/tree/master/docs/styleguide.md)方便之后的校对以及修改工作。

## 构建

首先请安装Python，2和3都可以，之后初始化环境：

```bash
$ pip install mkdocs
$ python setup.py install
```

初始化以后，每次构建只需要输入以下指令即可，构建后的文件在`site`文件夹内：

```bash
$ mkdocs build --clean
```

如果只是想测试的话，请输入以下指令：

```bash
$ mkdocs serve
```

部署的网页可以通过`127.0.0.1:8000`来访问。

## 部署文档到 github pages

### 方式一 (最简单的方式)

运行

`mkdocs gh-deploy`

命令解释:
[如何发布文档](https://www.mkdocs.org/user-guide/deploying-your-docs/)
[如何配置 remote_branch 参数](https://www.mkdocs.org/user-guide/configuration/#remote_branch)
[如何配置 remote_name 参数](https://www.mkdocs.org/user-guide/configuration/#remote_name)

这命令会把 `/site` 目录推送到远程的git仓库的`gh-pages`分支.

### 方式二 

如果你想把 `/site` 目录(或别的什么目录名, 如` /dist` 等等) 发布到 `gh-pages` 分支的话,以下是一种我认为最简单的方法:

第一步

`/site` 目录需要被 git 记录，于是后面我们才可以用它作为`子树（subtree）`，因此 `/site` 不能被 `.gitignore` 规则排除

第二步

`git subtree push --prefix site origin gh-pages`

搞定. 其中:

`site`代表子树所在的目录名
`origin` 是 remote name
`gh-pages` 是目标分支名称

其实, 就是方法一的具体实现