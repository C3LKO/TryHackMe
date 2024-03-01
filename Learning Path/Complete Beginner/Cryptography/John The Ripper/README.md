![image](https://user-images.githubusercontent.com/51442719/172149525-1e5cadd6-ca8b-457a-b19e-b767549d7124.png)
- [x] [John The Ripper](https://tryhackme.com/room/johntheripper0)
  > Learn how to use John the Ripper - An extremely powerful and adaptable hash cracking tool
    - [x] Task 1  John who?
    - [x] Task 2  Setting up John the Ripper
    - [x] Task 3  Wordlists
    - [x] Task 4  Cracking Basic Hashes
    - [x] Task 5  Cracking Windows Authentication Hashes
    - [x] Task 6  Cracking /etc/shadow Hashes
    - [x] Task 7  Single Crack Mode
    - [x] Task 8  Custom Rules
    - [x] Task 9  Cracking Password Protected Zip Files
    - [x] Task 10  Cracking Password Protected RAR Archives
    - [x] Task 11  Cracking SSH Keys with John
    - [x] Task 12  Further Reading

-

 This file is part of John the Ripper password cracker,
 Copyright (c) 1996-2006,2008-2013,2019 by Solar Designer

Redistribution and use in source and binary forms, with or without
 modification, are permitted.

 There's ABSOLUTELY NO WARRANTY, express or implied.

 Please note that although this configuration file is under the cut-down BSD
 license above, many source files in John the Ripper are under GPLv2.
 For licensing terms for John the Ripper as a whole, see doc/LICENSE.


[Options]
 Wordlist file name, to be used in batch mode
Wordlist = $JOHN/password.lst
 Use idle cycles only
Idle = Y
 Crash recovery file saving delay in seconds
Save = 600
 Beep when a password is found (who needs this anyway?)
Beep = N

 "Single crack" mode rules
[List.Rules:Single]
 Simple rules come first...
:
-s x**
-c (?a c Q
-c l Q
-s-c x** /?u l
 These were not included in crackers I've seen, but are pretty efficient,
 so I include them near the beginning
>6 '6
>7 '7 l
-c >6 '6 /?u l
>5 '5
 Weird order, eh? Can't do anything about it, the order is based on the
 number of successful cracks...
<* d
r c
-c <* (?a d c
-c >5 '5 /?u l
-c u Q
-c )?a r l
-[:c] <* !?A \p1[lc] p
-c <* c Q d
-c >7 '7 /?u
>4 '4 l
-c <+ (?l c r
-c <+ )?l l Tm
>3 '3
-c >4 '4 /?u
-c >3 '3 /?u l
-c u Q r
<* d M 'l f Q
-c <* l Q d M 'l f Q
 About 50% of single-mode-crackable passwords get cracked by now...
 >2 x12 ... >8 x18
>[2-8] x1\1
