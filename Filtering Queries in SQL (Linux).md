<h1>Scenario</h1>
<p>As a security professional at a large organization. Part of my job is to investigate security issues to help keep the system secure. 
I recently discovered some potential security issues that involve login attempts and employee machines.

My task is to examine the organization’s data in their employees and log_in_attempts tables.
I’ll need to use SQL filters to retrieve records from different datasets and investigate the potential security issues.</p>

<h2>Solution</h2>
<b>Step 1: Retrieve Login Attempts On Specific Dates</b>
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
<p>Therefore, to find the failed login attempts made after hours, we will use the following query: <pre>Select *<br>from log_in_attempts <br>where login_time > '18:00' and success = 0</pre></p>
<li>SELECT - indicates which column to return, SELECT * means will want to return all information in the table we're working on.</li>
<li>FROM - indicates which table to query, in this case, we were querying the log_in_attempts table.</li>
<li>WHERE - indicates the condition for the filter, in this case, login_time and success.</li>
<li>THE GREATER THAN OPERATOR (>) - indicates that we wanted to query attempts made after 18:00.</li>
<li>AND - indicates that both conditions must be met concurrently or simultaneouesly. 'login_time' and 'success'.</li>
<br>


![2  Failed](https://github.com/ThokozaneN/Google-Cybersecurity-Projects/assets/133211908/19c587a3-5459-4b0f-9b75-0352c048d0be)
<br>
<br>
<b>Step 2: Retrieve Login Attempts On Specific Dates</b>
<p>A suspicious event occurred on 2022-05-09. To investigate this event, I had to review all login attempts which occurred on this day and the day before. To do this, I had to use filters in SQL
that identifies all the login attempts that occurred on 2022-05-09 or 2022-05-08.</p>
<p>To do this, we will use the following SQL query: <pre>select * <br>from log_in_attempts <br>where login_date = '2022-05-09' or '2022-05-08';</pre></p>

![3  By dates](https://github.com/ThokozaneN/Google-Cybersecurity-Projects/assets/133211908/f68f28a1-c8ab-467b-8914-1430bd02ebd6)

<p>Note now that we used the OR operator between the login dates. <pre>OR - is an operator that specifies that either the condition can be met.</pre></p>
<p>This returned 75 login attempts made on 2022-05-09 and 2022-05-08.</p>

