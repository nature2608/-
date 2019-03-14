mentohustV4的编译步骤
主要步骤分成编译环境的配置，libpcap的交叉编译，mentohust的交叉编译，mentohust的使用。

a. 编译环境的配置。这些命令为计算机指定接下来的工作要用到的编译器类型。
打开终端(ctrl+alt+T),输入以下命令(需联网)：

sudo -i (这里要输入密码)
apt-get install build-essential bison flex zlib1g-dev libncurses5-dev subversion quilt intltool ruby fastjar unzip gawk autogen autopoint
export PATH=$PATH:/home/xxx/Openwrt-SDK-rampips-mt7620/staging_dir/toolchain-mipsel_24kec+dsp_gcc-4.8-linaro_uClibc-0.9.33.2/bin
export CC=mipsel-openwrt-linux-gcc  
export CPP=mipsel-openwrt-linux-cpp  
export GCC=mipsel-openwrt-linux-gcc  
export CXX=mipsel-openwrt-linux-g++  
export RANLIB=mipsel-openwrt-linux-uclibc-ranlib  
export ac_cv_linux_vers=2.6.24  
export LDFLAGS="-static"  
export CFLAGS="-Os -s"  
export STAGING_DIR=/home/xxx/Openwrt-SDK-rampips-mt7620/staging_dir/toolchain-mipsel_24kec+dsp_gcc-4.8-linaro_uClibc-0.9.33.2/
b. libpcap的交叉编译：  

cd /home/xxx/libpcap-1.7.4  
./configure --host=mipsel-linux --with-pcap=linux 
make  
c. Mentohust的编译：  

cd /home/xxx/mentohust-master/  
sh autogen.sh 
./configure --host=mipsel-linux   --disable-encodepass --disable-notify --with-pcap=/home/xxx/libpcap-1.7.4/libpcap.a 
make  
此时交叉编译已完成，mentohust在/home/xxx/mentohust-master/src文件夹中。将电脑和路由用网线连上，把mentohust传到路由上
