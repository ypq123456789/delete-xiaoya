# 脚本作用
可以自动删除小雅转存文件夹内的内容，结合定时计划任务定时清除。

本文代码来自：https://www.bilibili.com/read/cv28501448/#reply204926778608

感谢“就爱买破烂”大佬。

结合GPT修改代码语法错误，可以使用。本人对代码一窍不通，主打一个实用主义，分享给大家。

# 适用平台
·VPS（最好用Ubuntu x86_64，其他没测试过，可能会报错）

·路由器（openwrt经测试可以用）

·NAS（未测试过）

# 前置条件
安装python(最好为3.7.9，其他版本没测试过，可能会报错)

平台要支持定时计划任务（VPS可以用宝塔面板，路由器和NAS一般有自己的定时计划系统）

具体怎么安装自行搜寻，不赘述。

# 测试脚本是否生效

下载文件里面的delete.py，然后放到自己VPS的根目录。

根据代码注释，修改自己的alist域名、账号、密码、alist挂载阿里云盘小雅缓存文件夹的路径，别的不用改。
<img width="337" alt="a9e01c620287c9737140efa7398da048" src="https://github.com/ypq123456789/delete-xiaoya/assets/114487221/b0f1bc4d-e5ee-4722-9444-97f9f96d5fd6">
<img width="401" alt="c6d3bcb52a1d4b9f308c7787f04a88c6" src="https://github.com/ypq123456789/delete-xiaoya/assets/114487221/f844dacf-6b52-410e-9a31-abbd508ff872">
<img width="343" alt="ad559fec6dbc50be09238802eac6a0b8" src="https://github.com/ypq123456789/delete-xiaoya/assets/114487221/b1fc1070-9b19-4a35-a742-c76f5b463a7f">

打开终端，输入：

cd /

python3 delete.py

如果没有任何反应，打开阿里云盘的小雅转存文件夹，看到内部文件被删除，说明脚本生效了。

如果报错，说明可能python版本和平台有问题，建议使用VPS和python3.79再试试。

如果切换后还是不能使用，建议将自己使用的平台、python版本、报错的内容和脚本内容输入GPT，请它帮你修改合适的脚本，应该能解决问题。

# 设置定时计划任务
以安装宝塔面板的VPS平台为例：

打开宝塔面板，选择计划任务，输入：

cd /

python3 delete.py

执行周期为一分钟。

<img width="742" alt="1706272841154" src="https://github.com/ypq123456789/-/assets/114487221/8dc3e304-6cb8-43da-bcdc-c0fd9e610c4f">

然后就可以愉快地清理备份盘的小雅分享缓存啦！该文件夹内的内容每分钟自动清理，即使并非是小雅保存的文件，你自己上传、新建的文件也是每分钟自动清理，如果你有这个需求也可以满足。

<img width="556" alt="8adda8d10dba5dd4e7ff9d87b98200f7" src="https://github.com/ypq123456789/delete-xiaoya/assets/114487221/56baca26-57c6-46bb-98e9-cedae263d51d">
