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
>9 \[
 >3 x22 ... >9 x28
>[3-9] x2\p[2-8]
 >4 x32 ... >9 x37
>[4-9] x3\p[2-7]
 >2 x12 /?u l ... >8 x18 /?u l
-c >[2-8] x1\1 /?u l
-c >9 \[ /?u l
 >3 x22 /?u l ... >9 x28 /?u l
-c >[3-9] x2\p[2-8] /?u l
 >4 x32 /?u l ... >9 x37 /?u l
-c >[4-9] x3\p[2-7] /?u l
 Now to the suffix stuff...
<* l $[1-9!0a-rt-z"-/:-@\[-`{-~]
-c <* (?a c $[1-9!0a-rt-z"-/:-@\[-`{-~]
-[:c] <* !?A (?\p1[za] \p1[lc] $s M 'l p Q X0z0 'l $s
-[:c] <* /?A (?\p1[za] \p1[lc] $s
<* l r $[1-9!]
-c <* /?a u $[1-9!]
-[:c] <- (?\p1[za] \p1[lc] Az"'s"
-[:c] <- (?\p1[za] \p1[lc] Az"!!"
-[:c] (?\p1[za] \p1[lc] $! <- Az"!!"
 Removing vowels...
-[:c] /?v @?v >2 (?\p1[za] \p1[lc]
/?v @?v >2 <* d
 crack -> cracked, crack -> cracking
<* l [PI]
-c <* l [PI] (?a c
 mary -> marie
-[:c] <* (?\p1[za] \p1[lc] )y omi $e
 marie -> mary
-[:c] (?\p1[za] \p1[lc] )e \] <+ )i val1 oay
 The following are some 3l33t rules
-[:c] l /[aelos] s\0\p[4310$] (?\p1[za] \p1[:c]
-[:c] l /a /[elos] sa4 s\0\p[310$] (?\p1[za] \p1[:c]
-[:c] l /e /[los] se3 s\0\p[10$] (?\p1[za] \p1[:c]
-[:c] l /l /[os] sl1 s\0\p[0$] (?\p1[za] \p1[:c]
-[:c] l /o /s so0 ss$ (?\p1[za] \p1[:c]
-[:c] l /a /e /[los] sa4 se3 s\0\p[10$] (?\p1[za] \p1[:c]
-[:c] l /a /l /[os] sa4 sl1 s\0\p[0$] (?\p1[za] \p1[:c]
-[:c] l /a /o /s sa4 so0 ss$ (?\p1[za] \p1[:c]
-[:c] l /e /l /[os] se3 sl1 s\0\p[0$] (?\p1[za] \p1[:c]
-[:c] l /[el] /o /s s\0\p[31] so0 ss$ (?\p1[za] \p1[:c]
-[:c] l /a /e /l /[os] sa4 se3 sl1 s\0\p[0$] (?\p1[za] \p1[:c]
-[:c] l /a /[el] /o /s sa4 s\0\p[31] so0 ss$ (?\p1[za] \p1[:c]
-[:c] l /e /l /o /s se3 sl1 so0 ss$ (?\p1[za] \p1[:c]
-[:c] l /a /e /l /o /s sa4 se3 sl1 so0 ss$ (?\p1[za] \p1[:c]
 Now to the prefix stuff...
l ^[1a-z2-90]
-c l Q ^[A-Z]
^[A-Z]
l ^["-/:-@\[-`{-~]
-[:c] <9 (?a \p1[lc] A0"[tT]he"
-[:c] <9 (?a \p1[lc] A0"[aA]my"
-[:c] <9 (?a \p1[lc] A0"[mdMD]r"
-[:c] <9 (?a \p1[lc] A0"[mdMD]r."
-[:c] <9 (?a \p1[lc] A0"__"
<- !?A l p ^[240-9]
 Some word pair rules...
 johnsmith -> JohnSmith, johnSmith
-p-c (?a 2 (?a c 1 [cl]
 JohnSmith -> john smith, john_smith, john-smith
-p 1 <- $[ _\-] + l
 JohnSmith -> John smith, John_smith, John-smith
-p-c 1 <- (?a c $[ _\-] 2 l
 JohnSmith -> john Smith, john_Smith, john-Smith
-p-c 1 <- l $[ _\-] 2 (?a c
 johnsmith -> John Smith, John_Smith, John-Smith
-p-c 1 <- (?a c $[ _\-] 2 (?a c
 Applying different simple rules to each of the two words
-p-[c:] 1 \p1[ur] 2 l
-p-c 2 (?a c 1 [ur]
-p-[c:] 1 l 2 \p1[ur]
-p-c 1 (?a c 2 [ur]
 jsmith -> smithj, etc...
-[:c] (?a \p1[lc] [{}]
-[:c] (?a \p1[lc] [{}] \0
 Toggle case...
-c <+ )?u l Tm
-c T0 Q M c Q l Q u Q C Q X0z0 'l
-c T[1-9A-E] Q M l Tm Q C Q u Q l Q c Q X0z0 'l
-c l Q T[1-9A-E] Q M T\0 Q l Tm Q C Q u Q X0z0 'l
-c >2 <G %2?a [lu] T0 M T2 T4 T6 T8 TA TC TE Q M l Tm Q X0z0 'l
-c >2 /?l /?u t Q M c Q C Q l Tm Q X0z0 'l
 Deleting chars...
>[2-8] D\p[1-7]
>[8-9A-E] D\1
-c /?u >[2-8] D\p[1-7] l
-c /?u >[8-9A-E] D\1 l
=1?a \[ M c Q
-c (?a >[1-9A-E] D\1 c
# Inserting a dot...
-[:c] >3 (?a \p1[lc] i[12].
# More suffix stuff...
<- l Az"[190][0-9]"
-c <- (?a c Az"[190][0-9]"
<- l Az"[782][0-9]"
-c <- (?a c Az"[782][0-9]"
<* l $[A-Z]
-c <* (?a c $[A-Z]
 cracking -> CRACKiNG
-c u /I sIi
 Crack96 -> cRACK96
%2?a C Q
 Crack96 -> cRACK(^
/?A S Q
 Crack96 -> CRaCK96
-c /?v V Q
 Really weird charset conversions, like "england" -> "rmh;smf"
:[RL] Q
l Q [RL]
-c (?a c Q [RL]
:[RL] \0 Q
 Both prefixing and suffixing...
<- l ^[1!@#$%^&*\-=_+.?|:'"] $\1
<- l ^[({[<] $\p[)}\]>]
 The rest of two-digit suffix stuff, less common numbers...
<- l Az"[63-5][0-9]"
-c <- (?a c Az"[63-5][0-9]"
 Some multi-digit numbers...
-[:c] (?a \p1[lc] Az"007" <+
-[:c] (?a \p1[lc] Az"123" <+
-[:c] (?a \p1[lc] Az"[0-9]\0\0" <+
-[:c] (?a \p1[lc] Az"1234" <+
-[:c] (?a \p1[lc] Az"[0-9]\0\0\0" <+
-[:c] (?a \p1[lc] Az"12345" <+
-[:c] (?a \p1[lc] Az"[0-9]\0\0\0\0" <+
-[:c] (?a \p1[lc] Az"123456" <+
-[:c] (?a \p1[lc] Az"[0-9]\0\0\0\0\0" <+
................
