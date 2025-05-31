
Package Manager

- We use this to install new packages on Linux OS.
- There are some commands according to different Linux OSs:
  1. RPM - Redhat Package Manager
  2. YUM - Yellowdog Update Manager
  3. DNF - Dandified YUM
  4. APT - Advanced Package Tool (Ubuntu, Debian)
  5. ZYpp (Zypper) - openSUSE
  6. Pacman - Arch Linux

Using these tools, we can:
- Install packages
- Update packages
- Remove packages
- Get info about packages

In RHEL7, we used RPM to install, update, or remove packages. But after RHEL8, Red Hat discontinued it because it required manual installation of package dependencies, which was difficult to manage.

Therefore, Red Hat introduced YUM, which handles dependencies automatically.

DNF is the advanced version of YUM, offering more functionality, better performance, and improved dependency resolution.

How to run this service:

- First, attach the ISO or log in to the Red Hat portal.
- In this practice, we focus on using the ISO.

Steps:
1. Attach ISO and list it:
```bash
$ lsblk
```

2. Navigate to the ISO location and check the ISO content, which includes AppStream and BaseOS:
   - **AppStream**: Includes user-space applications, languages, databases, and other software packages.
   - **BaseOS**: Provides core functionality and dependencies.

3. Mount the ISO:
```bash
$ mkdir /mnt/iso
$ mount /mnt/iso /pathofiso
```

4. Create a repository file for the package manager at:
```bash
/etc/yum.repos.d/
$ vim /etc/yum.repos.d/local.repo
```

Content of the file:
```ini
[AppStream]
name=AppStream
baseurl=file:///pathofmountpoint/AppStream
gpgcheck=0
enabled=1

[BaseOS]
name=BaseOS
baseurl=file:///pathofmountpoint/BaseOS
gpgcheck=0
enabled=1
```

- Save the file and verify:
```bash
$ yum repolist
```

**Common YUM Commands:**
- List packages:
```bash
$ yum list all
```

- Install packages:
```bash
$ yum install package_name
```

- Update packages:
```bash
$ yum update package_name
```

- Check YUM history:
```bash
$ yum history
```

- Get package info:
```bash
$ yum info package_name
```

- Check groups:
```bash
$ yum group list
```

- Install group packages:
```bash
$ yum groupinstall package_name
```

- Remove packages:
```bash
$ yum remove package_name
$ yum groupremove package_name
```

- Undo a task:
```bash
$ yum history undo <id>
```

- Search for a package:
```bash
$ yum search package_name
```

Using these commands, you can download and run packages on Linux OS with trusted providers.

**EPEL (Extra Packages for Enterprise Linux):**
- Open Firefox and search for EPEL packages.
- Copy the EPEL link and download it into the system.
- Alternatively, create a repo file:
```bash
$ vim /etc/yum.repos.d/epel.repo
```
Content:
```ini
[epel]
name=epel
baseurl=url://link
enabled=1
gpgcheck=0
```
