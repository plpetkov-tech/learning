# POSIX  

POSIX is the Portable Operating System Interface standard, IEEE Std 1003.1-1988 and related.  These standards, based on the Unix operating system, define a set of programming and command interfaces.  Programs and scripts following these standards are supposed to be easily portable between operating system platforms providing these interfaces.  

The POSIX standards imply a model for file system organization: POSIX file systems are organized as directories (folders) containing files (documents).  The POSIX programming API defined a number of operations to work with files, directories, and entire file systems:  
  
mount, umount the file system  
open, close file descriptor  
write, read to/from file descriptor  
mkdir, rmdir, creat, unlink, link, symlink  
fcntl (byte range locks, etc.)  
stat, utimes, chmod, chown, chgrp  
Path names are case sensitive, components are separated with forward slash (/).  
Essentially, this is the API that evolved for Unix and adopted by Linux.  

POSIX file systems are treated as a sequence of bytes.  However, internally the data content of a file is stored as logical sequence of file system blocks:

inodesEach block is a fixed number of bytes.  The last block might not be full.  
Within a block, all the bytes are sequential.  However, within a file, the blocks might not reside sequentially on the disk.  
Underlying storage systems are usually organized as blocks, and ideally file system blocks are aligned with the storage system’s blocks.  
File systems also contain metadata, i.e., “data about the data”:  

There is an inode for each file or directory, providing:  
Locations of the data blocks for the file  
Attributes about the file, like “time last accessed” or “owner of the file”  
The inode table records where each inode is located, indexed by number.  
Directories are special files listing the names and inode numbers of files under the folder.  

## POSIX Basic Regular Expressions  

<https://en.wikibooks.org/wiki/Regular_Expressions/POSIX_Basic_Regular_Expressions>
