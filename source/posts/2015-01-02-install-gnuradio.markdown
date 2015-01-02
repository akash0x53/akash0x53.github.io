---
title: "install-GNUradio"
date: 2015-01-02 10:37
categories:
slug: install-gnuradio
---

Here are the ways to install GNURadio on your Ubuntu machine  
<!--more-->  

#####1. Using source (git, tar)  
* Get source ``git clone http://git.gnuradio.org/git/gnuradio.git``  
or get weekly tarballs from [here.](http://jenkins.gnuradio.org/builds/gnuradio-current.tar.gz)  

* Check dependencies [Here](http://gnuradio.org/doc/doxygen/build_guide.html)
* And build GnuRadio   
```
$ mkdir build  
$ cd build  
$ cmake ../  
$ make  
$ sudo make install  
```

#####2. Using GnuRadio build script
* The script check dependencies and download if not met any. So just download and 
  execute the script.
 
* Download build script from [here](http://www.sbrac.org/files/build-gnuradio). 
* Make it executable, i.e ``chmod +x build-gnuradio``  
* and run it, ``./build-gnuradio``

#####3. Using PPA 
*  This is easiest way to install GnuRadio, gqrx, rtl-sdr, and many related tools  
*  Add PPA, ``$ sudo apt-add-repository ppa:gqrx-releases``  
*  Update repo   
*  and install GnuRadio ``sudo apt-get install gnuradio``  


