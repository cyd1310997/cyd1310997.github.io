

<a href="https://zhuanlan.zhihu.com/p/105652962" target="_blank">WSL（Windows Subsystem for Linux) 安装教程 - 知乎</a>  |  <br>    

# wsl 命令 (powershell)  

```
wsl -l -v
```

# wsl1    

1.以管理员身份运行powershell ，输入下面的代码，等待提示完成后，重启系统：    
```  
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux    
```  

2.在微软应用商城搜索LINUX或WSL。    

# wsl2    

启用“虚拟机平台”可选组件    
以 管理员身份 打开 PowerShell 并运行：   
``` 
Enable-WindowsOptionalFeature -Online -FeatureName VirtualMachinePlatform    
``` 
需要 重新启动计算机，这些更改才能更好地生效    


