# gnuradio_on_raspberry_pi_3
This repository will have all my instelation files for setting up Gnuradio on Raspberry Pi 3
# Project Status
This project has just started and is not compleet yet.
# Installation procedure.
Setting up Gnuradio with rtl_sdr and hackrf on my Raspberry Pi 3


We first need to increase the virtual memory of the Raspberry for Gnuradio to compile.

increase the virtual disk to 1024mb

 

Edit the following file

sudo vi / etc / dphys-swapfile

 

Change the content to   

CONF_SWAPSIZE = 1024 


restart the service:
sudo /etc/init.d/dphys-swapfile stop
sudo /etc/init.d/dphys-swapfile start

 

We now need to install the depending libraries.

sudo apt-get install python-cheetah libboost-all-dev python-lxml \ python-wxgtk2.8 python-numpy python-lxml libfftw3-dev libsdl1.2-dev \ python-scipy python-matplotlib python-tk octave liboctave-dev \ libgsl0-dev python-sphinx libcppunit-dev libuhd-dev swig \ python-qt4-dev libqwt-dev git 

 
We now need to prepare the Gnuradio directory
cd

 git clone --recursive <a href="http://git.gnuradio.org/git/gnuradio.git" rel="nofollow"> http://git.gnuradio.org/git/gnuradio.git</a >
 cd gnuradio 

mkdir gr-build
 cd gr-build
 cmake -Dhave_mfpu_neon = 0 -DCMAKE_CXX_FLAGS: STRING = "- march = armv6 \
 -mfpu = vfp -mfloat-abi = hard "-DCMAKE_C_FLAGS: STRING =" - march = armv6 \
 -mfpu = vfp -mfloat-abi = hard "../ 

 make 

 sudo make install  

