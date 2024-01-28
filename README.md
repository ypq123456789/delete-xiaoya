# 脚本作用

**可以自动删除小雅转存文件夹内的内容，结合定时计划任务定时清除。**

本文代码来自：https://www.bilibili.com/read/cv28501448/#reply204926778608

感谢“就爱买破烂”大佬。

结合GPT修改代码语法错误，可以使用。

大概原理是调用alist的api，直接删除阿里云盘指定文件夹内的内容，**不会进入回收站**，避免繁琐操作。

再强调一遍：**你脚本设置的阿里云盘指定文件夹内的内容，被删除后不会进入回收站，没了就是没了，无法恢复！**

**正因如此，在设置删除路径时请务必小心，如果设置错误，会导致你的阿里云盘的文件被删除，本脚本概不负责！**

与xiaoyakeeper的区别：

1.**xiaoyakeeper只会自动删除容器生效以后小雅转存的文件，无法自动删除容器生效之前的缓存文件、自行添加的文件；而本脚本中，该文件夹内的内容定时（可自行设置周期）自动清理，脚本生效之前的缓存文件、自行添加的文件也是定时自动清理，如果你有这个需求也可以满足。**

2.**xiaoyakeeper只能设置立即删除或者每天定点删除，缺少中间的过渡选项；而本脚本可以自行选择执行的周期，例如你可能觉得1分钟删除一次比较危险，那你可以设置5分钟或者半小时删除一次，既做到快速清理不占用空间，又实现相对保险安全。**

本人对代码一窍不通，主打一个实用主义，分享给大家。

# 适用平台
·VPS（最好用Ubuntu x86_64，其他没测试过，可能会报错）

·路由器（openwrt经测试可以用）

·NAS（未测试过，“就爱买破烂”大佬提示：**如果使用群晖NAS的定时执行，python需要提前下载好requests库**）

# 前置条件
·**平台安装了alist且能够联通外网（因为要调用alist的api），且alist挂载了阿里云盘open（备份盘、资源盘均可），阿里云盘open内专门建了一个小雅缓存文件夹**

·**安装python（最好为3.79，其他版本没测试过，可能会报错）**

·**平台要支持定时计划任务（VPS可以用宝塔面板，路由器和NAS一般有自己的定时计划系统）**

具体怎么安装自行搜寻，不赘述。

# 测试脚本是否生效

下载文件里面的delete.py，**然后放到自己VPS的根目录**。

根据代码注释，修改自己的**alist地址（ip+端口）、账号、密码、alist挂载阿里云盘小雅缓存文件夹的路径**，别的不用改。

<img width="337" alt="a9e01c620287c9737140efa7398da048" src="https://github.com/ypq123456789/delete-xiaoya/assets/114487221/b0f1bc4d-e5ee-4722-9444-97f9f96d5fd6">

<img width="401" alt="c6d3bcb52a1d4b9f308c7787f04a88c6" src="https://github.com/ypq123456789/delete-xiaoya/assets/114487221/f844dacf-6b52-410e-9a31-abbd508ff872">

<img width="315" alt="daf21197b516d1068f585fd16b983382" src="https://github.com/ypq123456789/delete-xiaoya/assets/114487221/1c903244-3529-4a06-a54b-d52b157bd9ce">


打开终端，输入：

cd /

python3 delete.py

如果没有任何反应，打开阿里云盘的小雅转存文件夹，看到内部文件被删除，说明脚本生效了。

**如果报错，说明可能python版本和平台有问题，建议使用VPS和python3.79再试试。**

**如果切换后还是不能使用，建议将自己使用的平台、python版本、报错的内容和脚本内容输入GPT，请它帮你修改合适的脚本，应该能解决问题。**

# 设置定时计划任务
以安装宝塔面板的VPS平台为例，**其他平台自行寻找设置方法**：

打开宝塔面板，选择计划任务，输入：

cd /

python3 delete.py

**执行周期设置为5分钟（不建议低于5分钟，很可能清理太快导致播放出问题）**。你也可以根据自己的需要自行调整，例如一小时一次，一天一次。

<img width="748" alt="1706333813200" src="https://github.com/ypq123456789/delete-xiaoya/assets/114487221/9912d0df-dec0-4308-a233-e66bbaae18b9">

然后就可以愉快地清理备份盘的小雅分享缓存啦！

<img width="556" alt="8adda8d10dba5dd4e7ff9d87b98200f7" src="https://github.com/ypq123456789/delete-xiaoya/assets/114487221/56baca26-57c6-46bb-98e9-cedae263d51d">
