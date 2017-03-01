iTerm ssh 保存



记住用户名与IP地址：man ssh_config


###### 记住用户名和IP地址

如果需要记住用户名和密码的话，需要在~/.ssh/目录下 新建一个config文件，如果有的话就追加内容，配置内容格式示例如下：

> 

Host dev-hadoop-44

Hostname 172.16.2.44

Port 52119

User root

IdentityFile ~/.ssh/id_rsa

> 

Host dev-hadoop-45

Hostname 172.16.2.45

Port 52119

User root

IdentityFile ~/.ssh/id_rsa

> 

Host dev-hadoop-46

Hostname 172.16.2.46

Port 52119

User root

IdentityFile ~/.ssh/id_rsa



其中Host的内容表示你可以执行 

> ssh dev-hadoop-45



##### IdentityFile是免密登陆的内容

免密配置方法：

> 首先把你本机的公钥id_rsa.pub拷贝到目标主机（注意不要把别人的文件覆盖了，最好重命名）

>> scp -P 52119 id_rsa.pub root@dev-hadoop-46:.ssh/id_rsa.pub.yuyong

> 然后追加你的公钥到authorized_keys,注意是追加

>> cat id_rsa.pub.yuyong >> authorized_keys



 
