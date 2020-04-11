## 从零开始：搭建一个测试练习平台

### 一、环境准备
1、准备一台电脑<br>
2、官网下载最新版Intellij IDEA，破解步骤：<a href="https://segmentfault.com/a/1190000021220727?utm_source=tag-newest" target="_blank">点我传送</a><br>
3、官网下载最新版PyCharm，破解步骤同上，区别是配置路径不同<br>
4、风刑软件站，下载安装VMware虚拟机破解版，再找个CentOS7的镜像文件安装，<br>
5、官网下个xshell6，不用破解<br>
6、下载JavaSE最新版本，目前是13，配环境变量<br>
7、下载python最新版，目前是3.8，不用配环境变量，安装时勾选，能自动配<br>
### 二、检验工具
1、python：<br>
1)基本语法不难，多用就熟了<br>
2)库很多，windows系统在cmd中执行pip命令安装即可,数据分析类方便直观<br>
3)自动化测试方面，根据需求，封装函数，数据分离，生成报告，没了。<br>
4)用selenium时，要启动webdriver控制谷歌浏览器，需要下载插件chromedriver.exe，
<br>&nbsp;找自己浏览器对应版本，下载地址:<a href="http://chromedriver.storage.googleapis.com/index.html" target="_blank">点我传送</a>
<br>&nbsp;把插件放python默认安装目录下<br>
5)20200318，最近很多股票打75折，我用以前学的财务知识挑股票，很累，票太多。
<br>&nbsp;于是想用python做个程序，根据条件选股票。优矿依赖它平台，不顺眼，东方财富新浪百度等API陈旧不易用
<br>&nbsp;无意中发现了一个库，叫证券宝 <a href="http://baostock.com/baostock/index.php/%E9%A6%96%E9%A1%B5" target="_blank">官方文档点我传送</a>，国内开源，能pip安装，用了用发现，目前的股票接口，都是用于趋势分析的，
<br>&nbsp;我觉得一根线也能看出技术是扯淡，不过细想，A股十几年都是3000点，价值投资也是扯淡。遂作罢<br>
6)python3.x版本连接mysql数据库要pip install mysqlclient，然后import MySQLdb使用，具体用法<a href="https://www.runoob.com/python/python-mysql.html" target="_blank">点我传送</a><br>
7)安装python最新版后，cmd中运行pip没用，最后发现是本机安装了loadrunner，环境变量冲突了，where pip查环境变量，删除冲突项即可。
<br>&nbsp;<a href="https://blog.csdn.net/h18208975507/article/details/103049635" target="_blank">可参考</a>
2、java：<br>
<br>1)暂时搭建一个web网页，springboot + spring data jpa + mysql
<br>2)打开Intellij IDEA，新建spring项目，选jdk13，.properties中开日志，设tomcat端口
<br>3)建目录：web，dao，service，启动类加@ComponentScan(basePackages = {"com.*"})，不然扫不到其他类
<br>4)建页面：两种方式
<br>&nbsp;有前端程序员的公司，写好页面，留ajax等后端程序员传数据即可。
<br>&nbsp;没前端程序员的公司，后端程序员需要用引擎模板开发页面，java会自己渲染页面并传数据，前端引擎模板jsp，freemarker，thymeleaf都一样，累死后端吧
<br>我选thymeleaf，要在html标签开头加一句咒语xmlns:th="http://www.thymeleaf.org"，就可以用th标签在页面里操作后端来的变量了
<br>要在templates下建h5页面，去bootstrap官网，不用下载，引cdn方式的文件，js和css都是现成的，官网能看组件，还自适应，后端的福音
3、linux
<br>1)虚拟机里改分辨率太费劲，所以直接用xshell
<br>2)网络选桥接，改/etc/sysconfig/network-scripts/ifcfg-ens33文件的onboot为yes，能连外网
<br>3)关防火墙，虚拟机才能ping通宿主机，具体参考<a href="https://blog.csdn.net/hskw444273663/article/details/81301470">点我传送</a>
<br>4)yum update更新一下库，然后安装docker，书上方法太旧，2020年3月6号，docker最新是19版本，
<br>&nbsp;步骤参考<a href="https://www.runoob.com/docker/centos-docker-install.html">点我传送</a>  教程太多，总结一下：
<br>&nbsp;1-安装依赖软件；2-设置仓库；3-安装社区版；4-启动docker；5-下载较大的软件网会断，配个加速器 # vi /etc/docker/daemon.json，
<br>&nbsp;这个daemon.json文件默认没有，官网有介绍，管各种配置的，里面写{"registry-mirrors":["https://n9h3vi0d.mirror.aliyuncs.com"]}
<br>5)以后的操作都在docker里进行，先安装个mysql，步骤参考菜鸟教程:<a href="https://www.runoob.com/docker/docker-install-mysql.html" target="_blank">点我传送</a>
<br>&nbsp;第四步运行容器之后，需要执行“docker exec -it 这里填容器id或名称 /bin/bash“ 这就可以在shell中使用mysql了
<br>&nbsp;进shell之后，登陆账户，mysql -u root -p，完成，
<br>&nbsp;mysql用的是3306端口，在第5）步，我将虚拟机里，docker容器的3306端口，映射给了虚拟机的3306端口，
<br>&nbsp;所以，只要docker启动mysql，我就能通过虚拟机的ip+3306端口使用mysql。
<br>&nbsp;为了方便使用，我要在宿主机（我的win10笔记本)用Navicat for mysql连虚拟机的3306端口。
<br>&nbsp;官网下载Navicat最新版本（目前是15）。下载破解程序，教程及地址：<a href="https://www.jb51.net/database/710931.html" target="_blank">点我传送</a>
<br>&nbsp;以上，虚拟机+centOS+docker+mysql终于搭建完成。linux命令+docker命令+mysql命令得多练。
<br>6)docker一句话总结：<br>
docker是一个容器干一件事，所以搭建环境，先要下载各种新镜像，通过手工配置或者写dockfile配置把镜像启动为容器，一切配好环境能用，就把这些镜像导出，再上传到私服仓库，然后本机下载dockcompose，写个dockercompose.yml，里面是环境需要启动的各种容器。<br>
要复制环境时，在新机器上安装docker，然后从私服拉取镜像，用复制来的dockercompose.yml直接用命令运行，就完成了。<br>
查了这么多，<a href="https://blog.csdn.net/londa/article/details/91815208" target="_blank">这篇文章</a>终于说到点子上了。
### 三、项目中的小问题
1、spring boot会自动扫描@SpringBootApplication所在类的同级包以及下级包里的bean。<br>
<br>&nbsp;所以建包若在别处，入口类会扫不到，需要加注解：
<br>&nbsp;@ComponentScan(basePackages = {"com.*"})
<br>&nbsp;@EnableJpaRepositories("com.*")
<br>&nbsp;@EntityScan("com.*")<br>
2、springboot使用rest，是看谁继承JpaRepository接口的，实体类加s是spring data REST的默认规则<br>
3、某天虚拟机ip变了，于是设为静态ip，却发现docker的mysql容器3306端口连不上，最后发现systemctl restart docker重启docker服务就好了<br>
4、docker上部署了两个容器，一个是web项目，一个是mysql，结果web连不上数据库，最后发现是防火墙挡住了。<br>
<br>&nbsp;我刚才是是关了防火墙，参考的这个<a href="https://www.cnblogs.com/zuokun/p/10577641.html" target="_blank">点我传送</a>。
<br>&nbsp;进而又查了查docker容器间的通讯方式，<a href="https://blog.csdn.net/u013355826/article/details/84987233" target="_blank">点我传送</a>他这个需要初始化容器的时候就配好<br>
5、突然今天xshell时不时地连不上虚拟机，我都已经配了静态IP了，结果发现是自己手机的ip跟虚拟机冲突了，
<br>&nbsp;于是上路由器管理页面，在DHCP池里挑了个IP，跟自己手机的mac地址绑定，就好了
### 四、监控
1、ant、nexus<br>
在看junit自动化构建，瞥见构建工具ant <a href="https://blog.csdn.net/shandong_chu/article/details/37902273" target="_blank">（点我传送）</a>，它跟maven差不多，我就想使用maven的deploy(在构建环境中，将最终打包的文件复制到远程仓库当中用于和其他开发者和项目进行分享。)，
<br>&nbsp;于是就在docker上安装了nexus私服，具体参考<a href="https://www.cnblogs.com/wotoufahaiduo/p/11223834.html" target="_blank">点我传送</a>
<br>&nbsp;注意两点：
<br>&nbsp;&nbsp;一是我用docker装的nexus，很简单，但最好在上面链接里的第五步，指定自己的目录
<br>&nbsp;&nbsp;二是这个博主在maven的setting.xml文件里少配了一处，导致传jar包报错没权限，具体<a href="https://blog.csdn.net/weixin_43554942/article/details/103739658" target="_blank">点我传送</a>
2、nmon<br>
下载压缩包，解压后找对应版本，执行export PATH="$PATH:/路径"配下环境变量，就能直接用了，监控结果用excel分析，我那vb工具直接把结果统计出来即可。
<br>&nbsp;我觉得还可以写个工具实现一键完成部署、打点、结果汇总，日后再说吧
3、java监控<br>
工具很多，可以用java自带的visualVm远程监控，远程只需在java项目启动时加参数 <a href="https://blog.csdn.net/mn960mn/article/details/73958701" target="_blank">点我传送</a>，docker中的web项目加参数写在docker run -e ""里面
4、top<br>
Linux自带，看进程的，<a href="https://www.cnblogs.com/fuqu/p/10230385.html" target="_blank">具体点我</a>，可用于查进程ID定位代码
5、vmstat<br>
Linux自带，看内存的，<a href="https://www.cnblogs.com/jiujuan/p/9034165.html" target="_blank">具体点我</a>
6、iotop<br>
需安装，用于定位正在IO的进程。<a href="https://www.cnblogs.com/yinzhengjie/p/9934260.html" target="_blank">具体点我</a>
### 五、自动化测试
1、TestNG<br>
<a href="https://blog.csdn.net/qq_32821227/article/details/53816639" target="_blank">(点我传送)</a>跟junit差不多，看到junit更新到了5，就学习了一下，它内嵌在spring boot test包里，springboot项目默认有这个包。
<br>&nbsp;简单来说，右键要测的类生成测试类，在test目录下，给测试类加@SpringBootTest注解，给方法加@Test注解，
<br>&nbsp;直接@Autowired拿到要用的bean，在测试方法里写逻辑，加断言判断，最后用maven的test按钮运行一下，就能自动测完所有内容。
<br>&nbsp;可以看看这个junit4的简单上手 <a href="https://www.cnblogs.com/vipstone/p/9908545.html" target="_blank">点我传送</a>，结合junit5的文档看 <a href="https://junit.org/junit5/docs/current/user-guide/#writing-tests-assertions" target="_blank">点我传送</a>
<br>&nbsp;啰嗦一句，单元测试的方法，加@Transactional可以直接回滚数据，哪个包的@Transactional都行，但数据库的主键还是对自增，不想回滚数据就加@Rollback(false)
<br>&nbsp;再啰嗦一句，用junit时尝试了一下java的lambda和双冒号::，没有get到双冒号的使用场景<a href="https://blog.csdn.net/weixin_34249678/article/details/92428476?depth_1-utm_source=distribute.pc_relevant.none-task&utm_source=distribute.pc_relevant.none-task" target="_blank"> 点我传送</a>
2、jenkins+jmeter<br>
接口自动化：简言之，就是用jmeter做好脚本，设置为运行一次，放服务器上，jenkins设置构建后触发jmeter命令行，测试报告发邮件。<a href="https://www.cnblogs.com/zishi/p/8448073.html" target="_blank">具体步骤</a>+<a href="https://www.cnblogs.com/wldan/p/10946919.html" target="_blank">发邮件</a>
3、python自动化<br>
目前常见的是用法是 selenium+unittest+htmlreport,selenium支持多种语言，用于模拟人工操作浏览器，需pip安装
<br>&nbsp;unittest是python自带的单元测试框架，跟junit、testng几乎一样，通过testsuite调run方法批量执行测试类，
<br>&nbsp;htmlreport用于生成测试报告，pip安装，testsuite用htmlreport调用run即可。
<br>&nbsp;一个python自动化框架用法：先封装函数：打开浏览器、进入页面、获取页面元素、操作、判断结果，共5步，这里注意获取元素要用显式等待，报错要截图，
<br>&nbsp;然后是测试数据（或者叫测试用例）与代码分离，测试结果可以写入表格，也可以生成html。
<br>&nbsp;一个页面对应一个class，class里多个函数对应多个要测的功能，testsuite写在入口方法，添加所有class，便可运行所有测试。
### 六、接口测试
1、postman<br>
现在主要推销自己的客户端，看来想做成一个大平台，在官网号称可以用于CI自动化。快速上手 <a href="https://blog.csdn.net/fxbin123/article/details/80428216" target="_blank">点我传送</a>
### 七、单元测试
1、mock<br>
mock的工具很多，spring boot test内置的是mockito，和junit配合用的。它就是用反射机制拿到类，然后让人手动设置方法返回值而已，
<br>&nbsp;之后再判断方法的调用顺序呀、次数呀等等细节，最后加个junit的断言判断，具体以后用到再复习吧 <a href="https://blog.csdn.net/cckevincyh/article/details/82228245" target="_blank">点我传送</a>
<br>&nbsp;此外，mock还能测controller，如果哪天有针对单元测试的活儿，可以先看一眼这个 <a href="https://www.cnblogs.com/jpfss/p/11271015.html" target="_blank">点我传送</a>
<br>&nbsp;python的unittest自带mock，<a href="http://blog.itpub.net/69908432/viewspace-2647614/" target="_blank">具体参考。</a>
### 八、性能测试
1、jmeter
<br>&nbsp;<a href="https://www.cnblogs.com/imyalost/p/7062784.html" target="_blank">这篇</a>作为入门看着笔记方便,但要是快速上手，还是徐景峰<a href="https://mp.weixin.qq.com/s?__biz=MzI0NzEyODIyOA==&mid=2247484493&idx=1&sn=1dc17d69d6b15a186b9ff6dfe555950e&chksm=e9b58d86dec204908863621b3213efdaab0a3bcbd2e7248f0ea50f2059b2938699fa025079ea&mpshare=1&scene=24&srcid=&sharer_sharetime=1567989008735&sharer_shareid=6acb53c777c0956c7b3b43c93583c9e7#rd" target="_blank">这篇</a>思路正确，其他很多上手文章，讲不到点上。入门之后，<a href="https://www.cnblogs.com/testwjr/p/9156705.html" target="_blank">这篇</a>可用作总结提升。
<br>&nbsp;新建csv文件，可以通过txt改后缀，然后用记事本编辑。如果直接用xls改后缀，会读取乱码
<br>&nbsp;做参数关联，若用正则，被参数化的值必须是(.*?)，不然正则无效
2、loadrunner：
<br>&nbsp;1)关于tps、vu、响应时间的关系
```
我做了一次实验，发现如下结论
Vu  响应时间  tps
1    0.003    315
10   0.006    1670
100  0.061    1478
300  0.183    1486
1个vu时，1000毫秒/平均响应时间=tps。但1个以上的vu，这个公式就不适用了。
Vu增加，响应时间会变慢，tps变大，但到了一定值，tps反而减少。
因此，想变大tps，先加vu。若想变小tps，可以继续加vu，但此时最好设置pacing。
我还听到一个公式： vu = pacing * tps 。但实验发现此公式不准。
我按照公式，vu不变，设置目标tps，得出pacing时间，但运行后，发现tps比目标少25%，所以不准。如果想加pacing，可以直接加成需求给的时间，比如复杂交易不大于400毫秒。不加pacing的话，响应时间是最快的。所以，如果pacing设置的小于它最快的时间，这个pacing就不起作用了。
```
<br>&nbsp;2)关于场景：场景与计划共四种组合方式，<a href="https://www.cnblogs.com/snailvsstar/p/6845964.html" target="_blank">具体参考</a>
<br>&nbsp;3)loadrunner打印日志时，若返回报文内容过多，会显示不全，但不影响web_reg_save_param抓数据。
<br>&nbsp;4)用lr转码中文，数据提交后在页面发现中文最后有空格，<a href="https://my.oschina.net/erichd/blog/499680" target="_blank">解决方法</a>
### 九、前端
1、最近面试项目要用vue.js，它基于nodejs，<a href="https://blog.csdn.net/woshinannan741/article/details/51337484" target="_blank">nodejs是什么</a>。npm是它自带的包管理工具，cnpm是淘宝做的国内版，安装之后，用法一样。<br>
继续学vue，文档提示我参考webpack，Webpack是一个前端资源加载/打包工具，可以将多种静态资源 js、css、less 转换成一个静态文件，减少了页面的请求，用cnpm安装。我现在不需要。<br>
接着看，文档说vue有两种安装方式，要么npm装，要么页面引个cdn链接，效果一样，毕竟nodejs和我的谷歌浏览器用的都是谷歌的V8引擎。<br>
文档看完，一句话描述，vue本质是封装好的js函数（学名叫框架），主要通过new Vue({})操作一个dom元素，完成各种动作。<br>
当然，一个前端框架有除了js还有html、css，vue做完的项目肯定很大，需要webpack打包，于是vue又封装了一下，出了个工具叫vue cli，<a href="https://www.runoob.com/vue2/vue-install.html" target="_blank">cnpm安装它</a>，能生成个单页模板项目，能用开发工具打开，以后直接在里面写代码即可。<br>
我打开这个vue模板项目，入口文件是个APP.vue,  .vue文件是一个自定义的文件类型，用类似HTML的语法描述一个Vue组件。每个.vue文件包含三种类型的顶级语言块 `<template> <script> <style>`。这三个部分分别代表了 html,js,css。<br>
一个完整的vue项目，有多个.vue文件，每个都是一个组件，<a href="https://www.jianshu.com/p/f5804394819c" target="_blank">参考链接</a>。<br>
这样看来，vue项目的cdn安装方式只能做些小功能，项目中还得用nodejs环境开发vue。<br>
面试的项目要求精通vue + element ui ，头大，不想去了。element ui用vue开发的，但为了更好的打包还得cnpm安装一下，然后直接在vue模板项目里引入就能用，<a href="https://element.eleme.cn/#/zh-CN/component/installation" target="_blank">具体看官方文档</a>。<br>
element ui有很多主题和组件，这让我想起了bootstrap。人生苦短，先学到这里吧。<br>
