## FFMpeg在Linux下编译
### 1、For Linux 

    编译环境：
- ndk版本：android-ndk-r2b
- ffmpeg版本：ffmpeg-4.2.4
- linux版本 centos7
    
    命令行

1.  shell


```shell
./configure --target-os=linux --prefix=$(pwd)/android/arm --disable-doc --enable-shared --disable-static --disable-symver --enable-gpl
```
2.  make
```shell
make -j8
```
3.  make install
```shell
make install
```