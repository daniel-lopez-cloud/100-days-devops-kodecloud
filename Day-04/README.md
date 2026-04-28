# Day 04 - Grant Executable Permissions Using `chmod 755` on App Server 2

---

## 📌 Objective

The objective of this task is to grant executable permissions to the backup automation script:

```bash id="m1y4k9"
/tmp/xfusioncorp.sh
```

on **Application Server 2** (`stapp02`) within the Stratos Datacenter.

The requirement specifies that **all users must have the ability to execute the script**, which is correctly achieved using numeric permissions `755`.

---

## 🏗️ Environment

The task applies specifically to:

* **Server:** `stapp02`
* **Role:** Application Server 2
* **Script Location:** `/tmp/xfusioncorp.sh`
* **Requirement:** All users must be able to execute the script
* **Privilege Level Required:** Root

---

## 🧭 Procedure

### 1. Connect to Application Server 2

Access the server from the jump host using SSH.

```bash id="f0ks7m"
ssh steve@stapp02
```

---

### 2. Obtain Root Privileges

Administrative permissions are required to modify file permissions.

```bash id="b71s3t"
sudo su -
```

---

### 3. Verify Current File Permissions (Recommended)

Check the existing permissions of the script.

```bash id="n7z1k2"
ls -l /tmp/xfusioncorp.sh
```

Example output before modification:

```bash id="u6q9wp"
-rw-r--r-- 1 root root 1234 ...
```

This indicates the script does not yet have executable permissions.

---

### 4. Grant Executable Permissions Using `chmod 755`

Apply the required permissions using numeric notation:

```bash id="v8j3cn"
chmod 755 /tmp/xfusioncorp.sh
```

This command ensures that all users can execute the script.

---

## 🔢 Permission Breakdown — `755`

```text
7 = read + write + execute (owner)
5 = read + execute (group)
5 = read + execute (others)
```

Resulting permission structure:

```text
rwxr-xr-x
```

This satisfies the requirement that **all users** have execution capability.

---

### 5. Verify Updated Permissions

Confirm that the permissions were successfully applied.

```bash id="3q5mza"
ls -l /tmp/xfusioncorp.sh
```

Expected output:

```bash id="x4n2ld"
-rwxr-xr-x
```

The presence of `x` for owner, group, and others confirms correct configuration.

---

## 🧠 Key Concepts Learned

* Linux file permission management
* Numeric permission notation (`755`)
* Executable permissions for all users
* Privilege escalation using `sudo su -`
* Verification using `ls -l`
* Basic operational tasks in Linux administration
