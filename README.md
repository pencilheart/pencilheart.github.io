# GitHub Pages+ Hexo搭建自己的个人博客
（Hexo……把我搞瘫了）

两天的学习，查了众多大佬的好文，整理出来，算对自己学习的一个总结。win10亲测。

**注意：文中代码区皆在Git Bash中输入**

### 1. 网页端
#### 1.1 注册GitHub账号
#### 1.2 创建Your_username.github.io的Public仓库

### 2. 本地端
#### 2.1 [环境配置](https://hexo.io/zh-cn/docs/)
* [安装Git](http://git-scm.com/download/)
* [安装Node.js](https://nodejs.org/ko/blog/release/v9.11.1/)，一路下一步。

#### 2.2 本地安装Hexo

```
cd d:/blog			# 或者右键文件夹根目录Git Bash 
npm i hexo-cli -g		# 安装Hexo
Hexo -v				# 检查Hexo，显示版本号继续
hexo init			# 初始化Hexo博客
npm install			# 安装组件
hexo g				# 生成静态网页
hexo s				# 打开服务器，可以在http://localhost:4000/ 查看
ctrl+c				# 关闭本地服务器
```
实现本地查看博客，jer动不？
#### 2.3本地绑定GitHub

```
git config --global user.name "Your_username"
git config --global user.email "Your_email@qq.com"   
ssh-keygen -t rsa -C "Your_email@qq.com"		# 安装本地SSH
```
Enter三连。
```
cat ~/.ssh/id_rsa.pub		# 生成SSH密码
```
打开github网站，登录后点击头像-settings，左侧SSH and GPG keys，新建一个SSH，名字随便，填入上步的得到的SSH密码。
```
ssh -T git@github.com
```
检测到用户名即为成功绑定。
#### 2.4修改本地包上传目的地为GitHub

修改本地根目录文件_config.yml
修改最后一行的配置为：

```
deploy:
  type: git
  repository: https://github.com/Your_username/Your_username.github.io.git
  branch: master		
```

>新版github博客只可显示master分支
![image](https://github.com/pencilheart/pencilheart.github.io/blob/master/2020/03/12/2020-03-12-hexo/settingsss.png)
#### 2.5第一次上传

```
npm install hexo-deployer-git --save	#上传插件，自动装入package.json文件中
hexo clean				#清缓存
hexo g					#生成静态网页
hexo d					#上传到GitHub  
```
**:boom:上传完毕后，浏览器访问https://github.com/Your_username/Your_username.github.io 即可查看你的博客了。**

#### 2.6写博文
以下两种方法都可创建新博文：
一种是直接在/source/_posts添加.md文件
一种是根目录下敲代码

 ```
  hexo new post "article title“   
 ```

但最终都需要用markdown语法编辑好后保存。

>Win下Markdown软件推荐[VScode](https://code.visualstudio.com/)，是不是有点屈才？附[1分钟VScode入门](https://www.cnblogs.com/huyong/p/4573041.html)以及[1分钟markdown语法学习](https://www.jianshu.com/p/191d1e21f7ed)。

#### 2.7后续上传
从第二次上传开始就无须安装插件了，只需三行。
 ```
hexo clean
hexo g
hexo d
 ```
### PS

#### p1:[Hexo技巧](https://hexo.io/zh-cn/docs/)
* [添加图片](https://hexo.io/zh-cn/docs/asset-folders.html)

  使用自带的相对路径引用标签插件`{% asset_img example.jpg This is an example image %}`
* [添加支持emoji](https://kinboyw.github.io/2018/10/29/Hexo-NexT-%E5%BC%80%E5%90%AF-emoji/)

  采用hexo-renderer-markdown-it插件代替hexo-renderer-markdown
* 还未验证
  * [hexo加目录](https://pengloo53.gitbooks.io/hexo/content/chapter2/7%20%E6%B7%BB%E5%8A%A0%E6%96%87%E7%AB%A0%E7%9B%AE%E5%BD%95.html)
#### P2:更换博客模板—推荐[Next](https://github.com/theme-next/hexo-theme-next)模板

* [Next官方主题配置](http://theme-next.iissnan.com/theme-settings.html#set-page-tags) 、[Next民间个性化](https://guanqr.com/tech/website/hexo-theme-next-customization/#top)

#### P3:跨电脑修改博客
需要用Git把线上包下载到本地，链接最好采用SSH链接，使用如下命令：

```
git clone git@github.com:Your-username/Your-username.github.io.git
```
之后在本地修改，再上传即可

### 参考链接
* [Hexo官方文档](https://hexo.io/zh-cn/docs/)
* [Next官方文档](http://theme-next.iissnan.com/theme-settings.html#set-page-tags)
* [NPM介绍](https://www.runoob.com/nodejs/nodejs-npm.html)
* [NPM镜像](http://npm.taobao.org/)
* [手把手教你使用Hexo + Github Pages搭建个人独立博客—令狐葱@前端笔记](https://linghucong.js.org/2016/04/15/2016-04-15-hexo-github-pages-blog/ )
* [超详细Hexo+Github博客搭建小白教程—韦阳](https://zhuanlan.zhihu.com/p/35668237)
* [Hexo 博客搭建指南—Limedroid](https://github.com/limedroid/HexoLearning)