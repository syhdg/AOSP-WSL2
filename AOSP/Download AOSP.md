# <center> 获取AOSP源代码</center>

## 一、创建文件夹

**由于AOSP源代码比较大，有几十G，建议不要使用WSL的安装盘（C盘）作为下载和编译盘**

所以需要在另外的磁盘（最好剩余空间200G以上）

- 需要注意的是，需要修改本地文件夹的大小写敏感，否则lunch的时候直接错误，导致代码没法用

  1. 确定**Linux子系统功能**功能开启，否则无法执行

  2. 以**管理员身份**打开PowerShell或者命令提示符，输入命令

     ```
     fsutil file setCaseSensitiveInfo 文件夹路径 enable
     ```

  3. 新建两个不同的文件，名称除了大小写其他都相同，看是否能成功创建

     失败案例

​              

<img src="C:\Users\Administrator\Desktop\github\AOSP-WSL2\AOSP\res\file_error.png" style="zoom:100%;" />

​			成功案例

​			![](C:\Users\Administrator\Desktop\github\AOSP-WSL2\AOSP\res\file_normal.png)



## 二、下载源代码

### 2.1 说明

此处使用的是[清华大学AOSP镜像网站](https://mirrors.tuna.tsinghua.edu.cn/help/AOSP/)，如果需要，可以访问原网站进行学习

**由于 AOSP 镜像造成CPU/内存负载过重，我们限制了并发数量，因此建议：**

1. sync的时候并发数不宜太高，否则会出现 503 错误，即`-j`后面的数字不能太大，建议选择4。

2. 请尽量选择流量较小时错峰同步。

   

### 2.2 下载repo工具

1. 下载

   ```shell
   curl https://mirrors.tuna.tsinghua.edu.cn/git/git-repo -o repo
   chmod +x repo
   ```

   为了方便可以将其拷贝到你的`PATH`里。

2. 更新

​	repo的运行过程中会尝试访问官方的git源更新自己，如果想使用tuna的镜像源进行更新，可以将如下内容复制到你的`~/.bashrc`里

  ```
  export REPO_URL='https://mirrors.tuna.tsinghua.edu.cn/git/git-repo'
  ```

​	并**重启终端模拟器**。



###  2.3下载源码

1. 建立工作目录:

   ```shell
   mkdir WORKING_DIRECTORY
   cd WORKING_DIRECTORY
   ```

   

2. 初始化仓库:

```shell
repo init -u https://mirrors.tuna.tsinghua.edu.cn/git/AOSP/platform/manifest
```



3.如果需要某个特定的 Android 版本([列表](https://source.android.com/setup/start/build-numbers#source-code-tags-and-builds))：

最新的版本：android-12.0.0_r15

```shell
repo init -u https://mirrors.tuna.tsinghua.edu.cn/git/AOSP/platform/manifest -b android-12.0.0_r15
```



4.同步源码树（以后只需执行这条命令来同步）：

```shell
repo sync
```

