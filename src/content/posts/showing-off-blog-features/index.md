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
## Theming

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

---

## STEP 2 — 置換文字 | Shift the Characters

觀察字串中的英文字母與數字，將兩者分別向前位移 7 個位置。
e.g. 'a' ---> 'h' 'b' ---> 'i'

解密後得到：

```text
666c61677b696b6e65776974776173796f757279616e73756e677d0a
```
<!--圖片格式
![Pixel art of a tree](./PixelatedGreenTreeSide.png 'Pixel art renders poorly without proper CSS')
-->
---



## Admonitions

```md title="Admonition example in markdown"
:::note
testing123
:::
```

:::note
testing123
:::

:::tip
testing123
:::

:::important
testing123
:::

:::caution
testing123
:::

:::warning
testing123
:::

## Character Chats

```md title="Custom character chat" wrap
:::duck
**Did you know?** You can easily create custom character chats for your blog with MultiTerm!
:::
```

:::duck
**Did you know?** You can easily create custom character chats for your blog with MultiTerm!
:::

### Adding Your Own

To add your own character, first add an image file to the top-level `/public` directory in your cloned MultiTerm repo. Astro cannot automatically optimize image assets from markdown plugins, so make sure to compress the image to a web-friendly size (<100kb).

I recommend Google's free [Squoosh](https://squoosh.app) web app for creating super small webp files. The characters here have been resized to 300 pixels wide and exported to webp with 75% quality using Squoosh.

After you've added your image, update the `characters` option in `site.config.ts` with your newly added image file and restart the development server.

### Character Conversations

When there are multiple character chats in a row, the order of the chat image and chat bubble reverses to give the chat more of a back-and-forth appearance.

```md title="Sequential character chats"
:::owl
This is a cool feature!
:::

:::unicorn
I agree!
:::
```

:::owl
This is a cool feature!
:::

:::unicorn
I agree!
:::

You can specify the alignment (`left` or `right`) to override the default `left, right, left, ...` ordering.

```md wrap title="Character chats with specific alignment"
:::unicorn{align="right"}
Over here, to the right!
:::
```

:::unicorn{align="right"}
Over here, to the right!
:::

## GitHub Cards

GitHub overview cards heavily inspired by [Astro Cactus](https://github.com/chrismwilliams/astro-theme-cactus).

```md title="GitHub repo card example in markdown"
::github{repo="stelcodes/multiterm-astro"}
```

::github{repo="stelcodes/multiterm-astro"}

```md wrap=true title="GitHub user card example in markdown"
::github{user="withastro"}
```

::github{user="withastro"}

## Emoji :star_struck:

Emojis can be added in markdown by including a literal emoji character or a GitHub shortcode. You can browse an unofficial database [here](https://emojibase.dev/emojis?shortcodePresets=github).

```md title="Example markdown with GitHub emoji shortcodes"
Good morning! :sleeping: :coffee: :pancakes:
```

Good morning! :sleeping: :coffee: :pancakes:

> All emojis \(both literal and shortcoded\) are made more accessible by wrapping them in a `span` tag like this:
>
> ```html
> <span role="img" aria-label="coffee">☕️</span>
> ```
>
> At the time of writing, [emoji v16](https://emojipedia.org/emoji-16.0) is not supported yet. These emojis can be included literally but they do not have shortcodes and will not be wrapped.

## LaTeX/KaTeX Math Support

You can also display inline math via [remark-math and rehype-katex](https://github.com/remarkjs/remark-math).

```txt title="Rendering inline math with KaTeX"
Make those equations pretty! $ \frac{a}{b} \cdot b = a $
```

Make those equations pretty! $ \frac{a}{b} \cdot b = a $

Check out the [KaTeX docs](https://katex.org/docs/supported) to learn about the syntax.

```md title="Rendering a block of KaTeX" wrap
$$
a + ar + ar^2 + ar^3 + \dots + ar^{n-1} = \displaystyle\sum_{k=0}^{n - 1}ar^k = a \bigg(\dfrac{1 - r^n}{1 -r}\bigg)
$$
```

$$
a + ar + ar^2 + ar^3 + \dots + ar^{n-1} = \displaystyle\sum_{k=0}^{n - 1}ar^k = a \bigg(\dfrac{1 - r^n}{1 -r}\bigg)
$$

## HTML Elements

<button>A Button</button>

### Fieldset with Inputs

<fieldset>
    <input type="text" placeholder="Type something"><br>
    <input type="number" placeholder="Insert number"><br>
    <input type="text" value="Input value"><br>
    <select>
        <option value="1">Option 1</option>
        <option value="2">Option 2</option>
        <option value="3">Option 3</option>
    </select><br>
    <textarea placeholder="Insert a comment..."></textarea><br>
    <label><input type="checkbox"> I understand<br></label>
    <button type="submi">Submit</button>
</fieldset>

### Form with Labels

<form>
<label>
    <input type="radio" name="fruit" value="apple">
    Apple
</label><br>

<label>
    <input type="radio" name="fruit" value="banana">
    Banana
</label><br>

<label>
    <input type="radio" name="fruit" value="orange">
    Orange
</label><br>

<label>
    <input type="radio" name="fruit" value="grape">
    Grape
</label><br>

<label>
    <input type="checkbox" name="terms" value="agree">
    I agree to the terms and conditions
</label><br>
