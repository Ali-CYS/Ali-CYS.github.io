---
title: "Easy Stegnography Challange"
date: 2025-05-05 16:00:00 +0500
categories: [CTF,stegnography]
tags: [stegnography]
mermaid: true
description: A writeup of an easy stegnography challange.
---

# 🕵️‍♂️ Steganography Challenge – *"See It Was Not Difficult"*

## 📝 Task  
Find the hidden flag in the image:  
![Step 1](assets/img/seeitwasnotdifficult1.png)

---

## 🔍 Observation  
- The image is in black and white.  
- The challenge description hinted at something related to **brightness/darkness** levels.

---

## 🛠️ Step-by-Step Solution  

1. Go to [https://www.gifgit.com](https://www.gifgit.com) and upload the image:  
   `seeitwasnotdifficult1.png`

2. Increase the **brightness to the maximum level**.

3. A hidden message appears in the image:  
   ![Step 2](assets/img/seeitwasnotdifficult2.png)

4. On the bottom-right side, you’ll notice a **triangle with dot cipher** symbol.

5. To identify this symbol, use an online decoder like:  
   [List of Symbols Cipher – Online Decoder, Translator](https://www.dcode.fr)
 ![Searching](assets/img/seeitwasnotdifficult3.png)
6. After some searching, we find the cipher name:  
   **Templars Cipher**

7. Decoding reveals the final flag:  
   ![Final](assets/img/seeitwasnotdifficult.png)

---

## 🚩 Final Flag  
**SSH{SEEITWASNOTDIFFICULT}**
