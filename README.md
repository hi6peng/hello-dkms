# hello-dkms

~~~
$ tree /usr/src/hello-0.1/
/usr/src/hello-0.1/
├── dkms.conf
├── hello.c
└── Makefile

0 directories, 3 files
~~~

~~~
$ sudo dkms add -m hello -v 0.1

$ sudo dkms build -m hello -v 0.1
$ sudo dkms install -m hello -v 0.1

$ sudo modprobe hello

$ dkms status

$ sudo dkms remove -m hello -v 0.1 --all
~~~

You can also ask DKMS to build and install this module for another kernel version after "dkms add". 

~~~
$ sudo dkms build -m hello -v 0.1 -k 4.4.0-57-generic
$ sudo dkms install -m hello -v 0.1 -k 4.4.0-57-generic
~~~

It is also possible to build against multiple kernel versions. 

~~~
$ sudo dkms build -m hello -v 0.1 -k 4.4.0-57-generic -k 4.4.0-58-generic
~~~

Using "dkms mkdeb" to build deb package. You shall run "dkms mkdeb" after "dkms add" and "dkms build" 

~~~
sudo apt-get install debhelper
sudo dkms mkdeb -m hello -v 0.1
~~~

[DKMSPackaging](https://wiki.ubuntu.com/Kernel/Dev/DKMSPackaging)
