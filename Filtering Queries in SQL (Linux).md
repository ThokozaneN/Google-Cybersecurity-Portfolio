<h1>Scenario</h1>
<p>As a security professional at a large organization. Part of my job is to investigate security issues to help keep the system secure. 
I recently discovered some potential security issues that involve login attempts and employee machines.

My task is to examine the organization’s data in their employees and log_in_attempts tables.
I’ll need to use SQL filters to retrieve records from different datasets and investigate the potential security issues.</p>

<h2>Solution</h2>
<b>Task 1: Retrieve Login Attempts On Specific Dates</b>
<p>I had discovered a security potential (failed login attempts) that occurred after business hours. To investigate this, I needed to query the log_in_attempts table to review after hours activity.
  Let's keep in mind that the log_in_attempts table consists of the following columns:</p>
    <li><b>event_id</b> - stores/records event ids.</li>
    <li><b>username</b> - stores/records usernames of employees.</li>
    <li><b>login_date</b> - stores all recorded login attempts dates.</li>
    <li><b>login_time</b> - stores all recorded login attempts time.</li>
    <li><b>country</b> - stores/records countries which the login attempt was made from.</li>
    <li><b>ip_address</b> - stores/records ip addresses of machines used by employees.</li>
    <li><b>success</b> - shows if the login attempt was a success of failure, with true (1) indicating success, and false (0) indicating failure.</li>
    <br>
    
    
![1  Show](https://github.com/ThokozaneN/Google-Cybersecurity-Projects/assets/133211908/cd58132d-a2b0-43b0-bbaa-aa42b3f5de0d)
<br>
<p>Therefore, to find the failed login attempts made after hours, we will use the following query: <pre>SELECT *<br>FROM log_in_attempts <br>WHERE login_time > '18:00' AND success = 0</pre></p>
<li>SELECT - indicates which column to return, SELECT * means will want to return all information in the table we're working on.</li>
<li>FROM - indicates which table to query, in this case, we were querying the log_in_attempts table.</li>
<li>WHERE - indicates the condition for the filter, in this case, login_time and success.</li>
<li>THE GREATER THAN OPERATOR (>) - indicates that we wanted to query attempts made after 18:00.</li>
<li>AND - indicates that both conditions must be met concurrently or simultaneouesly. 'login_time' and 'success'.</li>
<br>


![2  Failed](https://github.com/ThokozaneN/Google-Cybersecurity-Projects/assets/133211908/19c587a3-5459-4b0f-9b75-0352c048d0be)
<br>
<br>
<b>Task 2: Retrieve Login Attempts On Specific Dates</b>
<p>A suspicious event occurred on 2022-05-09. To investigate this event, I had to review all login attempts which occurred on this day and the day before. To do this, I had to use filters in SQL
that identifies all the login attempts that occurred on 2022-05-09 or 2022-05-08.</p>
<p>To do this, we will use the following SQL query: <pre>SELECT * <br>FROM log_in_attempts <br>WHERE login_date = '2022-05-09' OR '2022-05-08';</pre></p>
<br>

![3  By dates](https://github.com/ThokozaneN/Google-Cybersecurity-Projects/assets/133211908/f68f28a1-c8ab-467b-8914-1430bd02ebd6)

<p>Note now that we used the OR operator between the login dates. <pre>OR - is an operator that specifies that either the condition can be met.</pre></p>
<p>This returned 75 login attempts made on 2022-05-09 and 2022-05-08.</p>
<br>
<br>
<b>Task 3: Retrieve Login Attempts Outside of Mexico</b>
<p>There’s been suspicious activity with login attempts, but the team has determined that this activity didn't originate in Mexico. Now, you need to investigate login attempts that occurred outside of Mexico. Now, we had to investigate login attempts that occurred outside of Mexico. The SQL query that we're going to use is as follow: <pre>SELECT * <br>FROM log_in_attempts<br>WHERE NOT country LIKE 'mex%'; </pre> <pre>NOT - negates a condition, so in this case, we knew the suspicious activity didn't originate in Mexico. <br>So to exclude the country, we had to use the NOT operator to filter out Mexico.</pre></p>
<pre>The LIKE operator is used with WHERE to search for a pattern in a column, and LIKE is used with the percentage (%) wildcard to<br>return columns that starts with a specific word, in this case, we wanted Mexico, so we used 'MEX%'. </pre>

![4  %](https://github.com/ThokozaneN/Google-Cybersecurity-Projects/assets/133211908/3e9d12cd-1c02-43cc-9801-d405334d096c)
<br>
<br>
<b>Task 4: Retrieve Employees In The Marketing</b>
<p>My team wanted to perform security updates on specific employee machines in the Marketing department in all the offices in the East building. I was responsible for getting information on these employee machines and needed to query the employees table. </p>
<p>The employees table consisted of the following columns:</p>
<li><b>employee_id</b> - employees can be identified by their employee id's.</li>
<li><b>device_id</b> - devices that are assigned to an employee have their own unique id.</li>
<li><b>username</b> - employee usernames.</li>
<li><b>department</b> - to which department does a certain employee work for.</li>
<li><b>office</b> - location of the office a certain employee work for.</li>
<br>

![5  employees](https://github.com/ThokozaneN/Google-Cybersecurity-Projects/assets/133211908/aafc2b70-1e36-44ff-aa40-a92418a20c5f)
<br>
<p>So to perform security updates on employee machines that are in the Marketing department, we will use the following SQL query to find employees on the marketing department, east office building, and filter out the rest:
<pre>SELECT *<br>FROM employees<br>WHERE department = 'marketing' AND office LIKE 'East%';</pre></p>

![6  MARKETING](https://github.com/ThokozaneN/Google-Cybersecurity-Projects/assets/133211908/1e8c6687-40c6-4f84-9859-518967bb723e)
<br>
<br>
<b>Task 5: Retrieve Employees In Finance or Sales</b>
<p>My team now needed to perform a different security update on machines for employees in the Sales and Finance departments. for this we will use the OR operator to query either finance or sales.</p>
<p>The query will look like this: <pre>SELECT *<br>FROM employees<br>WHERE department = 'finance' OR department = 'sales';</pre></p>

![7  Sales](https://github.com/ThokozaneN/Google-Cybersecurity-Projects/assets/133211908/230cd5a0-ba3d-4f77-a2ea-ad11b6957bcd)
<br>
<br>
<b>Task 6: Retrieve All Employees Not In IT</b>
<p>My team needed to make one more update to employee machines. The employees who are in the Information Technology department already had this update, but employees in all other departments need it. So, in this task, we need to filter out the Information Technology department since they've already received the update. We will use NOT operator to exclude the IT department. We will use the following SQL query to perform this task: <pre>SELECT *<br>FROM employees<br>WHERE NOT department = 'information technology';</pre></p>

![8  IT](https://github.com/ThokozaneN/Google-Cybersecurity-Projects/assets/133211908/a1eca73d-ab0b-40e0-a801-92989bbfd2dd)

<h1>Summary</h1>
<p>I've successfully applied SQL queries to retrieve information on both the log_in_attempts and employees tables. I used the AND, OR, NOT, LIKE operators and also the percentage (%) wildcard to successfully filter out information on the tables/database.</p>
