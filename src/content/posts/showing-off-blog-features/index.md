---
title: 'IG-spot-the-weak CTF Write-Up'
published: 2026-10-26
draft: false
tags: ['CTF', 'Crypto', 'Cybersecurity']
toc: true
coverImage:
  src: './cover.jpg'
  alt: 'Sorry, the image is not shown.'
---

我在IG帳號中藏入了一個加密字串，你的目標是找出帳號裡洩漏出的**data**，並觀察字串中的規律，加以破解取得**Flag**。
> 🏁Flag格式：flag{example}
## 開場 | Intro

> ⚠️WARNING: THIS WRITE-UP CONTAINS FLAG!!⚠️

以下為本題的完整解題流程。

1. 本題的答案藏在一個IG帳號中的三個貼文內。
2. 其中, 有一個貼文洩漏出了這一段文字：
```text
[  0.034100] data: 333j38344i363i3l32443641443840463m424946383l40423l344k7h
```
3. 找到之後就可以開始解題了。

---

## STEP 1 — 辨認加密字串 | Identify the Encrypted Code

首先，找出原帳號簡介中所提供的秘密帳號並找出裡面提供的加密字串：

```text
333j38344i363i3l32443641443840463m424946383l40423l344k7h
```
![IMG 1](./IMG_5257.jpg '找出帳號')

![IMG 2](./IMG_5258.png '總共有三篇奇怪的貼文')

![IMG 3](./IMG_5259.jpg '仔細找會發現其中一個貼文出現了"data"字樣')

---

## STEP 2 — 置換文字 | Shift the Characters

觀察字串中的英文字母與數字，將兩者分別向前位移 7 個位置。
> e.g. 'a' ---> 'h' 'b' ---> 'i'

解密後得到：

```text
666c61677b696b6e65776974776173796f757279616e73756e677d0a
```
<!--圖片格式
![Pixel art of a tree](./PixelatedGreenTreeSide.png 'Pixel art renders poorly without proper CSS')
-->
---


## STEP 3 — 觀察並利用xxd指令 Inspect and xxd Decode

觀察剛剛的字串可以發現是由十六進制格式組成的。 
> '66'--->'f' '6c'--->'l'

接下來，可使用 Linux 指令處理解密後的內容。
把結果echo出來並利用導管連接xxd指令：

```bash
echo '666c61677b696b6e65776974776173796f757279616e73756e677d0a' | xxd -r -p
```

利用網路上的工具轉換也行。

**指令break down**

- `cat`：讀取檔案內容
- `xxd -r`：將十六進制格式轉回二進制格式
- `xxd -p`：輸出純十六進制格式

## Step 4 — 取得FLAG Retrieve the Flag

完成上述步驟後，即可得到最終 Flag：

:checkered_flag: **Flag**

```text
flag{iknewitwasyouryansung}
```
![IMG of flag](./IMG_9487.png '指令結果')

## 總結 | Conclusion

本題結合了資料比對、字元位移與簡易十六進位解碼。

解題的關鍵在於：
1. 找出貼文內洩漏機密(data:)的字串。
1. 找出正確的字元位移規則。
2. 將解密後的字串視為十六進位資料。
3. 利用 Linux 指令還原資料。

## That's all!
![IMG footer](./pew.gif '')

:closed_lock_with_key: 我也不知道我為什麼要做這個，總之這是我的第一篇Write-Up然後如果有誤請馬上連繫我。最後，謝謝你的閱覽!
