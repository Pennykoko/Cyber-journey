TryHackMe - ROT47 Decoding

Challenge String: 7=28Lx{@G6~776?D:G6$64FC:EJPN

What is ROT47?
- Like Caesar cipher, but for 94 printable keyboard characters: from ! to ~
- It shifts by 47 positions. Since 94/2 = 47, doing it twice gives you back the original.
- So encode = decode (same operation)

How I Solved It
1. Went to https://www.dcode.fr/rot-47
2. Pasted the string
3. Got: flag{ILoveOffensiveSecurity!}

Characters Breakdown
7=28Lx decodes to flag{ - this pattern shows up in almost every CTF.

Lesson: Not every flag needs code, sometimes it's just an online decoder.
