## Dirty COW (CVE-2016-5195)

> After gaining access to vulnerable machine as chown in writeup1, and as part of machine discovery i checked the kernel version with "uname -a".
```
Linux BornToSecHackMe 3.2.0-91-generic-pae #129-Ubuntu SMP Wed Sep 9 11:27:47 UTC 2015 i686 i686 i386 GNU/Linux
```
> with some research this kernel version vulnerable to dirty cow vulnerability.
> **Dirty COW** (Copy-On-Write) is a security vulnerability that was discovered in 2016 in the Linux kernel. It allows a local attacker to gain unauthorized access to certain read-only memory mappings, such as those belonging to the system or other users.
> 
> The vulnerability arises because of a race condition in the kernel's memory management. Specifically, the kernel allows multiple processes to map the same piece of memory into their own address spaces, and then keep a reference count of how many processes are currently using the mapping. When a process wants to modify the memory, it is supposed to create a private copy for itself, which is known as copy-on-write.
> 
> However, the Dirty COW vulnerability allows an attacker to exploit the race condition and obtain a writable copy of the memory mapping, even if it is supposed to be read-only. This can be done by repeatedly accessing the memory in a specific way, causing the kernel to believe that it is still in use by another process.
> 
> The vulnerability can be exploited to gain access to sensitive information, such as password hashes or secret keys, or to elevate privileges on the system. It has been patched in most modern Linux distributions, but it is important to ensure that your system is up to date in order to protect against this and other security vulnerabilities.
> 
#### + download the exploit:
```
https://raw.githubusercontent.com/firefart/dirtycow/master/dirty.c
```

#### + compile the exploit with :
```
gcc -pthread dirty.c -o dirty -lcrypt
```

#### + run the newly create binary by either doing:
```
"./dirty" or "./dirty my-new-password"
```
### Ressources:
* [dirty cow](https://dirtycow.ninja/)
* [liveoverflow explaination](https://youtu.be/kEsshExn7aE)
* [medium article explaining dirty cow](https://0xcd4.medium.com/the-dirty-cow-race-condition-attack-7ba27f78f865)
* [understanding race condition, and dirty cow vulnerability](https://www.cs.toronto.edu/~arnold/427/18s/427_18S/indepth/dirty-cow/index.html)
