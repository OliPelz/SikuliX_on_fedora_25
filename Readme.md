# Notes on Installing SikuliX on fedora 25
```
dnf groupinstall -y "Development Tools" 
dnf install -y cmake gcc git pkgconfig ffjpeg g++ gtk+-devel libjpeg-devel libtiff-devel jasper-devel libpng-devel zlib-devel libicu-devel unzip numpy python-devel autoconf automake libtool pango pango-devel cairo cairo-devel
```
# now compile and install opencv2 because the opencv3 which comes with fedora 25 does not work with SikuliX
```
mkdir ~/opencv-2.4.13; cd $_
wget http://downloads.sourceforge.net/project/opencvlibrary/opencv-unix/2.4.13/opencv-2.4.13.zip
unzip opencv-2.4.13.zip
cd opencv-2.4.13
mkdir release
cd release
cmake -D CMAKE_BUILD_TYPE=RELEASE -D CMAKE_INSTALL_PREFIX=/usr/local -D BUILD_PYTHON_SUPPORT=ON ..
make 
make install
```
# update ldconfig path with new opencv2
```
touch /etc/ld.so.conf.d/opencv.conf
echo /usr/local/lib >> /etc/ld.so.conf.d/opencv.conf
ldconfig
```
```
dnf install -y tesseract xdotool wmctrl redhat-lsb
```
# now install SikuliX 1.1.0
```
mkdir ~/SikuliX; cd $_
wget https://launchpad.net/sikuli/sikulix/1.1.0/+download/sikulixsetup-1.1.0.jar
java -jar sikulixsetup-1.1.0.jar
```
click 1.)

wait, done!


start with 
```
java -jar sikulix.jar
```
