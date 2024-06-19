# Lab: Modifying File Permissions in Linux

## Objective

This lab demonstrates my capabilities in updating file permissions in Linux. In this scenario, the research team at my organization needs to update the file permissions to reflect the correct level of authorization. This involves reviewing current permissions, identifying discrepancies, and adjusting settings accordingly. Ultimately, the new file permissions mitigate potential risks associated with unauthorized access.

### Skills Learned

- Advanced comprehension of file permissions and ownership nuances in Linux.
- Mastery of command-line utilities such as 'chmod' and 'chown'.
- Proficiency in diagnosing and resolving permission-related challenges.
- Comprehensive knowledge of permission levels (user, group, others) and their practical implementation.
- Enhanced critical thinking and problem-solving abilities applicable to cybersecurity contexts.

### Tools Used

- Linux (Bash)

## Steps

### Step One 

Description: Check File and Directory Details

I used the following Linux commands in the Bash shell to determine the existing permission sets for a specific directory in the file system:

<img width="910" alt="LL_Step One" src="https://github.com/aehumphrey/File-Permissions-Linux-Lab/assets/33531835/f8b7ec86-dd7e-4876-b049-56c4ce25e967">

*Ref 1. Using ls -la command to display current file permissions.*

First, I navigated to the projects directory using cd projects. Next, I used the ls command with the -la modifier to display a list of the file contents, including hidden files. The output revealed that there is one directory named drafts, five project files, and one hidden file named .project_x.txt.


### Step Two

Description: Describe the permissions string

The 10-character string included with each file in the directory can be deciphered to understand the current file authorizations and permissions as follows:

- 1st character: This is either (d) or (-) and indicates the file type. D is for directory; hyphen (-) is for regular file.
- 2nd-4th characters: This first trio following the file type reflects user permissions: read (r), write (w), and execute (x). If the character is a hyphen (-), this permission is not granted to the user.
- 5th-7th characters: This second trio reflects group permissions:  read (r), write (w), and execute (x). If the character is a hyphen (-), this permission is not granted to the group.
- 8th-10th characters: This final trio reflects all other permissions beyond the user and the group (others). As with user
and group, these permissions are read (r), write (w), and execute (x). If the character is a hyphen (-), this permission is not granted for others.

As an example, project_t.xt has the permissions -rw-rw-r--. This means:
- 1st character: (-) indicates project_t.txt is not a directory
- 2nd-4th characters: The user can read and write. The user cannot execute.
- 5th-7th characters: The group can read and write. The group cannot execute.
- 8th-10th characters: Others can read. Others cannot write or execute.


### Step Three

Description: Change file permissions

In this scenario, my organization wants to remove write access from “other” across all files. To accomplish this, I referred to the initial file permissions (see Ref 1.) The file project_k.txt allowed others write access.

The following code demonstrates how I used Linux commands to remove write access from project_k.txt:

<img width="662" alt="LL_Step Two" src="https://github.com/aehumphrey/File-Permissions-Linux-Lab/assets/33531835/67f58bfe-8fc3-478f-b96e-d36cfd369855">

*Ref 2: Using chmod to change permissions on project_k.txt.*

The command chmod modifies permissions on files and directories. The first argument indicates what permissions should be changed and the second argument specifies the file or directory to which these changes will be applied. In this case, o-w project_k.txt removes write permissions from ‘other’ on the file project_k.txt. To review my changes and ensure they were applied correctly, I used ls -la to display a list of updated permissions.


### Step Four

Description: Change file permissions on a hidden file

The file .project_xt.txt has recently been archived. No one should have write access, but the user and group should have read access.

The following code demonstrates how I used Linux commands to update the permissions to reflect this:

<img width="730" alt="LL_Step Three" src="https://github.com/aehumphrey/File-Permissions-Linux-Lab/assets/33531835/cecbc297-8bf5-429d-9b10-d3d1b38b4fc2">

*Ref 3: Using chmod to change permissions on project_x.txt.*

The file .project_x.txt is a hidden file. I know this for two reasons: first, unless I add the modifier -a to my ls command, it will not appear in the output; second, it begins with a period (.). 

Using chmod, I removed write permissions from the user (u-w) and the group (g-w). The group does not currently have read permissions, so I added those (g+r). I then used ls -la to display a list of updated permissions.


### Step Five

Description: Change directory permissions

Finally, the organization would like to update the drafts directory so that only researcher2 has access to the directory and its contents. This means that only researcher2 should have execute permissions.

The following code demonstrates how I used Linux commands to change the permissions:

<img width="732" alt="LL_Step Four" src="https://github.com/aehumphrey/File-Permissions-Linux-Lab/assets/33531835/4bf1fce4-8d4e-453c-af16-951431595e3a">

*Ref 4: Using chmod to change permissions on the drafts directory*

I previously determined the group had execute permissions (see Ref. 1). Using the chmod command, I removed these (g-x). Researcher2 already had execute permissions, so I did not need to add these. I then used ls -la to display a list of updated permissions.

## Summary

I changed multiple permissions (user, group, other) to match the correct level of authorization. This involved using ls -la  to check the current permissions and the chmod command to change the permissions on files and directories.











