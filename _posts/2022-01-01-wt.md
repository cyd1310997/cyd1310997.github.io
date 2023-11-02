




# 安装  

应用商店搜索  
Windows Terminal  

# 配置  

下拉菜单 -> settings  -> startup  -> default profile  -> ubuntu-20.04 -> 保存  
下拉菜单 -> settings  -> interaction  -> automatically copy selection to clipboard  -> on -> 保存  
下拉菜单 -> settings  -> open JSON file  


# 配置文件  

```  

XXX() {  
    ssh -p 10000 username@192.168.1.2  
}  

    "profiles":   
    {  
        "defaults":   
        {  
            "startingDirectory": "."  
        },  
    }  


```  

# 使用方法  

选择即复制  
粘贴: Ctrl v  
多行粘贴会警告, 回车可继续执行  


# 卸载  

开始菜单右键卸载  


