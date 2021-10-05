# File System

> On a UNIX system, everything is a file;

## Why?

- Essentially everything stored on the computer is `just a stream of bytes`.
- If everything is a file then, we just need **single protocol** for interoperability and handling.
- This also provdes clear transparency on what a `file` (aka a stream of bytes) does.

## What do we mean by everything?

- Regular files: Common type such as binaries, images, text files, shared libs etc
- Directory: file containing a list of files.
- Character device: device where the driver communicates by sending/receiving single characters (serial ports, sound cards).
- Block device: device where the driver communicates by sending entire blocks of data (hard disks, USB cameras, Disk-On-Key).
- Pipes: Mechanism to perform interprocess communication.
- Links: Symbolic links for a file.
- Sockets: TCP/IP sockets.
- Processes: Stored information aboit a running program

## Understanding file distinctions

As a quick background check, `ls -l` returns 8 columns. Going from left to right, we have:

1. File permissions
2. Number of hard links
3. Owner name
4. Group name
5. File size
6. Month of last modification
7. Date of last modification
8. Name of the file

Running the `ls -l` command, we can inspect the file type by looking at the first character in the output of the first column (aka file permissions output).

Below is a list of the core file types found on a Linux system:

```
- Regular file
d Directory
l Link
c Special file
s Socket
p Named pipe
b Block device
```

## Examples

Note, I am running most of the following commands on a basic `alpine` docker image:

```
docker run -it alpine
```

**Regular files, directories and symbolic links are just files**

Run the following commands and inspect the file types:
```bash
touch test.txt
mkdir test/
ln -s test.txt link_test.txtg
```

Output:

```bash
$ ls -l
lrwxrwxrwx    1 root     root       8 Oct  5 00:01 link_test.txt -> test.txt
drwxr-xr-x    2 root     root    4096 Oct  5 00:00 test
-rw-r--r--    1 root     root       0 Oct  4 23:59 test.txt
```

Here, we see that:

- `-` is used to indicate that `test.txt` is a regular file.
- `d` is used to indicate that `test/` is a directory.
- `l` is used to indicate that `link_test.txt` is a symbolic link, pointing to `test.txt`

**Binaries are just regular files**

Here, we see that the `bash` binary is just a regular file:

```bash
$ cd bin
$ ls -l *ls*
-r-xr-xr-x  1 root  root  623472 22 Sep  2020 bash
```

**Processes are directories containing files**

We note that processes are directories, containing files holding metadata about that process:

```bash
# Run Vim as a background process
$ vim &
# Get PID (example here is 25)
[1] 25 
# View running vim process with PID in /proc
$ cd /proc/25
# View the symbolic link on where the vim process was started from
$ ls -l cwd
# View exe of where vim is located
$ ls -l exe

# Kill the vim process, and /proc/25 should be gone
$ kill -9 25
```

**Block devices are also files**

We see that the connected hard drive to my laptop is a block device, which is a file:

```bash
$ cd /dev
$ ls -l *disk0*
brw-r-----  1 root  operator    1,   0  5 Oct 09:28 disk0
```

**Stdout, Stdin, Stderr are symbolic links, which are files** 

```bash
$ cd /dev
$ ls -l *std*
lrwxrwxrwx    1 root     root            15 Oct  5 00:17 stderr -> /proc/self/fd/2
lrwxrwxrwx    1 root     root            15 Oct  5 00:17 stdin -> /proc/self/fd/0
lrwxrwxrwx    1 root     root            15 Oct  5 00:17 stdout -> /proc/self/fd/1
```

We see that it matches the pipes of stdin=0, stdout=1, stderr=2

## References

- [General overview of the Linux file system](https://tldp.org/LDP/intro-linux/html/sect_03_01.html)
- [Everything is a file](https://www.youtube.com/watch?v=dDwXnB6XeiA)