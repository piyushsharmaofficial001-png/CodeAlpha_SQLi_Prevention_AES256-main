# 🛡️ AES-256 & SQLi Protection Vault

A full-stack cybersecurity sandbox built with **Python (Flask)** and **SQLite** that demonstrates two essential web security defenses: **AES-256-CBC encryption** for data at rest and **SQL Injection (SQLi) neutralization** using parameterized queries[cite: 1, 2].

---

## 🔍 Overview

Modern web applications face two major threats: **unauthorized database access (SQL Injection)** and **data exposure if a database is compromised**. This project demonstrates how to mitigate both:

1. **Cryptographic Storage (AES-256-CBC):** User secrets are padded (PKCS#7) and encrypted using a 256-bit key with a unique random Initialization Vector (`IV`) for every record before being saved in SQLite as `Base64(IV):Base64(Ciphertext)`.
2. **Parameterized Queries & Attack Detection:** User lookups use prepared statements (`?` placeholders) so malicious SQL payloads are treated strictly as literal strings rather than executable commands, while flagging common SQLi patterns in real time.

---

## ✨ Features

- **AES-256-CBC Encryption & Decryption** using `PyCryptodome` with per-record random `IV` generation.
- **SQL Injection Defense Sandbox** that safely neutralizes payloads like `admin' OR '1'='1` or `' --`[cite: 1, 2].
- **Real-Time SQLi Pattern Detection** with visual alert badges (`Attack Intercepted` vs. `Clean Query`)[cite: 1, 2].
- **Ciphertext & Plaintext Inspection** to verify how data is stored in `secure_users.db` versus how it is decrypted on authorized access[cite: 1, 2].
- **Responsive Glassmorphic UI** built with HTML5, CSS3, and Fetch API.

---

## 📁 Project Structure

```text
├── app.py               # Flask backend, AES-256 encryption/decryption & SQLite routes
├── templates/
│   └── index.html       # Frontend UI for encryption & SQLi testing sandbox
├── secure_users.db      # Auto-generated SQLite database (created on first run)
└── README.md            # Project documentation
