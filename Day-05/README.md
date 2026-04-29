# Day 05 — Install SELinux Packages and Permanently Disable SELinux

---

## 📌 Objective

Following a security audit, the task requires preparing **SELinux** on **Application Server 2** by installing the necessary packages and permanently disabling SELinux through configuration changes.

The system must be configured so that **after the next reboot**, SELinux will be in a **disabled** state.
A manual reboot is not required because a scheduled maintenance reboot is already planned.

---

## 🏗️ Environment

The task applies specifically to:

* **Server:** `stapp02`
* **Role:** Application Server 2
* **Tool Used:** `sudo nano`
* **Package Manager:** `yum`
* **Configuration File:** `/etc/selinux/config`

---

## 🧭 Procedure

### 1. Connect to Application Server 2

Access the server from the jump host using SSH.

```bash
ssh steve@stapp02
```

---

### 2. Obtain Root Privileges

Administrative permissions are required to install packages and modify system configuration files.

```bash
sudo su -
```

---

### 3. Install Required SELinux Packages

Install the necessary SELinux policy packages using the `yum` package manager.

```bash
yum install -y selinux-policy selinux-policy-targeted
```

This ensures the system has the required SELinux components installed for future configuration and testing.

---

### 4. Edit the SELinux Configuration File Using `nano`

Open the SELinux configuration file:

```bash
sudo nano /etc/selinux/config
```

Locate the following line:

```bash
SELINUX=enforcing
```

or:

```bash
SELINUX=permissive
```

Modify the configuration to:

```bash
SELINUX=disabled
```

This change ensures SELinux will be disabled after the next system reboot.

---

### 5. Verify the Configuration

Confirm that the configuration has been updated correctly.

```bash
cat /etc/selinux/config
```

Expected output:

```bash
SELINUX=disabled
```

---

## ⚠️ Important Notes

* A system reboot is **not required** for this task
* The current runtime status of SELinux can be ignored
* The requirement focuses on the **permanent configuration** after reboot
* The scheduled maintenance reboot will apply the change automatically

---

## 🔐 Security and Operational Context

SELinux (Security-Enhanced Linux) is a Linux security module that provides mandatory access control (MAC).
Administrators may temporarily disable SELinux during testing, migrations, or configuration changes before re-enabling it with properly defined policies.

This task demonstrates:

* Package installation using `yum`
* System security configuration management
* Editing system configuration files
* Understanding persistent vs runtime configuration

---

## 🧠 Key Concepts Learned

* SELinux package installation
* Permanent configuration management
* Linux system security controls
* Using `yum` for package management
* Editing configuration files with `nano`
* Privilege escalation using `sudo su -`
