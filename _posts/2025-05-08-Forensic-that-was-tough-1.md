---
title: "Zip Maze"
date: 2025-05-08 16:00:00 +0500
categories: [CTF]
tags: [Forensics,Easy]
mermaid: true
description: A writeup of an easy forensics challange.
---
# 🧩 ZIP Maze – Forensics CTF Challenge

## 📝 Task  
You're given a ZIP file. The goal is to find the **flag** hidden somewhere inside it.

---

## 📂 Step-by-Step Extraction

1. **Extract the first ZIP** – it contains a text file and another ZIP inside:  
   ![Step 1](assets/img/TrustMeYouAreProInForensicsCTFchallenges1.png)

2. Inside the `flag.txt` file, we see:
   ```
   SSH{f4k3_f14g_f0r_t3st1ng}
   ```
   ⚠️ This is a **fake flag** (as hinted), but always test each flag just in case it's real.

---

## 🌀 Keep Extracting...

3. Extract the next ZIP. You get another `flag.txt` file and yet another ZIP.  
   ![Step 2](assets/img/TrustMeYouAreProInForensicsCTFchallenges3.png)

4. The next file has:  
   ![Encoded Fragment](assets/img/TrustMeYouAreProInForensicsCTFchallenges4.png)  
   ```
   VHJ1
   ```

---

## 🔁 Repeating the Process

- Continue extracting the nested ZIPs.
- Each one contains a piece of base64-encoded text.
- Keep copying and adding the pieces together.

In the **final ZIP**, the entire encoded string looks like this:

```
VHJ1c3RNZVlvdUFyZVByb0luRm9yZW5zaWNzQ1RGY2hhbGxlbmdlcw==
```

---

## 🔓 Decoding the Message

- Use [CyberChef](https://gchq.github.io/CyberChef/) or any base64 decoder.
- Decoding the above gives:

```
TrustMeYouAreProInForensicsCTFchallenges
```

---

## 🔐 Final Password-Protected File

- The **last ZIP file** contains a **password-protected file**:  
  ![Password Protected](assets/img/TrustMeYouAreProInForensicsCTFchallenges5.png)

- Use the decoded text as the password:  
  ```
  TrustMeYouAreProInForensicsCTFchallenges
  ```

- Successfully opening it reveals the final flag:  
  ![Flag](assets/img/TrustMeYouAreProInForensicsCTFchallenges6.png)

---

## 🚩 Final Flag  
**SSH{7hat_w4s_7h0u9h}**

---
