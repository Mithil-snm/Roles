# # Bulk User Profile Creation – Wellytics Platform

A Jupyter Notebook to automate bulk creation of user profiles (Admin, Medical Officer, Doctor) on the Wellytics health platform via API.

---

## 🗂️ Supported Roles

- Admin
- Medical Officer
- Doctor

---

## 📁 CSV Format

Prepare a `.csv` file with the following columns:

| Column | Required | Description |
|--------|----------|-------------|
| `First Name` | ✅ | User's first name |
| `Last Name` | ✅ | User's last name |
| `Email Id` | ✅ | Email (also used as username) |
| `Contact Number` | ✅ | 10-digit mobile number |
| `Password` | ✅ | Initial password |
| `Organization Id` | ✅ | UUID of the organization |
| `Role` | ✅ | `Admin`, `Medical Officer`, or `Doctor` |
| `Registration ID` | Doctors only | Medical registration number |
| `Designation` | Doctors only | e.g., `Doctor` |
| `Speciality` | Doctors only | Must match a value from the platform |
| `Department` | Doctors only | Must match a value from the platform |

> **Note:** Speciality and Department values for doctors must exactly match the names configured in your platform instance.

---

## ⚙️ Setup

### Prerequisites

- Python 3.8+
- Jupyter Notebook or JupyterLab

### Install Dependencies

```bash
pip install pandas requests
```

---

## 🚀 Usage

1. **Clone the repo**
   ```bash
   git clone https://github.com/your-org/your-repo.git
   cd your-repo
   ```

2. **Open the notebook**
   ```bash
   jupyter notebook Role.ipynb
   ```

3. **Configure the environment** in Cell 2:
   ```python
   ENV = "STAGE"        # Options: DEV | STAGE | DEMO | PROD
   filepath = "users.csv"   # Path to your CSV file
   ```

4. **Run all cells** — the notebook will process each user and print live progress, then display a final summary.

---

## 🌐 Environments

| ENV | Base URL |
|-----|----------|
| `DEV` | `https://api-dev.platform.wellytics.health/auth/api` |
| `STAGE` / `DEMO` | `https://api-stage.platform.wellytics.health/auth/api` |
| `PROD` | `https://api.platform.wellytics.health/auth/api` |

---

## 📊 Output Summary

After processing, the notebook prints a breakdown like:

```
===== OVERALL SUMMARY =====
Total: 10
Success: 10
Failed: 0

===== ADMIN SUMMARY =====
ADMIN: 2 success, 0 failed

===== MO SUMMARY =====
MO: 4 success, 0 failed

===== DOCTOR SUMMARY =====
DOCTOR: 4 success, 0 failed
```

---


## 📌 Notes

- The `countryCode` is hardcoded to `+91` (India). Update it in the class methods if needed for other regions.
- If a user fails mid-flow, they are logged in the failed list — rerun after fixing the issue.
- Ensure the CSV has no extra spaces in column headers or values.

---

