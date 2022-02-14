# <center>Andorid Source Code For Android Studio</center>

## 一、说明

​		使用环境：源代码位置，采用了WSL下载的文件源，详见DownloadAOSP.md文件

​						   Android Studio 4.0+

​		

## 二、导入方式

### 2.1 初始化环境变量

```shell
"source build/envsetup.sh" (source可以用 . 代替，即". build/envsetup.sh")
```



### 2.2 加载编译的项目

```shell
lunch 1
```



### 2.3 编译idegen.jar文件

```shell
"make idegen -j4" (这里的 -j4 表示用4线程来编译，可以不加)
```



### 2.4 生成文件

```shell
"sudo development/tools/idegen/idegen.sh" (我的电脑需要管理员权限才能执行成功，所以我一般会在前面加上"sudo")
```

注意：

WSL2  ubuntu20.04版本不能加sudo,斗则会出现bug 



![error1](.\issue\error1.png)



### 2.5 导入说明

1、执行上述动作后会生成三个文件

     1. android.iml (记录项目所包含的module、依赖关系、SDK版本等等，类似一个XML文件)
    
        2. android.ipr (工程的具体配置，代码以及依赖的lib等信息，类似于Visual Studio的sln文件)
    
        3. android.iws (主要包含一些个人的配置信息，也有可能在执行上述操作后没有生成，这个没关系，在打开过一次项目之后就会自动生成了)

![AS code1](.\issue\AS code1.png)



2、修改这两个文件的权限

```
chmod 777 android.iml
chmod 777 android.ipr
```



3、打开Android Studio，导入android.ipr即可
