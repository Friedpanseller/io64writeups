# Level 04
## Tags
buffer overflow | binary | stack | shellcode | return address | gdb | radare2
## Writeup
First I had a look at the sourcecode

char * arg is copied unsafely into buf so it means you can replace data in the stack frame, esp the return addr.

I opened the program up in IDA and went to the dobug function, which starts from 0x40050c and ends at 0x40052c
the strcpy function is at 0x400526

using GDB I entered AAAAAAAAAAAAAAAAAAAAAAA as the argement, I made a b right after strcpy and checked the stack

register rdi and rax stored where buf starts "4141414141...." and it was at location 0x7ffd67fd1370 (rdi == rax since right before strcpy "mov rdi, rax")

from rdi to return addr there are 24 bytes, the return addr was 0x400500

I tried editing the function to return open a shell but since ASLR is enabled the location gets shuffled around everytime so we have to inject a bit of our own shell code and jmp to where we started our injection (rdi || rax)

Using radare2 "/R jmp rdi" to find out if the function can return to somewhere that has a jmp rdi instruction. No results, so I tried "/R jmp rax" and it found jmp rax at 0x600477

So we need our function to return to 0x600477, so it can exec jmp rax, and since in rax is stored our injected code to pop a shell, it will exec the code.

Shellcode was googled "x86_64 shellcode" 

The code will put 0x600477 return addr at the end, so it goes to jmp rax, and jumps to the start of the shell code and starts executing

./level04 $(perl -e 'printf "\x5c\x31\xf6\x48\xbb\x2f\x62\x69\x6e\x2f\x2f\x73\x68\x56\x53\x54\x5f\x6a\x3b\x58\x31\xd2\x0f\x05\x77\x04\x60"')
## Flag
IpzNGTYQOK5bh3xC
