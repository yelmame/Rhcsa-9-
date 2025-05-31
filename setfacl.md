

# ACL Permissions

- ACL stands for Access Control List  
- It provides a more flexible mechanism for the file system. It is designed to assist with Unix file permission  
- ACL allows giving permission for any user and group to any disk resource  
- `setfacl` and `getfacl` are used for setting up ACL and showing ACL respectively  

## For example:

### Display the ACL
```bash
$ getfacl path_of_directory_or_file
```

##
 
Set the ACL

1. To add permission for a user

``` bash
$ setfacl -m "u:username:permission" path_of_file/folder
$ setfacl -m "u:username:rw-" passwd
```
2. To add permission for a group

```bash
$ setfacl -m "g:groupname:permission" path_of_file/folder
$ setfacl -m "g:group:r--" myfolder

```

3. To allow all files or directories to inherit ACL permission from main to subcontent
```bash 
$ setfacl -Rm "u:username:permission" /directory
```
4. To remove a specific entry
```bash
$ setfacl -x "u:username" path_of_file/directory

```
5. To remove all entries
```bash
$ setfacl -b path_of_file/directory
```
