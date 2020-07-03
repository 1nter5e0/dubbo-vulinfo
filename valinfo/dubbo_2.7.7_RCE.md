# Dubbo 2.7.7 Remote Code Execute

## 版本号: 2.7.7

## poc使用JNDI的利用方式远程执行代码

## 漏洞描述:

我们发现当Dubbo配置不当的时候存在全版本的远程代码执行漏洞，

## 漏洞触发
```log4j.rootLogger=debug, stdout ``` 
当dubbo开启debug的日志配置，将造成全版本的远程代码执行漏洞。

## 漏洞证明详细：
新建ldap服务，将请求重定向到http服务的恶意类。当造成代码执行的时候会加载ldap请求，具体实现如poc.py文件

