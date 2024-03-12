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

fsck.ext2 cs111-base.img
This command checks that the filesystem is correct.

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

python -m unittest:
This runs the given tests to check our program and filesystem.

Output:

## Cleaning up
TODO
cmds:
sudo umount mnt
The command "sudo unmount mnt" unmounts the filesystem we previously mounted for testing.

rmdir mnt
The "rmdir mnt" command removes the mnt directory created in the process of running the code.

make clean
The "make clean" command is defined in the Makefile to remove the executble ext2-create and the ext2-create.o object file. It also removes all img files.
