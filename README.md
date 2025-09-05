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

Step 2: Create a Virtual Environment

# Navigate to the project directory
cd ~/Password-Manager/python-password-manager

# Create virtual environment
python3 -m venv venv

# Activate it
source venv/bin/activate

Step 3: Install Python Dependencies

pip install -r requirements.txt

Step 4: Install MariaDB

sudo apt update
sudo apt install mariadb-server mariadb-client -y

Start and enable MariaDB:

sudo systemctl start mariadb
sudo systemctl enable mariadb

Check status:

systemctl status mariadb

Step 5: Secure MariaDB

Run the security script:

sudo mysql_secure_installation

Recommended answers:

    Set root password: Yes

    Remove anonymous users: Yes

    Disallow remote root login: Yes

    Remove test database: Yes

    Reload privilege tables: Yes

Step 6: Create Database and User

Log in as root:

sudo mysql -u root -p

Inside the MariaDB shell:

CREATE DATABASE password_manager;
CREATE USER 'pm'@'localhost' IDENTIFIED BY 'password';
GRANT ALL PRIVILEGES ON password_manager.* TO 'pm'@'localhost';
FLUSH PRIVILEGES;
EXIT;

Test user login:

mysql -u pm -p password_manager

Configuration

Before first use, configure the password manager with a MASTER PASSWORD.
Create Configuration

python config.py make

Delete Configuration

python config.py delete

Recreate Configuration

python config.py remake

Usage
Help

python pm.py -h

Add Entry

python pm.py add -s mysite -u mysite.com -e hello@email.com -l myusername

Retrieve Entries

All entries:

python pm.py extract

By site:

python pm.py e -s mysite

By site and username:

python pm.py e -s mysite -l myusername

Copy to clipboard:

python pm.py e -s mysite -l myusername --copy

Generate Password

python pm.py g --length 15

Running the Project

    Activate virtual environment:

source venv/bin/activate

Configure the password manager (only once):

python config.py make

Use the password manager:

    python pm.py add ...
    python pm.py extract ...
    python pm.py g ...

Summary

    Uses MariaDB as backend with AES-256 encryption

    Secure database user pm should be used

    Configuration required once via config.py make

    Passwords can be added, retrieved, or generated with pm.py
