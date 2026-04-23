# Day 02 – Create a Temporary User with Expiry Date (Linux User Management)

## 📌 Objective

Create a temporary user account for a developer who requires access to the **Nautilus project** for a limited duration.
The user must be created on the specified server with an account expiration date.

This task demonstrates basic **Linux user management**, specifically creating users with expiration policies — a common requirement in enterprise environments for contractors, temporary staff, or project-based access.

---

## 🧾 Task Requirements

* **User:** `john`
* **Server:** Application Server 2
* **Hostname:** `stapp02`
* **Expiration Date:** `2027-03-28`
* **Username must be lowercase**

---

## 🖥️ Infrastructure Details

| Server Name          | Hostname | User  | Purpose                      |
| -------------------- | -------- | ----- | ---------------------------- |
| Application Server 2 | stapp02  | steve | Hosts Nautilus Application 2 |

---

## 🔐 Step 1 – Connect to the Target Server

From the `jump-host`, connect to **App Server 2** using SSH:

```bash
ssh steve@stapp02
```

---

## 👤 Step 2 – Create the User with Expiry Date

Use the `useradd` command with the `-e` option to set the account expiration date.

```bash
sudo useradd -e 2027-03-28 john
```

### Explanation

* `useradd` → Creates a new user
* `-e` → Sets the account expiration date
* `2027-03-28` → Expiration date (YYYY-MM-DD format)
* `john` → Username

---

## 🔍 Step 3 – Verify the User Expiration Date

Check the account details using:

```bash
sudo chage -l john
```

Expected output:

```text
Account expires : Mar 28, 2027
```

---

## 🧠 Key Concepts Learned

* Linux user management
* Creating temporary users
* Setting account expiration policies
* Using `useradd`
* Using `chage` to verify user settings
* SSH access to remote servers

---

## 🛠️ Command Summary

```bash
ssh steve@stapp02
sudo useradd -e 2027-03-28 john
sudo chage -l john
```

---

## 📚 Real-World Relevance

Temporary user accounts with expiration dates are commonly used for:

* Contractors
* Interns
* Vendors
* Project-based access
* Security compliance (ISO 27001 / SOC 2)

This ensures automatic access removal without manual intervention.

---

## ✅ Status

Completed successfully.
