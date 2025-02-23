# Part I : Learn

Dans cette partie, je vous fais (re)découvrir quelques commandes usuelles quand on travaille autour des programmes et des processus.

**Au menu : on dissèque des programmes, et on repère les syscalls qu'ils utilisent.**

## Sommaire

- [Part I : Learn](#part-i--learn)
  - [Sommaire](#sommaire)
  - [1. Anatomy of a program](#1-anatomy-of-a-program)
    - [A. `file`](#a-file)
    - [B. `readelf`](#b-readelf)
    - [C. `ldd`](#c-ldd)
  - [2. Syscalls basics](#2-syscalls-basics)
    - [A. Syscall list](#a-syscall-list)
    - [B. `objdump`](#b-objdump)

## 1. Anatomy of a program

**Un programme est un fichier *exécutable*. C'est à dire que :** 

- c'est un simple fichier
- il est composé de plusieurs sections
  - la section `.text` contient les instructions du programme pour le CPU
  - les autres sections contiennent essentiellement des metadonnées
- il peut être compilé...
  - statiquement : tout est dans le programme
  - dynamiquement : le programme pourra faire appel à des librairies du système
- il est marqué comme étant "exécutable"
  - sur Linux, on donne la permission d'exécution avec `chmod`

Dans cette partie, on va voir quelques outils très usuels pour obtenir des infos sur un programme.

### A. `file`

🌞 **Utiliser `file` pour déterminer le type de :**

- la commande `ls`
```ps
[cauchemar@vbox ~]$ file /usr/bin/ls
/usr/bin/ls: ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, BuildID[sha1]=1afdd52081d4b8b631f2986e26e69e0b275e159c, for GNU/Linux 3.2.0, stripped

[cauchemar@vbox ~]$ file /usr/sbin/ip
/sbin/ip: ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, BuildID[sha1]=77a2f5899f0529f27d87bb29c6b84c535739e1c7, for GNU/Linux 3.2.0, stripped
