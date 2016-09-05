# code_review_tools_1_Codebrag

最近几天尝试安装几个review工具 [参考](http://note.youdao.com/)， 尝试了Crucible（结合JIRA使用），RhodeCode，Barkeep这三个都失败了。Codebrag成功了，尝试了使用，记录下过程。

本文前半部分为InstallGuide的实践缩略版。后半分为Codebrag实际使用。


### 1准备  
- [官网](http://codebrag.com/)  http://codebrag.com/

- [Install Guide](http://codebrag.com/)  //可以看着Guide进行安装

- Ubuntu //宿主操作系统

- Java7 //codebrag运行环境  

```
$sudo add-apt-repository ppa:webupd8team/java  
$sudo apt-get update && sudo apt-getinstall oracle-java7-installer
```


- git  //同步git repository    

```
$sudo apt-get install git
```


- git-svn //同步svn repository  
```
$sudo apt-get install git-svn
```

### 2下载Codebrag

```
$wget http://codebrag.com/latest/codebrag.zip  
$unzip codebrag.zip
```
可以通过win的下载工具下载，然后copy到ubuntu。

### 3 Clone Repository

```
$cd codebrag-2.3/repos
$git clone git://yourcompany.com/path/to/project-abc.git
```

```
$cd codebrag-2.3/repos
$git svn clone http://yourcompany.com/path/to/svn/project-abc project-abc     # Use 'git svn clone', not 'svn checkout'
```
代码库的代码需要下载到 repos， 启动codebrag之前必须要有个Repository。

### 4 编辑 'codebrag.conf'

```
//设置Repository登录名和密码
repository {
    username = "johndoe"
    password = "password"
}

//If you authenticate using a key secured with a passphrase, you need to provide it in the configuration. Leave empty if you have got no passphrase configured.
repository {
    passphrase = "secret_passphrase"
}

//Sending anonymous statistics

//Optional settings - config email server, other setting

```

### 5 Running Codebrag

```
$./codebrag.sh start         # Unix/OS X

//Logs will be written to logs/codebrag.log. Codebrag will be available at http://yourserver:8080.
//To display Codebrag logs execute:
$tail -n 1000 -f logs/codebrag.log

//To stop Codebrag execute:
$./codebrag.sh stop
```

以上浏览器输入 ： localhost：8080 就能够访问Codebarg了。



---



### 6 实际使用
登录
![A](https://github.com/iAmeng/code_review_tools_1_Codebrag/blob/master/images/codebrag_a.png?raw=true)

Repository，Branch， ToReview
![image](https://github.com/iAmeng/code_review_tools_1_Codebrag/blob/master/images/codebrag_b.png?raw=true)

Reviewing
![image](https://github.com/iAmeng/code_review_tools_1_Codebrag/blob/master/images/codebrag_c.png?raw=true)

Comment
![image](https://github.com/iAmeng/code_review_tools_1_Codebrag/blob/master/images/codebrag_d.png?raw=true)

### 7 Ubuntu 局域网访问
实际使用的时候只在Localhost是不太方便的，希望局域网成员也能加入进来。
现在补充一些Ubuntu局域网访问的内容  
1 Windows + VMware + Ubuntu  
2 VMware 网络模式 - Bridge  
3 关闭防火墙  
4 设置ip，mask，dns  
5 设置dns file  

WM网络，桥接模式  
![image](https://github.com/iAmeng/code_review_tools_1_Codebrag/blob/master/images/vm_a.png?raw=true)

设置IP，mask，dns
![image](https://github.com/iAmeng/code_review_tools_1_Codebrag/blob/master/images/vm_b.png?raw=true)
![image](https://github.com/iAmeng/code_review_tools_1_Codebrag/blob/master/images/vm_c.png?raw=true)
![image](https://github.com/iAmeng/code_review_tools_1_Codebrag/blob/master/images/vm_d.png?raw=true)

设置DSN file
![image](https://github.com/iAmeng/code_review_tools_1_Codebrag/blob/master/images/vm_e.png?raw=true)
![image](https://github.com/iAmeng/code_review_tools_1_Codebrag/blob/master/images/vm_f.png?raw=true)

!!! Enjoy:)
