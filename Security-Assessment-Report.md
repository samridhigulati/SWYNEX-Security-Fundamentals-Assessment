Finding 1: SQL Injection in Product Category Filter

1. Objective
To investigate a SQL injection vulnerability in an intentionally vulnerable web application and understand its potential impact.

2. Affected Component
The product category filter, specifically the category parameter used in the SQL query.

3. Vulnerability Type
SQL Injection (SQLi) — retrieval of hidden data.

4. Risk
An attacker may manipulate the SQL query by supplying specially crafted input. This can bypass intended filtering conditions and expose unreleased products.
Depending on the database permissions and the application's design, SQL injection can potentially lead to more serious data exposure or unauthorized database operations.

5. Evidence
Test environment: PortSwigger Web Security Academy — authorized SQL injection lab.

Test input: ' OR 1=1--

Expected result: Only products belonging to the selected category that are marked as released should appear.
<img width="1917" height="960" alt="image" src="https://github.com/user-attachments/assets/6f002e61-1cff-4f76-acab-9d70e8d181c3" />

Observed result: <img width="1917" height="965" alt="image" src="https://github.com/user-attachments/assets/9931fe58-342f-4116-aa90-2ab69357d775" />

Lab status: lab was solved

6. Recommended Mitigation
Use parameterized queries or prepared statements instead of concatenating user input into SQL statements.
Perform security testing to verify that user input cannot change the intended SQL query structure.

8. Conclusion
This exercise demonstrates how unsafe handling of user input can allow SQL injection and bypass intended application filters. Parameterized queries are a primary defence against this vulnerability.
