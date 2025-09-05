# Local-Password-Manager-

A simple local password manager written in Python and MariaDB.  
It uses **PBKDF2** to derive a 256-bit key from a **MASTER PASSWORD** and **DEVICE SECRET**, then applies **AES-256** for encrypting/decrypting your stored passwords.  

This tool is intended for personal use on a single machine and provides a secure way to manage and retrieve credentials.  

---

## Features
- AES-256 encryption with PBKDF2 key derivation  
- Local MariaDB database for secure storage  
- Add, retrieve, and generate strong passwords  
- Clipboard copy option for convenience  
- Command-line interface  

---

## Requirements
- **Python 3.8+**  
- **pip** (Python package manager)  
- **MariaDB** database server  

---

## Installation

### Step 1: Install Python and pip
```bash
sudo apt update
sudo apt install python3 python3-pip python3-venv -y
