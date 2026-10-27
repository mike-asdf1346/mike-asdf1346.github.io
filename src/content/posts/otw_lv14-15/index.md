---
title: 'OverTheWire lv13-14 Learning Journal'
published: 2026-10-26
draft: false
description: '這是一篇無聊的學習筆記(x。主要用來紀錄我在OverTheWire遇到比較印象深刻的題目或是困難，還有我是如何理解其中的出題思路。在這篇中我會整理我遇到一個新觀念時是如何解決的。'
tags: ['OTW', 'Linux', 'Cybersecurity', 'Journal']
---

## Overview
> Updated 2026/10/27 -- refined general formatting and grammer inconsistency.
平台: OverTheWire  
戰爭遊戲: Bandit  
此篇Lv: Level 13 → Level 14  
狀態: Complete  
此篇是否含有flag: No  

![otw img](/otw-image.png 'goal')

## Learning Objectives

In this level, I learned how to access the OTW server at the next level without entering a password by using the SSH keys.

Here are the commands I'm going to use:
```bash
cat
```

```bash
ls
```

```bash
ssh
```

```bash
chmod
```  
 
## 1 - New Concepts

Using the given private key on the current level (level 13) to access lv14 without requiring a password.

### Command:   
 
```bash
ssh -i
```
It specifies the identity file (private key) to use for authentication.  
 
### Purpose:  
Use the file that contains the key in order to enter the target server.  

### Usage:  
```bash
ssh -i './private_key.txt' bandit14@bandit.labs.overthewire.org -p 2220
```  
  
![otw-login-com](/otw-login.png 'command')  

## 2 - Challenges I Encountered

I was confused when I first saw 'no password needed to enter the next level' I soon understood this after a quick research and know more about the 'ssh' command.  
 
## Quick Reflection

For now I can properly use the ssh command and utilize it to complete the incoming levels.  
> I cleared this level by myself one month ago.
