# User Management in Linux

A quick reference for creating, modifying, and managing users, groups, and sudo access on Linux systems.

---

## Table of Contents

- [Key Files](#key-files)
- [Creating Users](#creating-users)
- [Managing Passwords](#managing-passwords)
- [Modifying Users](#modifying-users)
- [Deleting Users](#deleting-users)
- [Working with Groups](#working-with-groups)
- [Sudo Access and Privilege Escalation](#sudo-access-and-privilege-escalation)

---

## Key Files

| File           | Purpose                                  |
| -------------- | ---------------------------------------- |
| `/etc/passwd`  | Stores user account details              |
| `/etc/shadow`  | Stores encrypted user passwords          |
| `/etc/group`   | Stores group information                 |
| `/etc/gshadow` | Stores secure group details              |

> **Note:** Passwords in `/etc/shadow` cannot be decrypted. Once a password is lost, there is no way to recover it.

---

## Creating Users

### useradd

Available on most Linux distributions.

Create a user without a home directory:

```bash
useradd username
```

Create a user with a home directory:

```bash
useradd -m username
```

Create a user with a specific shell:

```bash
useradd -s /bin/bash username
```

> `useradd` is mostly used in scripts because it asks for less information.

### adduser

Available on Debian-based systems. This is an interactive command that asks for a password and additional details.

```bash
adduser username
```

---

## Managing Passwords

Set or change a user's password:

```bash
passwd username
```

### Enforcing Password Policies

Set password expiry days:

```bash
chage -M 90 username
```

Lock a user account:

```bash
passwd -l username
```

Unlock a user account:

```bash
passwd -u username
```

---

## Modifying Users

Use `usermod` to modify an existing user.

Change the username:

```bash
usermod -l new_username old_username
```

Change the home directory:

```bash
usermod -d /new/home/directory -m username
```

Change the default shell:

```bash
usermod -s /bin/zsh username
```

---

## Deleting Users

Remove a user but keep their home directory:

```bash
userdel username
```

Remove a user and their home directory:

```bash
userdel -r username
```

---

## Working with Groups

### Creating Groups

```bash
groupadd groupname
```

### Adding Users to Groups

```bash
usermod -aG groupname username
```

### Viewing Group Memberships

```bash
groups username
```

### Changing the Primary Group

```bash
usermod -g new_primary_group username
```

---

## Sudo Access and Privilege Escalation

### Adding a User to the Sudo Group

On Debian-based systems:

```bash
usermod -aG sudo username
```

On RHEL-based systems:

```bash
usermod -aG wheel username
```

### Granting Specific Commands with Sudo

Edit the sudoers file:

```bash
visudo
```

Then add:

```
username ALL=(ALL) NOPASSWD: /path/to/command
```