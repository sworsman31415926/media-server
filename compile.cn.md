# 一、下载代码

```markdown
#主仓库
git clone https://github.com/ireader/media-server.git
#依赖仓库
git clone https://github.com/ireader/sdk.git
git clone https://github.com/ireader/avcodec.git
git clone https://github.com/ireader/3rd.git
```

请将上述仓库放在同一级目录下。为了行文方便，假设都放在src目录下。

# 二、**编译和运行**

## linux系统

推荐gcc 版本 >= 4.8

1、先分别在sdk目录和avcodec目录执行make,编译media-server的依赖库

```markdown
cd src/sdk 
make clean && make
cd src/avcodec
///////////////////////////////////////////////////////
20230203 编译的时候编译存在错误的， 存在头文件的，
这个地方编译存在错误的时候，不用关心的，编译rtsp-server-test.cpp
自己加上头文件就可以的
//////////////////////////////////////////////////////////////
make clean && make

```

2、在media-server目录下执行make

```markdown
cd src/media-server
make clean && make
```

3、运行，在media-server的test目录下集合了各种不同的使用demo

```markdown
cd src/media-server/test
make clean && make

20230203 fix the build file start
我自己在编译的时候不使用这样的方法进行编译，自己写cmakelists.txt 编译
rtsp-server-test.cpp 就ok的(写的编译文件都在这个博客中)
https://blog.csdn.net/hfut31415926/article/details/128875772?csdn_share_tail=%7B%22type%22%3A%22blog%22%2C%22rType%22%3A%22article%22%2C%22rId%22%3A%22128875772%22%2C%22source%22%3A%22hfut31415926%22%7D
20230203 fix the build file end

#func name 为你想要测试的列子，具体的请查看test.cpp支持的测试用例或者直接./debug.linux/test查看输出支持的函数
./debug.linux/test -c <func name>
#rtsp server
eg: ./debug.linux/test -c rtsp_example
```

执行可能会报错 “error while loading shared libraries: [libaio.so](http://libaio.so/): cannot open shared object file: No such file or directory”

请执行 “export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:../../sdk/libaio/debug.linux”

4、make选项

1. make RELEASE=1 (make release library, default debug)
2. make PLATFORM=arm-hisiv100nptl-linux (cross compile)

## win系统

推荐visual stuido版本 >= 2015

直接打开media-server文件夹下的media-server.sln即可

## mac系统

直接打开media-server文件夹下的media-server.xcworkspace即可。


# 致谢：
文档作者：[Dw](https://github.com/Dw9)
20230203 在自己工作中测试h264 和 h265 都可以播放的
