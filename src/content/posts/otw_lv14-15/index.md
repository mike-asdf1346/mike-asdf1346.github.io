---
title: 'Over-The-Wire lv13-14 Learning Journal'
published: 2026-10-26
draft: false
description: '這是一篇無聊的學習筆記(x。第一次用我說明一下。我會用來紀錄我在OverTheWire遇到比較印象深刻的題目或是困難，還有我是如何理解其中的出題思路。在這篇中我會整理我遇到一個新觀念時是如何解決的。'
tags: ['OTW', 'Linux', 'Cybersecurity', 'Journal']
---

## Overview

平台: OverTheWire  
戰爭遊戲: Bandit  
此篇Lv: Level 13 → Level 14  
狀態: Complete  
此篇是否含有flag: No  

![otw img](/otw-image.png 'goal')

## Learning Objectives

In this level, I must learned how to access OTW server level without entering passwords by using the SSH keys.

here's the commands I'm going to use:
```bash
cat
```

```bash
la
```

```bash
ssh
```

```bash
chmod
```  
 
## 1 - New Concepts

Using the given private key on the current level (level 13) to access the lv14 without password required.

### Command:   
```bash
ssh -i
```

### Purpose:  
Use the file I want in order to enter the target server.  

### Usage:  
```bash
ssh -i './private_key.txt' bandit14@bandit.labs.overthewire.org -p 2220
```  
  
![otw-login-com](/otw-login.png 'Actual command')  

## 2 - Challenges I Encountered

I'm confused when I first seeing 'no password needed to enter the next level' but soon I understand this after a quick research and know more about the 'ssh' command.  
 
## Quick Reflection

For now I can properly use the ssh command and utilize it to complete the incoming levels.  
this level has cleared since 1 monthe ago by myself.
