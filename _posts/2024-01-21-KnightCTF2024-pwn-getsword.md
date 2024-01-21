# KnightCTF2024 PWN - Get Sword

I am writing this writeup to share my thought process on how to tackle a PWN challenge for any beginners who want to learn PWN (I am a beginner myself). This took me way longer than expected to solve, probably because I havent joined a CTF in awhile due to exams.

## Initial Analysis

We are provided with an ELF file and we will first gather some information about the challenge we are dealing with.

```bash
└─$ file get_sword           
get_sword: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked, interpreter /lib/ld-linux.so.2, BuildID[sha1]=4a9b260935bf815a04350e3bb9e0e4422f504b2a, for GNU/Linux 4.4.0, not stripped
```

Running the file command reveals that it is a 32 bit executable, and it is "not stripped" so the debugging symbols are not removed.

```bash
└─$ checksec --file=get_sword
RELRO           STACK CANARY      NX            PIE             RPATH      RUNPATH      Symbols         FORTIFY Fortified       Fortifiable     FILE
Partial RELRO   No canary found   NX disabled   No PIE          No RPATH   No RUNPATH   35 Symbols        No    0               1               get_sword
```
