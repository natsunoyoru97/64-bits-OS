#/***************************************************
#		版权声明
#
#	本操作系统名为：MINE
#	该操作系统未经授权不得以盈利或非盈利为目的进行开发，
#	只允许个人学习以及公开交流使用
#
#	代码最终所有权及解释权归田宇所有；
#
#	本模块作者：	田宇
#	EMail:		345538255@qq.com
#
#
#***************************************************/

all: 
	make refresh
	make write
	make run

generate: boot.bin loader.bin kernel.bin

boot.bin:
	nasm boot.asm -o boot.bin

loader.bin:
	nasm loader.asm -o loader.bin

kernel.bin:
	nasm kernel.asm -o kernel.bin

write:
	dd if=boot.bin of=boot.img bs=512 count=1 conv=notrunc
	if [ ! -e "tmp" ];then \
		mkdir tmp; \
	fi
	# To run in Ubuntu 18.04, you need sudo privilege. 
	sudo mount -t vfat -o loop boot.img tmp/
	sudo cp loader.bin tmp/
	sudo cp kernel.bin tmp/
	sync
	sudo umount tmp/
	rm -r tmp/

refresh:
	make clean
	make generate

clean:
	rm -rf *.bin *.asm~ Makefile~ loader.bin boot.bin kernel.bin

run:
	bochs -f myBochsSrc.txt
