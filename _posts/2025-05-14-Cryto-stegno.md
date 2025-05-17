---

title: "Stegnography & Cipher Challenge"
date: 2025-05-15 16:00:00 +0500
categories: [CTF, Cryptography]
tags: [Forensics, Cryptography]
mermaid: true
description: A writeup of an a mix challange of stegnography and cryptography
---

## 🕵️‍♂️ CTF Challenge Writeup: Steganalysis & Decryption

We are given an image and a file, and our task is to decrypt the hidden message within them.

![Initial Image](assets/img/cryy1.png)

![File Analysis Output](assets/img/cryy2.png)


---

### 🔍 Step 1: Metadata and Basic Analysis

We start by checking the EXIF data and running string extraction on the image file.
❌ However, nothing useful is found.

🔧 We then run the `file` command and notice that there is **embedded text** in the image. So, we try to extract it using `steghide`:

```bash
steghide extract -sf path_to_file
```
📸 **Output:**  
📄 **File:**  
![File Analysis Output](assets/img/cryy3.png)



But it asks for a passphrase, which we don't have. So we try brute-forcing with `stegseek`, which uses a wordlist:

```bash
stegseek path_of_image path_of_wordlist
```

🚫 **Result:** Password not found —  
![Stegseek Failure](assets/img/cryy4.png)


---

### 🧩 Step 2: Decrypting the Encrypted Text File

Next, we decrypt `hellworld.txt`, which contains:

```
NEMyNDxFOTpEQTJEREhAQzU6N0pARjQyPw==
```

🔐 This looks like a **base64**-encoded string. Decoding it in CyberChef gives us:

```
4C24<E9:DA2DDH@C5:7J@F42?
```

Still encrypted? Yes. We tried other ciphers, but base64 gave the **best output**.

---

### 🧠 Step 3: Cipher Identification

Using dCode's Cipher Identifier:

🖼️ ![Cipher Identifier](assets/img/cryy5.png)

💡 **Best match:** `ROT-47`

We decode it using ROT-47 and get:

🖼️ ![ROT-47 Decryption](assets/img/cryy6.png)

✅ **Decoded phrase:** `crackthispasswordifyoucan`

> 📝 NOTE: Default key is 47. If unknown, ROT brute force (Python/online) can help.

We use this as the **steghide passphrase** and try again. This time, it works!

📦 **Output:** ![Steghide Extracted](assets/img/cryy7.png)

---

### 🧾 Step 4: Extracted File Analysis

The `hash.txt` file contains:

```
ho_dootq_xryq_xyaw
```

🔍 This looks encrypted. Remove underscores (`_`) before using dCode's cipher identifier.

💬 It suggests: **Affine Cipher** 🔢

Affine Cipher is commonly used in CTFs, but we don’t know `A` and `B`. So, we use dCode's brute force tool.

🖼️ ![Affine Cipher Output](assets/img/cryy9.png)

✅ **Decryption Result:** `A=7, B=20  =>  no_fools_this_time`

---

### 🏁 Final Flag

```
🚩 SSH{no_fools_this_time}
```

---


