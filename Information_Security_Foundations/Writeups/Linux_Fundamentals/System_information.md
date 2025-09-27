# HTB Linux Commands Exercise - Writeup

This HTB exercise focuses on Linux commands and requires knowledge of essential system information commands such as `uname`, `env`, `pwd`, and understanding of different Linux directories like `/etc`.

## Available Commands for This Exercise

The following commands are covered in this module:
`whoami` `id` `hostname` `uname` `pwd` `ifconfig` `ip` `netstat` `ss` `ps` `who` `env` `lsblk` `lsusb` `lsof` `lspci`

## Questions and Solutions

### 1. Find out the machine hardware name and submit it as the answer

**Command to use:** `uname -m`
- The `-m` flag displays the hardware architecture (machine type)

```bash
uname -m
```

---

### 2. What is the path to htb-student's home directory?

**Command to use:** `pwd` (when logged in as htb-student)

```bash
pwd
```

Since we're logged in as htb-student, the `pwd` command will show our current directory, which should be the home directory by default.

---

### 3. What is the path to the htb-student's mail?

**Command to use:** `env`

```bash
env | grep MAIL
```

Look for the `MAIL` environment variable in the output.

---

### 4. Which shell is specified for the htb-student user?

**Method:** Access the `/etc/passwd` file and look for the htb-student entry.

The shell path is the last field (after the last colon `:`) in the passwd entry for the htb-student user. You need to examine the `/etc/passwd` file and copy the shell path for the htb-student user.

---

### 5. Which kernel release is installed on the system?

**Command to use:** `uname -r`
- The `-r` flag displays the kernel release version

```bash
uname -r
```

---

### 6. What is the name of the network interface that has MTU set to 1500?

**Command to use:** `ifconfig` or `ip`

```bash
# Method 1: Using ifconfig
ifconfig

# Method 2: Using ip command
ip link show
```

Look through the output for network interfaces and find the one where `MTU:1500` (ifconfig) or `mtu 1500` (ip) is displayed.

---

## Command Reference

### Commands Used in This Exercise
- `uname` - Display system information
  - `uname -m` - Machine hardware name
  - `uname -r` - Kernel release
- `pwd` - Display current directory path
- `env` - Display environment variables
- `ifconfig` - Display/configure network interfaces
- `ip` - Modern network configuration tool
  - `ip link show` - Show network interfaces

## Important Notes

- All answers should use absolute paths when specifying file locations
- The `env` command is particularly useful for finding environment variables like `$MAIL`, `$SHELL`, `$HOME`
- The `uname` command has various flags for different system information
- Network interface names can vary between systems (eth0, ens33, enp0s3, etc.)

---

**Note:** While there are other commands and methods to solve these questions (such as `cat /etc/passwd`, `echo $VARIABLE`, `grep`, etc.), this writeup focuses only on the commands studied in this module. Alternative solutions exist but are not covered here as they fall outside the scope of the current curriculum.