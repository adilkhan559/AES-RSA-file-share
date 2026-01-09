# Secure Backup (AES-GCM + RSA-OAEP + RSA-PSS)

This project is a command-line tool that creates an **encrypted backup** of a file or folder.
It uses a hybrid cryptographic design:

- **AES-256-GCM** encrypts file contents (confidentiality + tamper detection).
- **RSA-OAEP (SHA-256)** wraps the AES key for each authorised recipient (secure key sharing).
- **RSA-PSS (SHA-256)** signs the manifest (authenticity + manifest integrity).
- **SHA-256** hashes ciphertext files to support fast verification without decrypting.

The tool supports **two different users with separate keys** (e.g., Alice and Bob) and allows both to restore if they were included as recipients.

---

## Requirements

- Python 3.11+ recommended
- Packages: `cryptography` (installed via `requirements.txt`)

---

## Setup

### 1) Create and activate a virtual environment (Windows PowerShell)

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1