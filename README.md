# sshlogin
## 1. 生成秘钥对 
> `ssh-keygen -t rsa -f rsa_name` `rsa_name` 为生成的文件名字;  
## 2. 需要登录谁，就把公钥放到哪里去;  
> 2.1 如需要登录github，就把公钥放到github网站;  
> 2.2 如需要vscode登录服务器，就把公钥放到服务器的  
`.ssh/authorized_keys`中;  
> vscode配置格式  
```
Host 127.0.0.1
    HostName 127.0.0.1
    Port 22
    User jun
    IdentityFile "C:\Users\jun\.ssh\id_rsa"
```
## 3. ssh开启免密，秘钥登录  
> 3.1 `/etc/ssh/sshd_config`更改  
```
#公钥存储位置
AuthorizedKeysFile      .ssh/authorized_keys
#允许root账户登陆(慎用)
PermitRootLogin yes
#开启公匙认证
PubkeyAuthentication yes
#不容许密码登录
PasswordAuthentication no
StrictModes no
```
> 3.2 重启`service sshd restart`
> 3.3 排除问题  
```
ssh -v  root@192.168.123.229
ssh -vvv  root@192.168.123.229
```  
## 4. 设置目录权限 
```
chmod 0700 .ssh 
chmod 0600 .ssh/authorized_keys
```

## 5. 参考: `https://blog.csdn.net/buyueliuying/article/details/80898613`
