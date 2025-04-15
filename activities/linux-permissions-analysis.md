---
title: Linux File Permissions Analysis
difficulty: Easy
estimated_time: 15 minutes
---

### 🔐 Overview
This case study demonstrates how Linux commands were used to inspect, interpret, and modify file and directory permissions to enforce least privilege and correct misconfigurations within a team environment.

---

### 🧾 Project Objective
Review and manage file and directory permissions in a shared research environment, ensuring that access aligns with organizational security policies.

---

### 📂 Check File and Directory Details
Navigate to the working directory and list all files with detailed information:

```bash
cd ~/projects
ls -la
```

This command reveals files and directories with varying permission levels, including a hidden file `.project_x.txt` and a directory `drafts` with limited access.

---

### 🔎 Describe the Permissions String
Example output:

```bash
-rw--w---- 1 researcher2 research_team 46 Apr 15 18:57 .project_x.txt
```

**Breakdown:**
- `rw-` = user has read/write
- `-w-` = group has write-only (⚠️ insecure)
- `---` = others have no access

This string indicates that the file has misconfigured permissions for the group.

---

### 🔧 Change File Permissions
Adjust `.project_x.txt` so both user and group can read, but not write or execute:

```bash
chmod u=r,g=r,o= .project_x.txt
```

Updated permissions:

```bash
-r--r----- 1 researcher2 research_team 46 Apr 15 18:57 .project_x.txt
```

---

### 🫥 Change Permissions on a Hidden File
The same command was applied to `.project_x.txt` to reduce group access to read-only, removing write permissions.

---

### 📁 Change Directory Permissions
Remove execute permission for the group on the `drafts` directory:

```bash
chmod g-x drafts
```

**Before:**
```bash
drwx--x--- 2 researcher2 research_team 4096 Apr 15 18:57 drafts
```

**After:**
```bash
drw---- --- 2 researcher2 research_team 4096 Apr 15 18:57 drafts
```

Now, group members cannot enter or traverse the drafts directory.

---

### ✅ Summary
- Inspected and interpreted Linux file permission strings using `ls -la`.
- Hardened permissions on a sensitive hidden file using `chmod`.
- Applied least-privilege principles to a directory by removing group execute permission.
- Ensured that shared files have no unnecessary access by group or others.
- Used direct permission settings (e.g., `u=r,g=r,o=`) for precise control.