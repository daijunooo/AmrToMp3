# 微信H5开发 amr 录音转 mp3 

- 选用sox（http://sox.sourceforge.net/）
- sox是瑞士军刀的声音处理程序

1. 安装所有解码编码插件
```
tar -zxvf lame-3.100.tar.gz
cd lame-3.100
./configure
make
make install

tar -zxvf libmad-0.15.1b.tar.gz
cd libmad-0.15.1b
sed -i '/-fforce-mem/d' configure
./configure
make
make install

tar -zxvf libid3tag-0.15.1b.tar.gz
cd libid3tag-0.15.1b
./configure
make
make install

tar -jxvf amrnb-11.0.0.0.tar.bz2
cd amrnb-11.0.0.0
./configure
make
make install

tar -jxvf amrwb-11.0.0.0.tar.bz2
cd amrwb-11.0.0.0
./configure
make
make install
```

2. 安装sox
- 确保以上都安装好了才进行这一步

```
tar -zxvf sox-14.4.2.tar.gz
cd sox-14.4.2
./configure
```
> 确保 “lame….yes”, “mad….yes”, and “id3tag…yes”
```
make -s
make install
```

3. 用法
```
sox f.amr f.mp3
```
- 如果报错请检查程序依赖库是否正常
```
ldd /usr/local/bin/sox
```
- 如果不正常请查看依赖库中是否缺少文件，或者 /usr/local/bin 是否加入全局
