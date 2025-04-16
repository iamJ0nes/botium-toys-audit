---
title: SQL Query Filtering for Security Investigations  
difficulty: Easy  
estimated_time: 15 minutes  
---

### 🧮 Overview  
This case study demonstrates how SQL filters were applied to support an internal investigation into potential security events and to identify employee systems in need of security updates. The queries focused on isolating failed logins, suspicious activity, and department-specific employee data.

# SQL Security Filtering Activity  
## Applying Filters to Support Security Tasks

---

### 🔍 Retrieve After-Hours Failed Login Attempts  
To investigate potential unauthorized activity outside of business hours, I used the following SQL query:

```sql
SELECT * FROM log_in_attempts  
WHERE login_time > '18:00' AND success = FALSE;
```

**Explanation:**  
- Filters log entries after 6:00 p.m.  
- Returns only failed login attempts.

---

### 📆 Retrieve Login Attempts on Specific Dates  
To investigate a specific incident, I retrieved login activity for two dates:

```sql
SELECT * FROM log_in_attempts  
WHERE login_date = '2022-05-09' OR login_date = '2022-05-08';
```

**Explanation:**  
- Targets logins from the day of and the day before the incident.  
- Uses an OR clause for date matching.

---

### 🌎 Retrieve Login Attempts Outside of Mexico  
To identify logins from foreign sources:

```sql
SELECT * FROM log_in_attempts  
WHERE country NOT LIKE 'MEX%';
```

**Explanation:**  
- Uses NOT LIKE to exclude Mexico entries, including both `MEX` and `MEXICO`.  
- Helps identify unusual access patterns.

---

### 🧑‍💻 Retrieve Employees in Marketing (East Building)  
To plan system updates for Marketing staff in a specific location:

```sql
SELECT * FROM employees  
WHERE department = 'Marketing' AND office LIKE 'East%';
```

**Explanation:**  
- Filters for the Marketing department.  
- Limits results to those in the East building based on office.

---

### 💼 Retrieve Employees in Finance or Sales  
To find staff eligible for a different security update:

```sql
SELECT * FROM employees  
WHERE department = 'Finance' OR department = 'Sales';
```

**Explanation:**  
- Captures employees in either Finance or Sales.  
- Uses the OR operator to broaden the match.

---

### 🧯 Retrieve Employees Not in IT  
To apply a separate update for non-IT personnel:

```sql
SELECT * FROM employees  
WHERE department != 'Information Technology';
```

**Explanation:**  
- Excludes IT staff.  
- Ensures targeted updates for other departments.

---

### ✅ Summary  
- Utilized filtering logic using `WHERE`, `AND`, `OR`, and `NOT` to narrow down results.  
- Used pattern matching with `LIKE` and wildcards for flexible filtering.  
- Enhanced cybersecurity response through structured data querying.
