# 项目说明 #

本项目主要利用 ant 对前端脚本做统一管理，支持以下功能：

- jshint
- csslint
- spm (seajs)
- css compress
- 文件版本管理
- 区别正式和测试环境
- 上传线上ftp目录
- 记录发布日志

### 依赖 ###


- [ANT](http://ant.apache.org/bindownload.cgi)
- [nodejs](http://nodejs.org/)
- [ant-contrib](http://ant-contrib.sourceforge.net/) 支持执行一些逻辑运算
- [commons-net](http://commons.apache.org/net/) 支持FTP上传
- [ant-jshint](https://github.com/philmander/ant-jshint) 支持jshint对js的检查
- [csslint](https://github.com/stubbornella/csslint/wiki/Command-line-interface)
- [spm@0.4.1](https://github.com/seajs/spm)  使用的旧版，主要为了打包和压缩js文件


### 文件说明 ###

- common-build.xml  包括通用的配置与通用的任务
- build.xml 需要放置在项目代码目录中，一些项目相关的配置及自定义的任务
- tools 这个目录放置一些common-build.xml中要使用的一些依赖包

### 命令说明 ###

- `ant`  除ftp上传外，其它工作都在这个命令里做掉
- `ant pub` 打上发布时间戳, 发布到ftp
- `ant jshint` 也可以单独运行一些命令


## 前端文件的管理说明 ##

前端中的css, js等文件因为运行简单，所以在文件不多的情况上管理也非常简单。但是当项目复杂，文件众多，层层依赖时，这些文件的管理就是比较重要的事了，管理的好会显著接高效率，现在有了像seajs这样的模块化js开发框架，管理js,css就更加方便了。

### 目录 ###

- build (本项目文件)
- dev (主开发目录)
- dev/libs (seajs的模块目录)
- dev/mbb-libs (与业务相关的模块目录)
- dev/test (测试环境文件，可以同步到测试环境)
- dev/release (正式发布文件，可以发布上线，也可同步到预发布环境)
- dev/page (网站子项目目录)
- dev/page/app (子项目)
- dev/page/app/branches 
- dev/page/app/trunk
- dev/page/app/trunk/src (主要源代码目录)
- dev/page/app/trunk/src/build.xml (从本项目拷贝出来build.xml文件)
- dev/page/app/trunk/demo
- dev/page/app/trunk/test

 
### 版本 ###

每个项目都需要定义一个版本号，发布时在test和release里都会依据build.xml里定义的版本来创建目录。
这样新版本上线不会影响线上在使用的版本，也会像svn一样能很好的隔离不同修改的干扰。借助seajs的[SeaJS 里版本号和时间戳管理的最佳实践](http://lifesinger.wordpress.com/2011/08/01/best-practice-of-version-management/) 版本的升级也非常方便。



