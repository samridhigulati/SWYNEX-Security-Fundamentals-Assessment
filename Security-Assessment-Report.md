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



Finding 2: SQL Injection in Login Authentication
1. Objective
To understand how SQL injection can manipulate login queries and potentially allow unauthorized access to user accounts without valid credentials.

2. Affected Component
The login authentication system, specifically the username and password inputs used in the SQL query.

3. Vulnerability Type
SQL Injection (SQLi) — authentication bypass through application logic manipulation.

4. Risk
An attacker may exploit improperly handled user input to modify the logic of an SQL query and bypass password verification.

5. Evidence
Test Environment: PortSwigger Web Security Academy — authorized SQL injection training environment.

Example Test Input: administrator'--

Expected Result: The application should verify both the username and password before granting access.

Observed Result: In a vulnerable application, the SQL comment sequence (--) can cause the password-checking portion of the query to be ignored, potentially allowing authentication without a valid password.

Lab Status: lab was completed successfully

Evidence Screenshot: <img width="1762" height="842" alt="image" src="https://github.com/user-attachments/assets/b9b76815-aa60-4c02-a2e0-c9de10b38bef" />
<img width="1176" height="635" alt="image" src="https://github.com/user-attachments/assets/a8c42dbc-b902-43e3-a569-7fc715e5b3ff" />
<img width="1000" height="388" alt="image" src="https://github.com/user-attachments/assets/fcbe602a-18cf-4f4f-926c-a599c73c4996" />
<img width="1201" height="515" alt="image" src="https://github.com/user-attachments/assets/773f79ce-d43f-4345-804b-a4cf2ff28b34" />
<img width="1781" height="807" alt="image" src="https://github.com/user-attachments/assets/6ed43e69-126f-4dfa-a5eb-080c42e3501d" />


6. Recommended Mitigation
Use parameterized queries or prepared statements to prevent user input from altering SQL query structure.
Store passwords using secure password-hashing algorithms rather than plaintext.
Implement secure session management and appropriate access controls.
Perform regular security testing to identify authentication weaknesses.

8. Conclusion
This example demonstrates how SQL injection can undermine authentication when user input is incorporated unsafely into SQL queries. Parameterized queries and secure authentication practices are essential for protecting user accounts against unauthorized access.
