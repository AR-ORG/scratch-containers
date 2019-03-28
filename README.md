# Experimenting with containers from scratch - debian / ubuntu 

##  What is a minimal container? 

    A minimal container contains the least amount of packages. A rootfs can be treated with the most basic container 

##  What is a rootfs 

    A root file system contains everything needed to support a full Linux System. rootfs is a type of root file system. 
    
    rootfs is considered to be a minimal root filesystem which is an instance of ramfs. 
    
    Only certian libraries / binaries are loaded with a minimal rootfs. 
    
    It has directories for proc, sys, dev - however a rootfs is not mounted by default.
    
    To use rootfs - you will have to mount /dev /sys to your local /dev and /sys

##  Install debootstrap to create rootfs 

    apt-get install debootstrap
    
##  Use debootstrap to create rootfs 

    1.  Debian rootfs

    mkdir rootfs_debian
    
    debootstrap stable rootfs_debian http://deb.debian.org/debian/
    
    
    2.  Ubuntu rootfs
    
    mkdir rootfs_ubuntu
    
    debootstrap --arch=amd64 xenial rootfs_ubuntu http://archive.ubuntu.com/ubuntu/
    
##  Change root using chroot 

    1. Debian
    
    chroot  rootfs_debian /bin/bash 
    
    mount -t proc proc /proc
    
    2. Ubuntu
    
    chroot rootfs_ubuntu /bin/bash
    
    mount -t proc proc /proc
    
    3.  Unmount proc after playing around 
    
    umount /root/rootfs_ubuntu/proc
    
    umount /root/rootfs_debian/proc
    

##  What is a Linux namespace

    Linux namespaces allow isolation of global system resources between multiple processes.
    The isolation can be on the levels of PID, mounts, IPC, network, user, UTS etc. 
    
##  Using unshare to create namespaces with chroot 

    
  
  
  
  
    
    
