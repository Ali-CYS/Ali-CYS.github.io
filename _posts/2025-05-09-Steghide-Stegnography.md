---
title: "Easy Stegnography Challange"
date: 2025-05-09 16:00:00 +0500
categories: [CTF]
tags: [stegnography,Easy]
mermaid: true
description: A writeup of an easy stegnography challange.
---
# 🕵️‍♀️ Steganography Challenge – *"Y@u_C4ugH7_The_Tr41n"*

## 📝 Task  
Find the hidden flag in the image:  
![Initial Image](assets/img/y@u_C4ugH7_The_Tr41n1.png)

---

## 🔍 Investigation Steps

1. Tried adjusting **brightness levels** – no visible text or clues found.

2. Attempted to use `steghide`, but it **required a passphrase** which we didn't know.  
   ![Steghide Attempt](assets/img/y@u_C4ugH7_The_Tr41n12.png)

3. Switched to **Stegseek**, which tries passwords from the `rockyou.txt` wordlist to extract hidden content.

---

## 🛠️ Stegseek Usage

```bash
stegseek /path/to/image.jpg /usr/share/wordlists/rockyou.txt
```

*(Replace `/path/to/image.jpg` with the actual location of your image)*

- Stegseek **found an embedded file** and even revealed the passphrase (which can now be used with `steghide` too if needed).
- The extracted file was saved as: `1.jpg.out`  
  ![Extracted Image](assets/img/y@u_C4ugH7_The_Tr41n3.png)

4. The output contained this text:  
   ```
   SHyuCuH_h_r1}S{@_4g7TeT4n
   ```

---

## 🔓 Decoding the Message

- The text didn’t look like a normal flag – possibly encoded.
- Used this tool to analyze the cipher:  
  [Decrypt a Message - Cipher Identifier](https://www.dcode.fr/cipher-identifier)  
  ![Cipher Tool](assets/img/y@u_C4ugH7_The_Tr41n5.png)

- The tool identified it as a **Rail Fence Cipher**.

---

## 🧠 Decoding with CyberChef

- Used [CyberChef](https://gchq.github.io/CyberChef/) to decode the text using the **Rail Fence** cipher.
- Key used: **2**  
  ![Decoded Result](assets/img/y@u_C4ugH7_The_Tr41n6.png)

---

## 🚩 Final Flag  
**SSH{y@u_C4ugH7_The_Tr41n}**

---

## 💡 Notes
- Key used for Rail Fence here was `2`.
- If the key isn’t known, online tools or brute force attempts with small key ranges can be effective.
