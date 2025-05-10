---
title: "Behind Fake Lies Secret"
date: 2025-05-09 16:00:00 +0500
categories: [CTF]
tags: [Forensics,Easy]
mermaid: true
description: A writeup of an easy packet inspection challange.
---
# 🕵️‍♂️ Behind Fake Lies Secret – Network Traffic CTF Challenge

## 📝 Task  
You’re given a pcap file that seems like normal network traffic, but there’s something secret hidden behind it. Your job is to expose the secret.

### Flag format:
```
SSH{xxx_xxxxx_xxx_xxxxxx_xxxxxxxxxxxxx}
```

---

## 💡 Solution Overview

### Step 1: Open the pcap File

- Rename the file to `capfile` (or any name you prefer).
- Open the pcap file using Wireshark:
  ```bash
  wireshark -r <filename>
  ```

   ![Step 1: Open pcap](assets/img/secretcommunication1.png)  
   ![Step 2: Wireshark Output](assets/img/secretcommunication2.png)

---

### Step 2: Inspect Suspicious Protocols

- Search for **HTTP** packets, which may contain hidden data:
  ![Step 3: Search HTTP](assets/img/secretcommunication3.png)

- Skim through the captured data to find a suspicious file, `sus1.png`.

  ![Step 4: Find Sus1](assets/img/secretcommunication4.png)

---

### Step 3: Follow the HTTP Stream

- Right-click on `sus1.png`, then select **Follow → HTTP Stream**.
  
  ![Step 5: Follow HTTP Stream](assets/img/secretcommunication5.png)

- Inspect the HTTP stream. You’ll see part of the flag:  
  ```
  SSH{y0u_f0und_
  ```

  ![Step 6: Partial Flag](assets/img/secretcommunication6.png)

---

### Step 4: Find the Complete Flag

#### Method 1: Searching for More PNG Files

- Use **Find** to search for “SSH”.
  
  ![Step 7: Use Find](assets/img/secretcommunication7.png)

- Continue scrolling and locate the next `sus2.png`.

  ![Step 8: Find Sus2](assets/img/secretcommunication9.png)

- Follow the HTTP stream for `sus2.png` and you’ll uncover the full flag:

  ![Step 9: Full Flag](assets/img/secretcommunication12.png)

  **Flag**:  
  ```
  SSH{y0u_f0und_7he_s3cret_c0mmunicati0n}
  ```

#### Method 2: Export Objects and Decode

- Start by exporting the HTTP objects:
  - Click **File → Export Objects → HTTP**.
  
  ![Step 10: Export HTTP](assets/img/secretcommunication14.png)

- Save and extract the files you get.
  
  ![Step 11: Extracted Files](assets/img/secretcommunication16.png)

- Analyze the two PNG files using the **strings** command:
  
  ```bash
  strings <image_file>
  ```

  - Apply `strings` on both files, and combine the output to get the flag:
  
  ![Step 12: Combine PNG Data](assets/img/secretcommunication19.png)

  **Flag**:  
  ```
  SSH{y0u_f0und_7he_s3cret_c0mmunicati0n}
  ```

---

## 🚩 Final Flag  
**SSH{y0u_f0und_7he_s3cret_c0mmunicati0n}**

---

## 💡 Conclusion  
Great job! You’ve uncovered the hidden message within the network traffic. If you read all the way here, you’re surely into cyber 😊
