---
layout: post
title:  Portswigger Academy - SQL Injection
description: SQL Injection
date:   2023-09-02 15:01:35 +0700
image:  '/images/20.jpg'
tags:   [Penetration Tester, Red Team, Write Up,  Portswigger ]
---

# Table of Contents
- [What is SQL Injection?](#what-is-sql-injection)
- [How to Detect SQLi?](#how-to-detect-sqli)
- [How to Prevent SQLi](#how-to-prevent-sqli)
- [Labs](#labs)
    - [SQL injection vulnerability in WHERE clause allowing retrieval of hidden data](#sql-injection-where-clause)
    - [SQL injection vulnerability allowing login bypass](#sql-injection-login-bypass)
    - [SQL injection attack, querying the database type and version on Oracle](#sql-injection-oracle-type-version)
    - [SQL injection attack, querying the database type and version on MySQL and Microsoft](#sql-injection-mysql-microsoft-type-version)
    - [SQL injection attack, listing the database contents on non-Oracle databases](#sql-injection-non-oracle-listing)
    - [SQL injection attack, listing the database contents on Oracle](#sql-injection-oracle-listing)
    - [SQL injection UNION attack, determining the number of columns returned by the query](#sql-injection-union-columns)
    - [SQL injection UNION attack, finding a column containing text](#sql-injection-union-text-column)
    - [SQL injection UNION attack, retrieving data from other tables](#sql-injection-union-data-retrieval)
    - [SQL injection UNION attack, retrieving multiple values in a single column](#sql-injection-union-multiple-values)
    - [Blind SQL injection with conditional responses](#blind-sql-injection-conditional-responses)
    - [Blind SQL injection with conditional errors](#blind-sql-injection-conditional-errors)
    - [Visible error-based SQL injection](#visible-error-based-sql-injection)
    - [Blind SQL injection with time delays and information retrieval](#blind-sql-injection-time-delays)
    - [Blind SQL injection with out-of-band interaction](#blind-sql-injection-out-of-band)
    - [Blind SQL injection with out-of-band data exfiltration](#blind-sql-injection-data-exfiltration)
    - [SQL injection with filter bypass via XML encoding](#sql-injection-filter-bypass-xml-encoding)

## What is SQL Injection? <a id="what-is-sql-injection"></a>

SQL injection is a security vulnerability allowing attackers to inject malicious SQL code into web application inputs, potentially granting unauthorized access to databases and enabling data manipulation or control over the server. Preventive measures include using parameterized queries, input validation, and least privilege principles.

## How to detect SQLi <a id="how-to-detect-sqli"></a>
- Check for single quote characters ('), errors, or anomalies in responses.
- Evaluate SQL syntax with different values, noting response discrepancies.
- Test Boolean conditions like OR 1=1 and OR 1=2 for response variations.
- Use payloads causing time delays to identify response differences.
- Employ Out-of-Band (OAST) payloads to trigger network interactions and monitor responses.


## How to prevent SQLi <a id="how-to-prevent-sqli"></a>

- Use parameterized queries or prepared statements.
- Validate and sanitize user input.
- Utilize ORM frameworks.
- Apply the least privilege principle.
- Implement WAFs and security filters.
- Conduct regular security audits.
- Provide security training for developers.

## Labs <a id="labs"></a>

### 1. SQL injection vulnerability in WHERE clause allowing retrieval of hidden data <a id="sql-injection-where-clause"></a>

<!-- Content for SQL injection vulnerability in WHERE clause allowing retrieval of hidden data -->
#### Lab Description
![Alt text](/images/portswigger/sqli/lab1-description.png "lab1-description")

#### Solution
1. Detect SQL injection (SQLi) vulnerabilities using the single quote character (') to identify errors or anomalies. 
    - URL: web-security-academy.net/filter?category=Pets'
2. To retrieve all data, utilize true conditions 'OR 1=1--'
    - URL: web-security-academy.net/filter?category=Pets'+OR+1=1--
3. In summary, the solution involves first detecting the SQL injection vulnerability using the single quote character and then exploiting it by injecting a true condition to retrieve the hidden data.

![Alt text](/images/portswigger/sqli/lab1-solved.png "lab1-solved")

### 2. SQL injection vulnerability allowing login bypass <a id="sql-injection-login-bypass"></a>

#### Lab Description
![Alt text](/images/portswigger/sqli/lab2-description.png "lab2-description")

#### Solution
1. Detect SQL injection (SQLi) vulnerabilities by utilizing the single quote character (') to identify errors or anomalies on the login form.
    - URL: web-security-academy.net/login
2. To bypass the login page, add "admininistrator'or+1=1--" in the form. Here, "admininistrator'or1=1--" is a SQL injection payload. The condition "1=1" always evaluates to true, so the SQL query will return results as if the user were an administrator, effectively bypassing the login mechanism.
3. Test Boolean conditions like OR 1=1 and OR 1=2 to observe response variations, which can indicate potential SQL injection vulnerabilities.

![Alt text](/images/portswigger/sqli/lab2-solved.png "lab2-solved")

### 3. SQL injection attack, querying the database type and version on Oracle <a id="sql-injection-oracle-type-version"></a>

<!-- Content for SQL injection attack, querying the database type and version on Oracle -->

### 4. SQL injection attack, querying the database type and version on MySQL and Microsoft <a id="sql-injection-mysql-microsoft-type-version"></a>

<!-- Content for SQL injection attack, querying the database type and version on MySQL and Microsoft -->

### 5. SQL injection attack, listing the database contents on non-Oracle databases <a id="sql-injection-non-oracle-listing"></a>

<!-- Content for SQL injection attack, listing the database contents on non-Oracle databases -->

### 6. SQL injection attack, listing the database contents on Oracle <a id="sql-injection-oracle-listing"></a>

<!-- Content for SQL injection attack, listing the database contents on Oracle -->

### 7. SQL injection UNION attack, determining the number of columns returned by the query <a id="sql-injection-union-columns"></a>

<!-- Content for SQL injection UNION attack, determining the number of columns returned by the query -->

### 8. SQL injection UNION attack, finding a column containing text <a id="sql-injection-union-text-column"></a>

<!-- Content for SQL injection UNION attack, finding a column containing text -->

### 9. SQL injection UNION attack, retrieving data from other tables <a id="sql-injection-union-data-retrieval"></a>

<!-- Content for SQL injection UNION attack, retrieving data from other tables -->

### 10. SQL injection UNION attack, retrieving multiple values in a single column <a id="sql-injection-union-multiple-values"></a>

<!-- Content for SQL injection UNION attack, retrieving multiple values in a single column -->

### 11. Blind SQL injection with conditional responses <a id="blind-sql-injection-conditional-responses"></a>

<!-- Content for Blind SQL injection with conditional responses -->

### 12. Blind SQL injection with conditional errors <a id="blind-sql-injection-conditional-errors"></a>

<!-- Content for Blind SQL injection with conditional errors -->

### 13. Visible error-based SQL injection <a id="visible-error-based-sql-injection"></a>

<!-- Content for Visible error-based SQL injection -->

### 14. Blind SQL injection with time delays and information retrieval <a id="blind-sql-injection-time-delays"></a>

<!-- Content for Blind SQL injection with time delays and information retrieval -->

### 15. Blind SQL injection with out-of-band interaction <a id="blind-sql-injection-out-of-band"></a>

<!-- Content for Blind SQL injection with out-of-band interaction -->

### 16. Blind SQL injection with out-of-band data exfiltration <a id="blind-sql-injection-data-exfiltration"></a>

<!-- Content for Blind SQL injection with out-of-band data exfiltration -->

### 17. SQL injection with filter bypass via XML encoding <a id="sql-injection-filter-bypass-xml-encoding"></a>

<!-- Content for SQL injection with filter bypass via XML encoding -->
