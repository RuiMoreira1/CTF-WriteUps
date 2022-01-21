## **CTF 10**

## **CTF 10 1**

The strategy to solve this CTF was using XSS attack using the cookies, and waiting 2 minutes for the administrator approval, therefore getting the flag.
Terminal 1 
:---------:|
![Terminal print of lab task1](img/Week6/l6t1t3.jpeg) | 
Terminal 1 
:---------:|
![Terminal print of lab task1](img/Week6/l6t1t3.jpeg) | 


### **CTF 10 2**

By running checksec in the binary we have we can see, that NX is disabled and PIE is enabled. Therefore, we know that
the address will be randomized each execution so we need to play around that. Since NX is disabled, we will probably have to inject some shellcode.

Terminal 1 
:---------:|
![Terminal print of lab task1](/home/seed/Pictures/ctf10_5.png) | 


By executing the binary given, we see that we get a base stack address leak and we will work aroud that to defeat Pie.

Terminal 1 
:---------:|
![Terminal print of lab task1](/home/seed/Pictures/ctf10-2-2.png) | 

We will now see how many characters we need to write from the base address to start overwritting the instruction pointer.

Terminal 1 
:---------:|
![Terminal print of lab task1](/home/seed/Pictures/ctf102-1.png)  | 

We see that the distance between the base address and the EIP is 107 (we will user 108, gdb often misses by 1/2 and after some testing 108 is the distance between the base address and the EIP).

So our stategy will be, given that we have the leaked base address, we will insert the shellcode, crafted using python pwn tool, then overwrite the EIP with the leaked base address, directing our code to the shellcode, that is in buffer base address.

Terminal 1 
:---------:|
![Terminal print of lab task1](/home/seed/Pictures/ctf10_1.png) | 