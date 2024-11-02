<h1>Managing file permissions in Linux</h1>

<h2>Description</h2>
In this scenario, it was examined and managed the permissions on the files in the <b>/home/researcher2/projects</b> directory for the researcher2 user.
The researcher2 user was part of the research_team group.<br />
It was checked the permissions for all files in the directory, including hidden files, to make sure that permissions align with the authorization that should be given. When it wasn't, the permissions were changed.<br />
First, it was checked the user and group permissions for all files in the projects directory. Next, it was checked whether any files had incorrect permissions and the permissions were changed as needed. Finally, it was checked the permissions of the <b>/home/researcher2/projects/drafts</b> directory and modified these permissions to remove any unauthorized access.

<br />

<h2>Objectives</h2>

- <b>Examine directory and file permissions</b>
- <b>Change directory and file permissions</b>

<h2>Languages and Utilities Used</h2>

- <b>Bash commands for permission management</b> 

<h2>Environments Used </h2>

- <b>Linux CLI</b>

<h2>Program walk-through:</h2>

<b>Step 1 - Check file and directory details:</b> 
<br/> 
<br />
![1](https://github.com/user-attachments/assets/4c8598f6-474b-4dad-89a9-7b3c78501971)
<br />
<br />
Firstly, it was used <b>ls</b> to check what were the subdirectories of the researcher2 home directory, then it was navigated to projects directory through <b>cd projects</b>. 
<br />
<b>ls -l</b> checked the files and subdirectories of projects and also the permissions on them. <b>ls -la</b> did the same, but also including hidden item.
<br />
<br />
<br />

<b>Step 2 - Describe the permissions string:</b>  
<br/> 
As the first item of each line, there’s the permissions string which is made by 10 characters. 1st character can be a d or a - (d represents it’s a directory and - it’s not a directory, so it’s a file). Characters 2 to 4 represent the user permissions, characters 5 to 7 represent the group permissions and 8 to 10 others’ (r for read, w for write and x for execute, - represents permission is not granted). Taking <b>project_k.txt</b> as an example, <b>-rw-rw-rw-</b> shows it’s a file and the user, its group and others can read/write it.
<br />
<br />
<br />

<b>Step 3 - Change file permissions:</b>  
<br/> 
In this task, it was determined whether any files have incorrect permissions and then changed the permissions as needed. This action would remove unauthorized access and strengthen security on the system. None of the files should allow the other users to write to files. 
<br/> 
<br />
![2](https://github.com/user-attachments/assets/c5d48445-9f93-44be-ada8-5ab59e320a33)
<br />
<br />
As showed previously, other user could write to project_k.txt had. So to remove it, it was used <b>chmod o-w project_k.txt</b> to take off written permissions from other. <b>ls -l</b> command and the info <b>-rw-rw-r--</b> showed other could only read the file.
<br />
Another requisite was that project_m.txt should not be readable or writable by the group or other, so reading permission was removed from the group through <b>chmod g-r project_m.txt</b>. <b>ls -l</b> command showed the permissions on all the files again, and it was shown it was right once the file had the <b>-rw-------</b> string.
<br />
<br />
<br />

<b>Step 4 - Change file permissions on a hidden file:</b>  
<br/> 
In this task, it was determined if a hidden file had incorrect permissions and then changed the permissions as needed. This action would further remove unauthorized access and strengthen security on the system. The file .project_x.txt is a hidden file that has been archived and should not be written to by anyone. (The user and group should still be able to read this file.)
<br/> 
<br />
![3](https://github.com/user-attachments/assets/d3f9bdc5-4eaa-47bc-83ea-ca9d44519852)
<br />
<br />
Through <b>ls -la</b> and the string <b>-rw--w----</b> it was show the user had read and write permissions and the group had write permissions. Considering user and group should have only read permissions, it was changed through the <b>chmod u=r,g=r .project_x.txt</b> command. <b>ls -la</b> and <b>-r--r-----</b> string confirmed it was done accordingly.
<br />
<br />
<br />

<b>Step 5 - Change directory permissions:</b>  
<br/> 
In this task, it was changed the permissions of a directory. First, it was checked the group permissions of the /home/researcher2/projects/drafts directory and then modified the permissions as required. Only the researcher2 user should be allowed to access the drafts directory and its contents. (This means that only researcher2 should have execute privileges.)
<br/> 
<br />
![4](https://github.com/user-attachments/assets/188e8b27-d80d-41d6-a738-a3cddf20b849)
<br />
<br />
Firstly, it was checked the drafts directory permissions through <b>ls -l</b>, and it was shown on the string that user could read/write/execute in this directory and group could execute, which was a from config. This permission was removed through <b>chmod g-x drafts</b>, and it was visible through </b>ls -l and the drafts string that change was done effectively.
<br />
<br />

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
