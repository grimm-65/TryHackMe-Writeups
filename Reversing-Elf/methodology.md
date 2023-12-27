https://tryhackme.com/room/reverselfiles
Crackme1

chmod +x crackme1\
./crackme1

run above commands to get the flag
![Alt command](./img/crackme1.png)

    Crackme2

chmod +x crackme2\
./crackme2\
 it gives message : Usage: ./crackme2 password

so it needs a password try: password

![Alt command](./img/crackme2.png)

load the binary into ghidra

![Alt command](./img/crackme2ghidra.png)

Here we see our input is being compared with _super_secret_password_

pass it as the password and get

![Alt command](./img/crackme2soln.png)

    Crackme3

![Alt command](./img/crackme3.png)

![Alt command](./img/crackme3b.png)

load into ghidra

![Alt text](./img/crackme3ghidra.png)

strcmp which compares our input to a bae64 encoded string
_ZjByX3kwdXJfNWVjMG5kX2xlNTVvbl91bmJhc2U2NF80bGxfN2gzXzdoMW5nNQ==_

decode it to get the flag

![Alt command](./img/crackme3soln.png)

    Crackme4

![Alt command](./img/crackme4.png)

load into ghidra

![Alt command](./img/crackme4ghidra1.png)

Here we see a function _compare_pwd_ which takes in our input

Checking the compare_pwd function

![Alt command](./img/crackme4ghidra2.png)

We see that is compares our input with something stored in _*local_28*_

if the are equal ivar is set to 0 and _password Ok_ is printed

else _\*password not ok_\* is printed

we need to see what is stored in _local_28_

We will now use a debugger gdb

gdb crackme4

we then list functions in the binary

![Alt command](./img/crackme4gdb1.png)

As always we target strcmp :)

Set a break point at memory address of this function

![Alt command](./img/crackme4gdbr.png)

One break point is set run the binary

run yolo
Binary is executed until breakpoint is reached
we then view current state of the registers

info registers

rax and rdx are general purpose re gisters and from above we see that they have memory address values

To print strings at these addresses we use command

(gdb) x/s 0x7fffffffdad0

![Alt command](./img/crackme4soln.png)

printing values at rax and rdx we get our input and the password

    Craackme5

![Alt command](./img/crackme5.png)

load into ghidra

![Alt command](./img/crackme5ghidra.png)

We see the strcmp again :)

which compares our input local_58 with what is stored in &local_38

To see what is stored at &local_38 we use our debugger

load the binary into gdb and check functions used

![Alt command](./img/crackme5gdb.png)

put a break point on strcmp then run

![Alt command](./img/crackme5soln.png)

View what is sored in rax and rdx to get the password

    Crackme6

![Alt command](./img/crackme6.png)

![Alt command](./img/crackme6b.png)

load into ghidra

![Alt command](./img/crackme6ghidra.png)
we have a function compare_pwd which takes our input as argument

we check that function

![Alt command](./img/crackme6bghidra.png)

There is another function my_secure_test()
we check this also

![Alt command](./img/crackme6cghidra.png)

Here we a bunch of if satements that are used to check if our input matches

from this we can determine the password
13...

    Crackme7

We have 3 choices try all to see what the do
![Alt command](./img/crackme7.png)

load the binary into ghidra

![Alt command](./img/crackme7ghidra.png)

Here we see logic for each of the choices we make

particular interest on option 2 where it prints

"Wow such h4x0r!" if we give a particular value as our input

When we enter the value directly error so we need to convert it hex to decimal

![Alt command](./img/crackme7soln.png)

    Crackme8

![Alt command](./img/crackme8.png)

![Alt command](./img/crackme8b.png)

load into ghidra

![Alt command](./img/crackme8ghidra.png)

atoi => converts a string into an integer numerical representation

convert the -0x35010ff3 value to decimal, which is -889262067 and then pass it as the password to the binary

![Alt command](./img/crackme8soln.png)
