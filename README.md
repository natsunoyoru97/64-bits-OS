# 64-bits-OS

![](https://img.shields.io/badge/Ubuntu-18.04-success)
![](https://img.shields.io/badge/Parallels-15.1.4-success)

An OS based on [this book](https://book.douban.com/subject/30222325/).

The source code is under git version control, so you can revert to the snapshots(commits) of the program to look up the code in any chapter.

**Chinese README will be updated. I can only type in English in my virtual machine, the docs in Chinese will be updated after the code part is finished, or it may corrupt the cleanness the commits (and you guys will have a hard time to find the commits you want to revert to :) ).**

I also made some modification in Makefile, so it's easier to run these codes in bochs.

# Get Started
- Have your bochs COMPLIED rather than downloaded from the package managers, life would be much easier when you debug the kernel.
- Configure your bochs with these flags:

```bash
./configure --with-x11 --with-wx --enable-debugger --enable-disasm --enable-all-optimizations --enable-readline --enable-long-phy-address --enable-ltdl-install --enable-idle-hack --enable-plugins --enable-a20-pin --enable-smp --enable-cpu-level=6 --enable-large-ramfile --enable-repeat-speedups --enable-fast-function-calls --enable-handlers-chaining --enable-trace-linking --enable-configurable-msrs --enable-show-ips --enable-cpp --enable-debugger-gui --enable-iodebug --enable-logging --enable-assert-checks --enable-monitor-mwait --enable-x86-debugger --enable-pci --enable-usb --enable-voodoo --enable-avx --enable-evex --enable-x86-64

```
- Run ``make``.
- If there is a ``file not exists`` error, try these commands:

```bash
cp misc/bximage.cpp misc/bximage.cc
cp iodev/hdimage/hdimage.cpp iodev/hdimage/hdimage.cc
cp iodev/hdimage/vmware3.cpp iodev/hdimage/vmware3.cc
cp iodev/hdimage/vmware4.cpp iodev/hdimage/vmware4.cc
cp iodev/hdimage/vpc-img.cpp iodev/hdimage/vpc-img.cc
cp iodev/hdimage/vbox.cpp iodev/hdimage/vbox.cc

```
- Run ``make install``. 
- If you encounter with the ``recipe for target 'install_bin' failed`` error, you may not have privilege. Try ``sudo make install`` instead. 
- Make sure your bochs source file is SUCCESSFULY complied, or bochs might not run as expected.
- Run ``bochs -f <your-path>/MINEboot/myBochsScript.txt``.

# TODO
### 3.1 Boot loader
- Apply FAT16 file istead of FAT12

