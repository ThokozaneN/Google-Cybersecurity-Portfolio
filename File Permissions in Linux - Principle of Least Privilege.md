<h1>Scenario</h1>
<p>You are a security professional at a large organization. You mainly work with their research team. Part of your job is to ensure users on this team are authorized with the appropriate permissions. This helps keep the system secure. Your task is to examine existing permissions on the file system. You’ll need to determine if the permissions match the authorization that should be given. If they do not match, you’ll need to modify the permissions to authorize the appropriate users and remove any unauthorized access.</p>

<h2>Solution</h2>
<b>Step 1: Check File and Directory Details</b>
<p>Important commands to consider when checking files and directory privileges/permissions:</p>
<b>
  1. ls - We use ls to display files and directories (sub-directories) in the current working directory, <br>
  2. ls -l - We use ls -l to display file and directory permissions. <br>
  3. ls -a - We use ls -a to display hidden files. <br>
  4. ls -la - We use ls -la to display file and directory permissions, including hidden files. <br>
</b> <br>
<p>Below is a screenshot of all four above commands in action</p>

![1  Check Permissions](https://github.com/ThokozaneN/Google-Cybersecurity-Projects/assets/133211908/c6b50655-2f43-49f0-9b76-288ecf9e35ec)
<br>
<br>
<b>Step 2: Description Of The Permission String Used Above</b>
<p>In the Linux operating system there are three types of permissions, Read, Write & Execute. Files are represented by a 10 character permission string in Linux which is: <pre>drwxrwxrwx - r represnts Read, w represents Write & x represents Execute.</pre></p><br>
<p>For directories, the string looks like this: <pre>drwxrwxrwx</pre></p>
<p>The letter d in the string represents directory<pre>[d]rwxrwxrwx</pre></p><br>
<p>Then the first three letters after d (rwx) represent the user(u)<pre>d[rwx]rwxrwx</pre></p><br>
<p>The next three letters (rwx) represent the group(g) in your organization. <pre>drwx[rwz]rwx</pre></p><br>
<p>And the last three letters (rwx) represent other (o) users. <pre>drwxrwx[rwx]</pre></p><br>
it looks like this for regular files:
<pre>-rwxrwxrwx. The hyphen(-) represents regular file</pre>
<br>
<br>
<b>Step 3: Change File Permissions</b>
<p>The organization does not allow "other" to have write access to any files. So I had to check which files grant "others" write permissions and remove or change the permission. We use chmod command to change or remove permissions. In this case, project_k.txt had write permissions but I managed to remove it.</p> <br>

![2  Chmod](https://github.com/ThokozaneN/Google-Cybersecurity-Projects/assets/133211908/49cf26ea-1c8d-419a-afaf-26bb23836626)
<p>The file project_k.txt has a write primission which is not allowed by the organization (according to policy) so it has to be modified or rather removed. This is the command I used to remove the permission from the file: <pre>chmod o-w project_k.txt</pre></p>
<pre>The chmod command is used to change permissions, o stands others, w stands for write permission, the hyphen (subtract sign) means we're removing write permission for the project_k.txt file.</pre>
<br>
<br>
<b>Step 4: Change File Permissions on a Hidden File</b>
<p>The research team has archived .project_x.txt, which is why it’s a hidden file. This file should not have write permissions for anyone, but the user and group should be able to read the file.</p>
<p>So, given this scenario, to assign the appropriate permissions to a hidden file, we first need to display the hidden file and make sure we do have it under the projects directory.</p> <pre>The command we use to display hidden files under a certain directory (projects, in this case) is: ls -a</pre>
<p>So, to change and assign appropriate permissions to the hidden file, .project_x.txt, we will use the chmod command. Below is how I changed the permissions</p><pre>chmod u-w,g-w,g+r .project_x.txt</pre>

![3  Hidden](https://github.com/ThokozaneN/Google-Cybersecurity-Projects/assets/133211908/561d8d7e-824e-435c-81b5-ecc53377fecc)
<p>This will assign appropriate permissions to appropriate users/group, and restrict unathorized access and prevent the file from getting altered or modified.</p>
<br>
<br>
<b>Step 5: Change Directory Permissions </b>
<p>The files and directories in the projects directory belong to the researcher2 user. Only researcher2 should be allowed to access the drafts directory and its contents. First, we need to use the ls -l or ls -la command to check for permissions assigned to the drafts directory, then use the chmod command to change the permissions. In this case we used: <pre>ls -la (to display permissions assigned to drafts)</pre></p><pre>chmod g-x drafts (to remove the Execute(x) permission from group)</pre></p>

![4  Drafts](https://github.com/ThokozaneN/Google-Cybersecurity-Projects/assets/133211908/7fec2153-6e06-4729-bd40-f500ad422e8a)
<br>
<br>
<h1>Summary</h1>
<p>In my role as a Linux system administrator and cybersecurity professional, I conducted a comprehensive audit of the organization's file system permissions. I carefully adjusted permissions to grant access only to authorized users, thereby eliminating any unauthorized access points. This strict adherence to the principle of least privilege has significantly carried the organization's security infrastructure, reinforcing its overall posture against potential threats.</p>
