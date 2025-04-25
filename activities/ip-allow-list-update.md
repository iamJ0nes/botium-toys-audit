---
title: IP Allow List Update Script  
difficulty: Easy  
estimated_time: 15 minutes  
---

### 🧾 Overview  
This case study demonstrates how Python was used to automate the task of updating an allow list by removing unauthorized IP addresses. The algorithm reads data from a text file, filters out disallowed entries, and writes the cleaned list back to the file — supporting access control and reducing administrative overhead.

# Python File Operation: IP Allow List Update  
## Remove Unauthorized IPs from Access File

---

### 📁 Step 1: Open the File that Contains the Allow List  
```python
import_file = "allow_list.txt"

with open(import_file, "r") as file:
    ip_addresses = file.read()
```
> The `open()` function opens the file in read mode, and `.read()` stores the contents in a variable called `ip_addresses`.

---

### 🔄 Step 2: Convert the String into a List  
```python
ip_addresses = ip_addresses.split()
```
> The `.split()` method converts the string into a list of IP addresses.

---

### 🧹 Step 3: Remove IPs on the Remove List  
```python
remove_list = ["192.168.60.153", "192.168.247.153", "192.168.116.187"]

for element in remove_list:
    if element in ip_addresses:
        ip_addresses.remove(element)
```
> This loop checks each IP in the `remove_list`, and removes it from `ip_addresses` if present. This works because there are no duplicates in the file.

---

### 💾 Step 4: Update the File with the Revised IPs  
```python
updated_ips = "\n".join(ip_addresses)

with open(import_file, "w") as file:
    file.write(updated_ips)
```
> The list is joined into a newline-separated string and written back to the original file, replacing the old contents.

---

### ✅ Summary  
- Used Python file handling to read and write IP allow lists  
- Applied list operations to remove disallowed entries  
- Demonstrated control flow via loops and conditionals  
- Emphasized safe file I/O operations for security automation tasks

