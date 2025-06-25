---
title: "First_post"
date: 2023-02-11T13:02:32+08:00
draft: false

tags: ["hugo", "blog"]
categories: ["about me"]
---

Hello,world!  

# Blog
## 主题  
- [doc](https://hugoloveit.com/zh-cn/theme-documentation-basics/)  
- [github](https://github.com/dillonzq/LoveIt)  
- [迁移教程](https://kiosk007.top/post/再见hexo你好hugo/#开始迁移)

## Usage
### 创建新文章
```bash
hugo new posts/new_post.md
```
### 预览
```bash
hugo serve --disableFastRender
```
### 生成
```bash
hugo
```
### 部署
```bash
cd public
git add .
git commit -m "update"
git push origin master
```
or
```bash
./deploy.sh "commit message"
```


# 如何使用本地图片
一个实现逻辑：
1. Hugo 博客的根目录有一个 static 目录，这个 static 目录就是用来存放一些静态文件，比如图片、css、js 文件等。
2. 执行 hugo 命令的时候，会把 static 目录下的子目录或文件复制到 public 目录下。比如我在 static 下添加了一个 img 子目录，并且在 img 子目录放了图片，那执行 hugo 命令后，就会把 static\img 文件的内容拷贝到 public\img 里面。
3. 大家都知道Hugo博客网站展示的其实是public下的内容，因此markdown文章里引用图片的时候，得引用 pubic 下的图片才可以。
具体操作非常简单，分2步：
1. 在 static 目录下创建 img 子目录，把 markdown 要使用的图片放在 static\img 目录里。
2. 在 markdown 文件里，按照如下格式引用图片(这里假设图片名称叫wechat.png)。这样最终public目录下生成的静态页面就可以引用到 public\img 下的图片了。