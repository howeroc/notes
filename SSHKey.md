### 生成与使用SSH Key

- 使用以下命令生成公钥和私钥

```bash
$ ssh-keygen -t rsa -C "xxx@gmail.com"
```
- 使用SSH Key

```bash
$ scp ~/.ssh/id_rsa.pub user@remote.host:pubkey.txt # 将本地公钥复制到远程机器上的pubkey.txt文件中
$ ssh user@remote.host # 登入远程服务器
$ mkdir ~/.ssh # 创建存储key的文件夹
$ chmod 700 .ssh # 改变.ssh文件夹权限
$ cat pubkey.txt >> ~/.ssh/authorized_keys # 将公钥复制到已授权文件中
$ chmod 600 ~/.ssh/* # 将authorized_keys权限修改成可读写不可执行
$ 
$ ssh-copy-id -i id-rsa.pub user@remote.host # 也可用此指令直接执行
```
