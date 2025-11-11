  # File permissions in Linux

## Project description

I am acting as a security professional at a large organization, primarily working with the research team. The project I’m completing is examining the existing permissions on the file system. Determining if the permissions match the authorization that should be given. Modifying permissions to correct any discrepancies.

## Check file and directory details

I changed to the projects director to review the files and check their current permissions, shown below, by using ```ls -la```. <br>

```
researcher2@d2a04414eb3f:~$ cd projects
researcher2@d2a04414eb3f:~/projects$ ls -la
total 32
drwxr-xr-x 3 researcher2 research_team 4096 Nov 2 20:00 .
drwxr-xr-x 3 researcher2 research_team 4096 Nov 2 21:21 ..
-rw--w---- 1 researcher2 research_team   46 Nov 2 20:00 .project_x.txt
drwx--x--- 2 researcher2 research_team 4096 Nov 2 20:00 drafts
-rw-rw-rw- 1 researcher2 research_team   46 Nov 2 20:00 project_k.txt
-rw-r----- 1 researcher2 research_team   46 Nov 2 20:00 project_m.txt
-rw-rw-r-- 1 researcher2 research_team   46 Nov 2 20:00 project_r.txt
-rw-rw-r-- 1 researcher2 research_team   46 Nov 2 20:00 project_t.txt
```

## Describe the permissions string

There is 1 directory and 5 files, 1 being hidden, in the ```home/researcher2/projects```  directory.

The directory ```drafts``` gives read, write and execute permissions for the user, while also giving execute permissions to the ```research_team``` group. There are no permissions for the other group.

```
drwx--x--- 2 researcher2 research_team 4096 Nov 2 20:00 drafts
```

This is found by viewing the d/r/w/x/- indicators after the d. The beginning line will either be a ‘d’ or a ‘-’. The ‘d’ representing a directory while the ‘-’ represents a file. The ‘r’ represents read access, allowing a user to access the file. The ‘w’ is permissions to modify the file. The ‘x’ represents the ability to execute an executable command or program. The ‘-’ indicates no access.

The first three characters after the d (rwx) represent the user level. Which gives read (r), write (w) and execute (x) access. A (-) would indicate no access. The second grouping of three characters (--x), represents the group users. There is no read or write access, but there is an execute access. The last three characters, (---), represent the other group, which has zero access.

## Change file permissions

Per company policy, the other permission group is not to allowed to have writer access. While reviewing the permissions, it was found that the file ```project_k.txt``` did have writer access for the other group.

```
-rw-rw-rw- 1 researcher2 research_team   46 Nov 2 20:00 project_k.txt
```

Using the ```chmod``` command, ```chmod o-w project_k.txt```, the writer access was removed and confirmed using the ```ls \-la``` command.

The first letter after chmod will indicate which permission level is being adjusted. The equation symbol will dictate if the permission is being removed, added or changed to equal the permission. The third character is the type of access. In the example above, o-w is the other permission group removing the writer access.

(U=users, G=group, O=Other)

```
researcher2@d2a04414eb3f:~$ cd projects
researcher2@d2a04414eb3f:~/projects$ ls -la
total 32
drwxr-xr-x 3 researcher2 research_team 4096 Nov 2 20:00 .
drwxr-xr-x 3 researcher2 research_team 4096 Nov 2 21:21 ..
-rw--w---- 1 researcher2 research_team   46 Nov 2 20:00 .project_x.txt
drwx--x--- 2 researcher2 research_team 4096 Nov 2 20:00 drafts
-rw-rw-r-- 1 researcher2 research_team   46 Nov 2 20:00 project_k.txt
-rw-r----- 1 researcher2 research_team   46 Nov 2 20:00 project_m.txt
-rw-rw-r-- 1 researcher2 research_team   46 Nov 2 20:00 project_r.txt
-rw-rw-r-- 1 researcher2 research_team   46 Nov 2 20:00 project_t.txt
```

This is confirmed with the line, ```\-rw-rw-r–``` for ```project_k.txt```

## Change file permissions on a hidden file

The file ```.project_x.txt``` was found to have writer permissions, when it should only have read access. The (.) at the beginning of the file indicates the file is hidden. ```Chmod``` was used to change ```.project_x.txt``` to only allow read access to the user and group. There was a mistake that needed to be fixed, which is why there is an extra line of code.

```
researcher2@d2a04414eb3f:~/projects$ chmod u-w,g-r .project_x.txt
```
```
researcher2@d2a04414eb3f:~/projects$ chmod g+r,g-w .projectx.txt
```

```
researcher2@d2a04414eb3f:~$ cd projects
researcher2@d2a04414eb3f:~/projects$ ls -la
total 32
drwxr-xr-x 3 researcher2 research_team 4096 Nov 2 20:00 .
drwxr-xr-x 3 researcher2 research_team 4096 Nov 2 21:21 ..
-r--r----- 1 researcher2 research_team   46 Nov 2 20:00 .project_x.txt
drwx--x--- 2 researcher2 research_team 4096 Nov 2 20:00 drafts
-rw-rw-rw- 1 researcher2 research_team   46 Nov 2 20:00 project_k.txt
-rw-r----- 1 researcher2 research_team   46 Nov 2 20:00 project_m.txt
-rw-rw-r-- 1 researcher2 research_team   46 Nov 2 20:00 project_r.txt
-rw-rw-r-- 1 researcher2 research_team   46 Nov 2 20:00 project_t.txt
```

The permissions for the hidden file, ```.project_x.txt``` now only gives read permissions to the user and group level.

This is confirmed with the line, ```\-r--r----``` for the ```.project_x.txt```

## Change directory permissions

User researcher2 should be the only one to have access to the drafts folder. In the review of accesses, it was found that the group level also had access to this directory.

```
researcher2@d2a04414eb3f:~/projects$ chmod g-x /home/researcher2/projects/drafts
researcher2@d2a04414eb3f:~/projects$ ls -la
total 32
drwxr-xr-x 3 researcher2 research_team 4096 Nov 2 20:00 .
drwxr-xr-x 3 researcher2 research_team 4096 Nov 2 21:21 ..
-r--r----- 1 researcher2 research_team   46 Nov 2 20:00 .project_x.txt
drwx------ 2 researcher2 research_team   46 Nov 2 20:00 drafts
-rw-rw-r-- 1 researcher2 research_team   46 Nov 2 20:00 project_k.txt
-rw-r----- 1 researcher2 research_team   46 Nov 2 20:00 project_m.txt
-rw-rw-r-- 1 researcher2 research_team   46 Nov 2 20:00 project_r.txt
-rw-rw-r-- 1 researcher2 research_team   46 Nov 2 20:00 project_t.txt
```
The ```chmod g-x /home/researcher2/projects/drafts``` command was used to remove the group execution access.

This is now confirmed with the line, ```drwx------``` for the ```drafts``` folder.

## Summary

During this project to audit the permission of the folders for ```researcher2```, it was discovered that the other permission group had write access for ```project_k.txt```, which was removed.

The hidden file `.project_x.txt` was also found to have writer access at the user and group level. Both of these access have been removed.

The drafts folder for researcher2 was found to have the execute permission allowed for the `research_team`, group level. Only researcher2 should have this access, so this was removed.
