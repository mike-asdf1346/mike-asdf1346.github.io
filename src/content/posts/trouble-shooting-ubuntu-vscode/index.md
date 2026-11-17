---
title: 'Ubuntu-Trouble-shoot: p10k 跟 vscode 的相容性問題'
published: 2026-11-17
draft: false
tags: ['Shell', 'Ubuntu', 'Trouble-shoot', 'Journal', 'Vscode']
toc: true
coverImage:
  src: './firefox1.webp'
  alt: 'Sorry, the image is not shown.'
description: 'Vscode 在 Ubuntu 26.04.1 LTS 版本中使用 Zsh 的輸出問題'
---   
# 前言
:::note
標題圖片的作者(Title image credits to)：[久蒼穹](https://www.pixiv.net/en/artworks/98684552) 
:::  
哇，這個問題困擾我有一段時間了，總之呢，就是我的 vscode 不知道為什麼一次會輸出兩次 outputs 甚至還有錯誤，反正就是這樣。喔對了，最近有空的話我會試開留言區，請各位再多加留意！感恩！   
~~請忽略我vscode的字體~~
## 問題描述 & 我的裝置
問題：   
按下 'run python file' 時連續輸出兩次，第一次正常但沒東西，第二次正常輸出但出現錯誤訊息 'SIGINT(2)'，這個通常是因為觸發組合鍵`Ctrl + C`發送的一個 Linux/Unix 中斷程式執行的非同步訊號，全名是 Signal Interrupt 編號為 2。 
![my-error](./error-out.png)

Ubuntu 版本：
![version-ubun](./version.png)
其餘的：
| 內容   | 設置    |
| ----- | ------- |
| Shell | Zsh 5.9 |
| Shell framework | Oh-My-Zsh |
| Shell theme | p10k |
| Terminal | Alacritty |
| Vscode editor | 1.146.0 x64 |
| Python | 3.14.4 |
| Python interpreter | /usr/bin/python3 |

---

## 故障排除流程
我試了一些比較有可能會造成這問題的方法
### 直接終端機輸入   
試過直接手動執行，輸入`python3 -c 'print('test')'`是正常的，完全沒有錯誤出現。
### Vscode Extension
逐一關閉擴充插件測試，問題還在。
### 關閉 Python Environment
關掉 Python Environment ＆ terminal.env 也沒效。
### 用 Python sys module 測試
試試看 Import `sys` 模組：
```python
import sys

print('hello from py!')
print('python executable:', sys.executable)
print('python version:', sys.version)
```
輸出：
![module-test](./module-test.png)
看起來還是一樣沒變。
### 查看 '~/.p10k.zsh` 的設定
用 `vim` 或 `nano` 查看 `~./.p10k.zsh` 的設置。去 p10k `status: exit code of the last command`的 section 可以找到：
![setting-p10k](./settings.png)
ㄜ，看起來也沒什麼太大的問題。
### 關掉終端機 shell 整合
之後我跑去 `User setting (JSON)`把終端機整合關掉。   
`"terminal.integrated.shellIntergration.enabled": false,`
變正常了：
![result](./result.png)
## 總結
試了很多遍我在想有可能是因為 VS Code 終端機整合跟 Zsh 環境不相容或是有衝突才造成這個奇怪的錯誤訊息。     
最後：
- Python 3.14.4 正常
- `/usr/bin/python3`是正確的路徑
- 關掉 Python Env 沒用
- 關掉終端機整合就成功了
## 結語
我查了一下網路但還是找不到跟我有一樣問題的輸出，或許有，但大部分都是圍繞在關閉 Python Env 上。不過目前問題是解決了，如果後續有找出更好的方案，我會更新這篇文章，然後內文有誤的話請 DM 我，謝謝！ :D 
