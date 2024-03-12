# Hey! I'm Filing Here

In this lab, I successfully implemented a 1 MiB ext2 file system that consists of 2 directors, 1 regular file, and 1 symbolic link along with their proper permissions.

## Building

TODO
cmd: 
make
Running "make" creates the object and exectuble file for ext2-create. 

./ext2-create
This runs the executable file created as a result of the make. After running the executabl, the cs111-base.img is created.

dumpe2fs cs111-base.img
This will dump the filesystem information that can be used for debugging. It includes information like inode count, block count, free blocks, and free inodes.

output:
Filesystem volume name: cs111 -base
Last mounted on: <not available >
Filesystem UUID: 5a1eab1e -1337 -1337 -1337 - c0ffeec0ffee
Filesystem magic number : 0 xEF53
Filesystem revision #: 0 ( original )
Filesystem features : (none)
Default mount options : (none)
Filesystem state : clean
Errors behavior : Continue
Filesystem OS type: Linux
Inode count : 128
Block count : 1024
Reserved block count : 0
Free blocks : 1000
Free inodes : 115
First block : 1
Block size: 1024
Fragment size: 1024
Blocks per group : 8192
Fragments per group : 8192
Inodes per group : 128
Inode blocks per group : 16
Last mount time: n/a
Last write time: Sun May 23 19:35:00 2021
Mount count : 0
Maximum mount count : -1
Last checked : Sun May 23 19:35:00 2021
Check interval : 1 (0:00:01)
Next check after : Sun May 23 19:35:01 2021
Reserved blocks uid: 0 (user root)
Reserved blocks gid: 0 ( group root)

Group 0: ( Blocks 1 -1023)
Primary superblock at 1, Group descriptors at 2-2
Block bitmap at 3 (+2)
Inode bitmap at 4 (+3)
Inode table at 5 -20 (+4)
1000 free blocks , 115 free inodes , 2 directories
Free blocks : 24 -1023
Free inodes : 14 -128

fsck.ext2 cs111-base.img
This command checks that the filesystem is correct.

output:
e2fsck 1.46.4 (18-Aug-2021)
cs111 -base has gone 0 days without being checked , check forced .
Pass 1: Checking inodes , blocks , and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
3
cs111 -base: 13/128 files (0.0% non - contiguous ), 24/1024 blocks
4

mkdir mnt
This creates a directory called mnt that is used to mount my filesystem onto.

sudo mount -o loop cs111-base.img mnt
This command mounts the filesystem I created onto the mnt directory. The loop part of the command allows the cs111-base.img file to be mounted as a block device.

## Running

TODO
cmd:
ls -ain mnt/
This command will list all the files/directories in the directory called "mnt." The "a" flag stands for all meaning that even hidden files/directories will be shown. The "i" flag means inode and outputs the inode numbers of each file/directory. Finally the "n" tag means numeric-uid-gid. This means the output will include the numeric user and group ids.

Output:
total 105
942302 drwxr-xr-x  5 1000 1000    4096 Mar 11 23:49 .
937256 drwxr-xr-x 11 1000 1000    4096 Mar 10 15:25 ..
942325 -rw-r--r--  1 1000 1000 1048576 Mar 11 23:48 cs111-base.img
942324 -rwxr-xr-x  1 1000 1000   20888 Mar 11 22:40 ext2-create
942319 -rw-r--r--  1 1000 1000   16385 Mar 10 16:29 ext2-create.c
942323 -rw-r--r--  1 1000 1000   13392 Mar 11 22:40 ext2-create.o
942305 drwxr-xr-x  8 1000 1000    4096 Mar 11 23:44 .git
942317 -rw-r--r--  1 1000 1000     377 Mar 10 15:25 Makefile
     2 drwxr-xr-x  3    0    0    1024 Mar 11 23:42 mnt
   450 drwxr-xr-x  2 1000 1000    4096 Mar 10 16:08 __pycache__
942318 -rw-r--r--  1 1000 1000    1880 Mar 11 23:44 README.md
942320 -rw-r--r--  1 1000 1000    1585 Mar 10 15:25 test_lab4.py
942326 -rw-r--r--  1 1000 1000    1351 Mar 11 23:43 text
942322 -rw-r--r--  1 1000 1000       0 Mar 11 23:44 text2
942329 -rw-r--r--  1 1000 1000       0 Mar 11 23:49 text3

python -m unittest:
This runs the given tests to check our program and filesystem.

Output:
..
-------------------------------------------------
Ran 2 tests in 0.759s

OK
## Cleaning up
TODO
cmds:
sudo umount mnt
The command "sudo unmount mnt" unmounts the filesystem we previously mounted for testing.

rmdir mnt
The "rmdir mnt" command removes the mnt directory created in the process of running the code.

make clean
The "make clean" command is defined in the Makefile to remove the executble ext2-create and the ext2-create.o object file. It also removes all img files.
