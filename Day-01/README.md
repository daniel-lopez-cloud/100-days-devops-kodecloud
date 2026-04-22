# Day-01: Create a User with a Non-Interactive Shell on Application Server 2

## 🎯 Objective

Create a user named `ammar` with a **non-interactive shell** on **Application Server 2** as required by the backup agent tool specifications.

---

## 🧾 Infrastructure Details

| Server Name          | Hostname | User  | Purpose                      |
| -------------------- | -------- | ----- | ---------------------------- |
| Application Server 2 | stapp02  | steve | Hosts Nautilus Application 2 |

---

## 🛠️ Steps

### 1. Connect to Application Server 2

From the jump host, connect to the target server using SSH.

```bash
ssh steve@stapp02
```

---

### 2. Create the User with a Non-Interactive Shell

Execute the following command to create the user `ammar` with a non-interactive shell:

```bash
sudo useradd -s /sbin/nologin ammar
```

---

### 3. Verify the User Creation

Check that the user was successfully created and assigned the correct shell.

```bash
cat /etc/passwd | grep ammar
```

Expected output:

```text
ammar:x:1003:1003::/home/ammar:/sbin/nologin
```

---

## 🧠 Concepts Learned

* Linux user management
* Non-interactive shells
* SSH remote access
* Basic system administration
* Security best practices for service accounts

---

## 🔐 Why Use a Non-Interactive Shell?

A non-interactive shell is used to:

* Prevent user login
* Improve system security
* Create service or system accounts
* Reduce attack surface

Common non-interactive shells:

```text
/sbin/nologin
/usr/sbin/nologin
/bin/false
```

---

## ✅ Result

The user **`ammar`** was successfully created on **Application Server 2** with a non-interactive shell, fulfilling the challenge requirements.
