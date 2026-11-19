# 🔓 Password Cracking Report (Week 3)

**Pentester Name:** Rejoyce Mosesane
**Program/Batch:** Networkwalks Cybersecurity Internship 
**Date:** November 2026
**Modules Completed:** W3-PM1 (John the Ripper), W3-PM2 (Networkwalks Tools)

## 1. Executive Summary
This report documents the password recovery process of encrypted PDF files. The objective was to demonstrate how password hashes are extracted and how dictionary attacks are utilized to crack them. Two separate toolsets were used: the Networkwalks web-based tools, and the industry-standard John the Ripper (Johnny GUI) using a massive real-world wordlist. 

## 2. Methodology & Tools Used
*   **Hash Extraction:** Networkwalks Hash Calculator
*   **Dictionary Attack (Web):** Networkwalks Password Cracker (100-word dictionary)
*   **Dictionary Attack (Desktop):** Johnny (John the Ripper GUI) utilizing `rockyou.txt` (14+ million passwords)

---

## 3. Findings & Execution

### 3.1 Hash Extraction
Using the Networkwalks Hash Calculator, the PDF was uploaded, and the internal password hash was successfully extracted. 
*   **Format:** `$pdf$4*4*128...`
*   **Risk:** If an attacker steals a password-protected document, the password itself is not stored. Only the hash is stored. However, as demonstrated below, hashes can be cracked if weak passwords are used.
<img width="547" height="467" alt="Screenshot 2026-11-18 181412" src="https://github.com/user-attachments/assets/b1721f98-d213-4cb5-96fd-61a592244b0e" />


### 3.2 Web Tool Attempt (Module 2)
The extracted hash was pasted into the Networkwalks Password Cracker. The tool executed a dictionary attack using its built-in list of 100 common passwords. 
*   **Result:** Access Denied. The password was not in this small list, proving that even slightly complex passwords can defeat basic dictionary attacks.
<img width="521" height="462" alt="Screenshot 2026-11-18 181551" src="https://github.com/user-attachments/assets/dc036ede-33ed-4d3a-a38c-9644770e2492" />


### 3.3 Industry Tool Attempt (Module 1)
To recover the password, the hash was saved to a text file and loaded into Johnny. A dictionary attack was launched using the legendary `rockyou.txt` wordlist (containing over 14 million breached passwords).
*   **Result:** Success. The tool successfully matched the hash and cracked the password: **`good-luck`**.
<img width="959" height="564" alt="Screenshot 2026-11-19 114454" src="https://github.com/user-attachments/assets/315dc498-b865-48f6-b8e5-3aa85cf66840" />


### 3.4 Main Flag Captured
Using the cracked password `good-luck`, the primary PDF file was successfully decrypted, revealing the captured flag.
*   **Flag:** `nw{cybersecurity_flag_captured_2608}`
<img width="305" height="425" alt="Screenshot 2026-11-19 114639" src="https://github.com/user-attachments/assets/4901e4a6-ecf7-4043-9556-63eda2ca2e80" />


### 3.5 Extra Credit: Additional Files Cracked (Module 2)
Upon exploring the provided lab resources, I identified two additional encrypted PDF files and successfully cracked them using the Networkwalks Password Cracker web tool. 
*   **Finding:** Unlike the main PDF, the passwords for these files were simple enough to be present in the basic 100-word dictionary provided by the web tool. This reinforces the danger of using common dictionary words for security.
*   **Flag 1 (Red Lock):** `nw{networkwalks_persistence_jr_270521}`
*   **Flag 2 (Pink Shirt):** `nw{networkwalks_flag_260821_1}`
*   <img width="302" height="422" alt="Screenshot 2026-11-19 115610" src="https://github.com/user-attachments/assets/e10c04ec-b9c5-4b9a-ab49-bb0192dff7d3" />

<img width="320" height="416" alt="Screenshot 2026-11-19 115743" src="https://github.com/user-attachments/assets/f5480af9-e1ff-4bfc-942b-192293288966" />


---

## 4. Conclusion & Recommendations
This lab demonstrated the importance of strong, unique passwords. While the password `good-luck` was able to defeat a basic 100-word script, it was cracked almost instantly by a real-world tool using a massive dictionary. Other files with even simpler passwords were cracked instantly by the basic web tool.

**Recommendations for protecting sensitive files:**
1.  **Never use dictionary words or common phrases:** Even with hyphens, words like `good-luck` are easily cracked. Simple words are instantly cracked.
2.  **Use Passphrases:** Combine random, unrelated words (e.g., `BlueHorse-Battery-Staple`) to increase entropy.
3.  **Use Password Managers:** Generate and store highly complex, randomized passwords (e.g., `x7#qL9!mP2$v`).
