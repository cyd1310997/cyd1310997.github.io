

```
禁用 开源显卡驱动 nouveau  
安装 nvidia 驱动  
cuda 和 cudnn 不需要安装, 因为docker容器自带cuda和cudnn  
```

# 查显卡型号

```

lspci | grep -i nvidia
```

<a href="https://devicehunt.com/view/type/pci/vendor/10DE/device/20F1" target="_blank">PCI\VEN_10DE&DEV_20F1 - GA100 [A100 PCIe 40GB] | Device Hunt</a>  |  <br>  



# 安装显卡驱动
<a href="https://www.jianshu.com/p/158ae8fcdb4a" target="_blank">Ubuntu安装cuda和cudnn及测试方法 - 简书</a>  |  <br>  


终端下输入命令 ` lsmod | grep nouveau ` 查看是否被禁用
```
lsmod | grep nouveau 
```
没有信息输出说明禁用成功



1）打开终端输入以下命令删除旧驱动
```
sudo apt-get purge nvidia*
```

2）禁用自带的 nouveau nvidia驱动
首先利用命令行打开
```
sudo vim /etc/modprobe.d/blacklist.conf
```

在文件末端加入
```
blacklist nouveau
options nouveau modeset=0
```

然后更新
```
sudo update-initramfs -u
```
会显示 ` Possible missing firmware /lib/firmware/ast_dp501_fw.bin for module ast `  
it's annoying, but harmless.   
<a href="https://serverfault.com/questions/755194/ubuntu-15-10-server-w-possible-missing-firmware-lib-firmware-ast-dp501-fw-bin" target="_blank">Ubuntu 15.10 Server; W: Possible missing firmware /lib/firmware/ast_dp501_fw.bin for module ast - Server Fault</a>  |  <br>  



最后重启
```
sudo reboot
```


终端下输入命令 `lsmod | grep nouveau` 查看是否被禁用
```
lsmod | grep nouveau
```
没有信息输出说明禁用成功  


3）下载好对应gpu版本.run 形式的显卡驱动  
<a href="https://www.nvidia.com/Download/index.aspx?lang=cn" target="_blank">NVIDIA 驱动程序下载</a>  |  <br>    

![选择的 nvidia 驱动型号](https://telegra.ph/file/245174dd2a8c3612f468d.png)  


4）安装驱动

给驱动run文件赋予执行权限：
```
sudo chmod a+x NVIDIA-Linux-x86_64-470.82.01.run
```

然后开始安装
```
sudo ./NVIDIA-Linux-x86_64-470.82.01.run
```

```
Verifying archive integrity... OK
Uncompressing NVIDIA Accelerated Graphics Driver for Linux-x86_64 470.82.01 ...
```

5）挂载显卡驱动
```
modprobe nvidia
```

6）检查是否安装成功
```
nvidia-smi
nvidia-smi -q | grep -i vbios
nvidia-smi -q | less
```

