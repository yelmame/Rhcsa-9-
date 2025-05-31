# SSH - Secure SHell

- SSH stands for Secure SHell Login
- It provides secure and remote shell login from one device to another
- We can communicate and share data using SSH
- It communicates using port number **22**
- It creates an encrypted connection
- Before SSH, we used Telnet, which allows remote connection **without encryption**

## SSH Setup

### Key Concepts

- **Server**: The computer you want to access
- **Client**: The computer used to access the server

### Connection Methods

1. **Password-based**
2. **Key-based**

### SSH Service Details

- **Package name**: `openssh`
- **Config file**: `/etc/ssh/sshd_config`
- **Service**: `sshd.service`
- **Port**: `22`

## Connecting to the Server

### Using Password-based Login

```bash
ssh username@ip_addr
```

### Using Key-based Access

Steps:
1. Generate the key on the client machine:


```bash
ssh-keygen
```

2. Check the generated key:
``` bash
ls -a .ssh
```
3. Copy the public key to the server:
```bash
ssh-copy-id serveruser@ip_addr_server
```
-  The key is copied to the server's 
~/.ssh/authorized_keys file

- When the client connects, the client’s private key is matched with the public key on the server


### Enabling Root Login (if disabled)

- Sometimes root access is restricted

- To allow root login:

1. Open config file:
```bash 
/etc/ssh/sshd_config
```
2. Find and uncomment:
```bash
#PermitRootLogin yes
```

