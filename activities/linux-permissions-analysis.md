---
title: Linux File Permissions Analysis
difficulty: Moderate
estimated_time: 15 minutes
---

### 🔐 Overview  
This case study explores how to examine and modify file and directory permissions in a Linux environment. You'll use commands like `ls -l`, `chmod`, and permission string analysis to identify misconfigurations and apply appropriate access controls.

# File Permissions in Linux

🔐 Linux File Permissions Analysis
Project Objective:
To review and manage file and directory permissions in a shared research environment, ensuring that access aligns with organizational security policies.

📂 Check File and Directory Details
Initial directory listing and permissions were inspected in /home/researcher2/projects:

bash
Copy
ls -la
This revealed multiple files and directories with varying permission levels, including a hidden file .project_x.txt and a directory drafts with limited access.

🧾 Describe the Permissions String
Example output:

bash
Copy
-rw--w---- 1 researcher2 research_team 46 Apr 15 18:57 .project_x.txt
rw- = read/write for user

-w- = write-only for group (incorrect setting)

--- = no access for others

This string indicates that the file has insecure group permissions.

🔧 Change File Permissions
To secure .project_x.txt so that user and group can read, but not write or execute, we ran:

bash
Copy
chmod u=r,g=r,o= .project_x.txt
Updated permission string:

bash
Copy
-r--r----- 1 researcher2 research_team 46 Apr 15 18:57 .project_x.txt
🔐 Change Permissions on a Hidden File
The same command (chmod u=r,g=r,o=) was used to adjust the hidden file .project_x.txt. This reduced group access to read-only, removing write permissions.

📁 Change Directory Permissions
To remove execute access for the group on the drafts directory:

bash
Copy
chmod g-x drafts
Before:

bash
Copy
drwx--x--- 2 researcher2 research_team 4096 Apr 15 18:57 drafts
After:

bash
Copy
drw---- --- 2 researcher2 research_team 4096 Apr 15 18:57 drafts
Now, group members cannot enter or traverse the drafts directory.

✅ Summary
Inspected and interpreted Linux file permission strings using ls -la.

Hardened permissions on a sensitive hidden file using chmod.

Applied least-privilege principles to a directory by removing group execute permission.

Ensured that shared files have no unnecessary access by group or others.

Used direct permission settings (e.g., u=r,g=r,o=) for precise control.