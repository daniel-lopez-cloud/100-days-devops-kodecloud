# Day-03: Disable Direct Root SSH Login

## 📌 Objective

The objective of this task is to enhance system security by disabling direct SSH login for the `root` user on all application servers. This configuration change reduces the attack surface and enforces the use of privileged escalation mechanisms such as `sudo`.

This is a standard security hardening practice in Linux system administration and DevOps environments.

---

## 🏗️ Environment

The task applies specifically to the following **Application Servers**:

* `stapp01`
* `stapp02`
* `stapp03`

Other infrastructure components (load balancer, database, storage, etc.) are not modified for this task.

---

## 🧭 Procedure

### 1. Connect to the Application Server

Access the server using SSH with the assigned user credentials.

```bash
ssh <user>@stapp01
```

Example:

```bash
ssh tony@stapp01
```

---

### 2. Obtain Root Privileges

Switch to the root user to perform administrative changes.

```bash
sudo su -
```

---

### 3. Edit the SSH Configuration File using `nano`

Open the SSH daemon configuration file with elevated privileges.

```bash
sudo nano /etc/ssh/sshd_config
```

Locate the following directive:

```bash
PermitRootLogin yes
```

or:

```bash
#PermitRootLogin yes
```

Modify the configuration to:

```bash
PermitRootLogin no
```

This setting disables direct SSH login for the root user.

---

### 4. Save and Exit the Editor (`nano`)

To save the changes and exit:

```text
CTRL + O    (Write the file)
Enter
CTRL + X    (Exit the editor)
```

---

### 5. Restart the SSH Service

Apply the configuration changes by restarting the SSH service.

```bash
sudo systemctl restart sshd
```

If required by the system:

```bash
sudo systemctl restart ssh
```

---

### 6. Verify the Configuration

Confirm that the configuration has been successfully applied.

```bash
grep PermitRootLogin /etc/ssh/sshd_config
```

Expected output:

```bash
PermitRootLogin no
```

---

## 🔁 Repeat the Procedure

The same steps must be executed on each application server:

* `stapp01`
* `stapp02`
* `stapp03`

---

## 🔐 Security Rationale

Disabling direct root SSH login is a widely recommended security practice because:

* It prevents direct remote access to the most privileged account
* It enforces accountability through individual user accounts
* It reduces the risk of brute-force and credential-based attacks
* It aligns with industry security hardening standards

---

## 🧠 Key Concepts Learned

* SSH service configuration management
* Linux privilege escalation using `sudo`
* Secure system administration practices
* Editing system configuration files using `nano`
* Service management with `systemctl`
