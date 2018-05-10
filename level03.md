# Level 03
## Tags
buffew overflow | binary | pointers | gdb | radare2
## Writeup
The structure of opts:
16 Bytes of Characters: XXXXXXXXXXXXXX
4 Bytes of Function Ptr: XXXXXXXX

I opened level03 in IDA Pro

function f started at 0x0040054C, since everything is stored little-endian style

ops:
Chars: XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
FP:      4C054000

Now when Chars is written, it writes 17 Bytes instead of 16 since i=0 to i<=16 = 17 written
So we have to overflow it and overwrite FP to go to 0x0040056E instead where it tells us we won

so we can send the payload of AAAAAAAAAAAAAAAA\x6E

## Flag
raL6E8S0Y9BpioDK
