### 一、造成的原因（图片不显示）

1. Markdown文件上传到Github，或者把含有图片的md文件传给其他人。
2. Typora写的md文件中的图片都是另外存储的，不像word软件是存放到word文件里的。

比如：我在文件里面放了下面一张图片（雷神），但把md文件发给朋友的时候，图片就不能显示了。。。。。

![雷神4](https://raw.githubusercontent.com/Caiguangnan/ProgrammerToolBox/master/img/20200314211822.jpg)

解决办法：

- 方法1：转成Word格式或者PDF格式之类的
- 方法2：把图片和md文件一起打包，再进行分享
- 方法3：全部图片上传到Github服务器上，直接发md文件，但朋友需要联网打开，才能看到图片。
  说明：Github服务器，是免费的，但对于新手来说，刚开始使用会觉得很痛苦！



### 二、解决方案

#### 2.1 方案一：存储到本地（不适合小编写文章）

设置如下，每次传md文件给其他人的时候，需要把图片文件夹也一并压缩转发才行，记住勾选“优先使用相对路径”

![image-20200314145657430](https://raw.githubusercontent.com/Caiguangnan/ProgrammerToolBox/master/img/20200314211823.png)

#### 2.2  方案二：搭建图床并自动上传（适合小编写文章）

​	所谓图床工具，就是自动把本地图片转换成链接的一款工具，网络上有很多图床工具，就目前使用种类而言，PicGo 算得上一款比较优秀的图床工具。它是一款用 `Electron-vue` 开发的软件，可以支持微博，七牛云，腾讯云COS，又拍云，GitHub，阿里云OSS，SM.MS，imgur 等8种常用图床，功能强大，简单易用。

​	Typora要更新到最新版本，PicGo也要最新版【只有最近几个版本，才支持自动上传】



步骤一：创建GitHub账号和仓库

创建账号：https://blog.csdn.net/qq_43571415/article/details/100050781

创建仓库（很详细，记得另外保存好token值）：https://blog.csdn.net/acmman/article/details/77621253

说明：

1. 创建的仓库可以是自己写的Github文章的仓库
2. 第一次创建仓库步骤很繁琐，以后就不会了。也劝大家不要自己去找教程，这类的资料很杂，很多都不全，这样对于小白更加痛苦！



步骤二：下载安装Picgo【2.2.0以上的版本】

Picgo 2.2.2版本，下载链接：https://www.lanzous.com/ia49ojg

Picgo设置步骤（很坑，所以步骤我自己写吧）：

①右击，打开详细窗口

![image-20200314163338770](https://raw.githubusercontent.com/Caiguangnan/ProgrammerToolBox/master/img/20200314211825.png)

②设置图床

![image-20200314163540095](https://raw.githubusercontent.com/Caiguangnan/ProgrammerToolBox/master/img/20200314211826.png)

**配置以下内容**：

- 设定仓库名：用户名/仓库名

- 设定分支名：这里写入分支名称，一般直接用`maser`即可。

- 设定Token（任意一个令牌都可以）：在 GitHub 上生成一个 *token* 以便 PicGo 来操作我们的仓库，来到个人中心，选择 *Developer settings* 就能看到 *Personal access tokens*，我们在这里创建需要的 *token*
  ![image-20200314164021892](https://raw.githubusercontent.com/Caiguangnan/ProgrammerToolBox/master/img/20200314211827.png)

  点击 Generate new token 创建一个新 token，选择 repo，同时它会把包含其中的都会勾选上，我们勾选这些就可以了。然后拉到最下方点击绿色按钮，Generate token 即可。之后就会生成一个 *token* ，记得复制保存到其他地方，这个 *token* 只显示一次！！

  ![image-20200314164103683](https://raw.githubusercontent.com/Caiguangnan/ProgrammerToolBox/master/img/20200314211828.png)



- 指定存储路径：一般写`/img`，会在设定的仓库中创建img文件夹，也可以取另外的名字。
- 设定自定义域名（很坑）：格式（https://raw.githubusercontent.com/Github用户名/仓库名/分支名）
  raw.githubusercontent.com：固定的，不要修改
  Github用户名：自己创建的Github登录用户名，不是昵称哦！
  仓库名：上面创建的仓库名（尽量不要有中文符，或者特殊符号）
  分支名：如果前面设定的分支名是master，这里也写master。

③手动上传测试（先确保能上传，再配置Typora）

有时候可能会上传不上，重启PicGo就可以了

![image-20200314165533961](https://raw.githubusercontent.com/Caiguangnan/ProgrammerToolBox/master/img/20200314211829.png)

上传成功！

![image-20200314165628466](https://raw.githubusercontent.com/Caiguangnan/ProgrammerToolBox/master/img/20200314211830.png)

如果上传不成功？

- 仓库名有特殊符号？上传文件有特殊符号？或者有空格之类的？
  建议全部改成英文。【GitHub中空格是用下划线来表示，_】
- token值不对？
  解决：重新复制粘贴一下，或者重新创一个新的token。
- 自定义域名是否正确？
  解决：按照上面的步骤，仔细观察书写格式。



④**Typora自动上传设置：**

![image-20200314213643797](https://raw.githubusercontent.com/Caiguangnan/ProgrammerToolBox/master/img/20200314220033.png)

单击“验证图片上传选项”

可以由下图获得PicGo需要设置的信息（记住，待会要用）：

- 需要监听的地址：127.0.0.1

- 需要监听的端口：36677

![image-20200314214234363](https://raw.githubusercontent.com/Caiguangnan/ProgrammerToolBox/master/img/20200314220026.png)



⑤**PicGo设置Server**

![image-20200314214017367](https://raw.githubusercontent.com/Caiguangnan/ProgrammerToolBox/master/img/20200314220019.png)

![image-20200314214547568](https://raw.githubusercontent.com/Caiguangnan/ProgrammerToolBox/master/img/20200314220019.png)



⑥**上传所有本地文件（单文件）**：它会把文件中用到的图片重新上传一次，路径也改变一次。

![image-20200314212235528](https://raw.githubusercontent.com/Caiguangnan/ProgrammerToolBox/master/img/20200314212238.png)

### 三、常遇到的问题

#### 3.1 如果上传不成功？

- PicGo可能自己改了Server端口号？
  解决：把它改过来，这个可能是个bug（毕竟是最新版，问题肯定会有的）
- PicGo报错了？
  解决：关掉PicGo，重新启动

![image-20200314231901464](https://raw.githubusercontent.com/Caiguangnan/ProgrammerToolBox/master/img/20200314231903.png)

#### 3.2 如何想要转移图集？重新转移动新的GitHub仓库？

解决：

1. 下载GitHub之前仓库的图集，复制到新的仓库中。
2. 打开md文件，按ctrl+F，替换全部路径的仓库名。





