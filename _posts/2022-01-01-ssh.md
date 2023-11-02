


<a href="https://www.jianshu.com/p/dd053c18e5ee" target="_blank">ssh-keygen - 简书</a>        


# 启用ssh    
```  
sudo apt install -y sudo vim git openssh-server  
sudo service ssh restart  
可以重启试一下, 看有没有自动启动ssh  

```  

## 开机自动启动ssh命令
<a href="https://blog.csdn.net/fandroid/article/details/86799932" target="_blank">Ubuntu18.04 ssh 开机自动启动的设置方法_酷炫科技-CSDN博客_ubuntu 开机启动ssh</a>  |  <br>  

```
# 开机自动启动ssh命令
sudo systemctl enable ssh
或
sudo service ssh restart  


# 关闭ssh开机自动启动命令
sudo systemctl disable ssh

# 设置好后重启系统(我觉得可以不重启)
reboot

#查看ssh是否启动，看到Active: active (running)即表示成功
sudo systemctl status ssh
```
```
# 单次开启ssh
sudo systemctl start ssh

# 单次关闭ssh
sudo systemctl stop ssh
```

```
systemctl enable ssh
service ssh restart  
```



# 登录  
```
ssh 192.168.1.2
ssh ubuntu@192.168.1.2
ssh -p 10000 ubuntu@192.168.1.2
```

# 清除指纹
如果之前登录了这个ip地址, 但是这个ip地址对应的服务器重装了系统, 需要先清除指纹, 重新登录.
```
ssh-keygen -R 192.168.1.2
```


# 关于免密登录

## 生成公钥私钥      
```      
ssh-keygen      
```      
生成公钥私钥(`id_rsa.pub`, `id_rsa`)      

## 将id_rsa.pub 传输到服务器      
xftp    
scp    

## 服务器端接收公钥    
在服务器将其内容追加到 `~/.ssh/authorized_keys` 后面。      
```      
cat id_rsa.pub >> ~/.ssh/authorized_keys      
```      

## vscode 免密登录      
将之前在 `~/.ssh` 生成的公钥私钥 复制到 `C:\Users\xxx\.ssh` 即可实现 vscode 免密登录服务器      
(这里的`C:\Users\xxx\.ssh` 就相当于 ubuntu 中的 `~/.ssh`)      

