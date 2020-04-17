# Gaction安装教程 2020.04.15 by king
---
## 一、准备工作
1. 一台可上网的Android手机。
2. 一个github账号。 注册地址：<https://github.com/join>
3. 一个ESC账号。 注册地址：<https://passport.escience.cn/regist.jsp>
4. 一个邮箱账号(非必须)。 推荐: 163邮箱。这个邮箱是用来发送通知的。目前，163邮箱测试oK!
5. Termux APP。 下载地址：各大应用商店 或者 <https://termux.com/>

## 二、开始安装
1. 首先，登录你的github账号。然后，打开链接：<https://github.com/search>，输入关键词：`King-Test/Gaction`，搜索Gaction仓库。在搜索列表中找到Gaction仓库后，点击进入fork该仓库。操作步骤如图2-1、图2-2、图2-3所示。
<div  align="center">
 <img src="https://github.com/King-Test/Gaction/blob/master/screenshots/2-1.jpg" width="500" alt="图2-1" align="center" />
 <p align="center" >图2-1</p>
</div>

<div  align="center">
 <img src="https://github.com/King-Test/Gaction/blob/master/screenshots/2-2.jpg" width="500" alt="图2-2" align="center" />
 <p align="center" >图2-2</p>
</div>

<div  align="center">
 <img src="https://github.com/King-Test/Gaction/blob/master/screenshots/2-3.jpg" width="500" alt="图2-3" align="center" />
 <p align="center" >图2-3</p>
</div>

2. fork后，打开你自己的Gaction仓库主页，点击`settings -> Secrets -> Add a new secret`，添加秘钥字符串。请按图2-4、图2-5、图2-6中提示操作。
<div  align="center">
 <img src="https://github.com/King-Test/Gaction/blob/master/screenshots/2-4.jpg" width="500" alt="图2-4" align="center" />
 <p align="center" >图2-4</p>
</div>

<div  align="center">
 <img src="https://github.com/King-Test/Gaction/blob/master/screenshots/2-5.jpg" width="500" alt="图2-5" align="center" />
 <p align="center" >图2-5</p>
</div>

<div  align="center">
 <img src="https://github.com/King-Test/Gaction/blob/master/screenshots/2-6.jpg" width="500" alt="图2-6" align="center" />
 <p align="center" >图2-6</p>
</div>

3. 回到你的Gaction仓库主页，点击图2-7中所示的Actions菜单项，启用actions功能。
<div  align="center">
 <img src="https://github.com/King-Test/Gaction/blob/master/screenshots/2-7.jpg" width="500" alt="图2-7" align="center" />
 <p align="center" >图2-7</p>
</div>

4. 接下来，在你的Android手机上，安装“Termux APP”。

5. 打开Termux，等待Termux初试化完毕，然后执行如下Gaction安装命令。操作如图2-8、图2-9所示。
```
   apt update -y && apt install curl -y && bash <(curl -sSL https://github.com/[你的github账号名字]/Gaction/raw/master/setup)
```

<div  align="center">
 <img src="https://github.com/King-Test/Gaction/blob/master/screenshots/2-8.jpg" width="500" alt="图2-8" align="center" />
 <p align="center" >图2-8</p>
</div>

<div  align="center">
 <img src="https://github.com/King-Test/Gaction/blob/master/screenshots/2-9.jpg" width="500" alt="图2-9" align="center" />
 <p align="center" >图2-9</p>
</div>

6. 大功告成！！！

## 三、基本使用
1. 找到一个视频链接，比如：`http://file.gtv1.org/xxx/test.hls.m3u8`，打开Termux，在终端提示符下，输入如下命令：
```
  gac add http://file.gtv1.org/xxx/test.hls.m3u8
或者，
  gac add http://file.gtv1.org/xxx/test.hls.m3u8 test.mp4

```

```
  注意：这里的“test.mp4”，代表下载完成后视频的名称，你可以任意命名，但名称最好是英文和数字组合，并且“空格”请用“下划线”代替。 如果不加视频名字，gaction会自动命名。  
```

&nbsp;&nbsp;&nbsp;&nbsp;最后，按回车键就会开始离线下载。现在，你就可以关掉Termux干自己的事情了。 

2. Gaction会在视频离线完成后，自动发送邮件通知你。如果，你没有配置`MAIL_KEY`，gaction不会发送通知！不过，你可以访问自己Gaction仓库的actions页面，查看执行进度。或者，你也可以在Termux中，执行命令: `gac ls`，查看视频离线列表，以确认视频是否离线完毕。效果图3-1所示。  

<div  align="center">
 <img src="https://github.com/King-Test/Gaction/blob/master/screenshots/3-1.jpg" width="500" alt="图3-1" align="center" />
 <p align="center" >图3-1</p>
</div>

3. 视频离线完成后，你需要打开Termux，输入命令：`gac ls`，查看视频离线列表。从列表中找到，你要转存到本地的视频的“rid”。比如: rid值为：1234，执行相应命令: `gac dl 1234`，就可以转存视频到本地。效果图3-2所示。  

<div  align="center">
 <img src="https://github.com/King-Test/Gaction/blob/master/screenshots/3-2.jpg" width="500" alt="图3-2" align="center" />
 <p align="center" >图3-2</p>
</div>

4. 等待转存完毕，然后查看转存的视频。方法: 打开手机上的文件浏览器，找到Gaction转存路径，浏览视频文件。(默认转存路径：`/sdcard/Download/gaction`) 你可以在执行转存命令的时候指定路径。比如：
```
  ESC_LOCAL_PATH=/sdcard/new_path gac dl 1234
```

6. 由于ESC最多可以存储10G内容，你需要定期使用删除命令：`gac rr 1234`，删除不需要的离线视频，来腾出保存新视频的空间。

5. 其他gaction功能，请自行探索。

```
  补充：Gaction有一条比较方便的命令：gac adc wg，你可以使用它，在不需要提前准备任何视频链接下，就可以直接下载每天来自livestream的最新视频。 
```

## 四、问题反馈与帮助
1. 在<https://github.com/King-Test/Gaction>下提issue。  
2. 邮箱: <github_king_1025@163.com>  
3. QQ号: `1552392253`   

*请自行斟酌以上联系方式。*
