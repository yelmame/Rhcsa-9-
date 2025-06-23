
# nfs & autofs

autofs step by step cconfiguration 



✅ What is AutoFS?

AutoFS is a service that automatically mounts and unmounts filesystems (e.g., NFS, local, SMB) as they are accessed. This saves system resources and improves performance, especially for NFS shares.

## Step 1: Set Up NFS Server (Machine 1 – 192.168.1.10)

✅ 1.1 Install NFS Server

sudo dnf install nfs-utils -y       

sudo apt install nfs-kernel-server  

✅ 1.2 Create Shared Directory

sudo mkdir -p /srv/nfs/shared

sudo chown nobody:nobody /srv/nfs/shared

sudo chmod 755 /srv/nfs/shared

✅ 1.3 Add Entry to /etc/exports

sudo vi /etc/exports

/srv/nfs/shared 192.168.1.0/24(rw,sync)

✅ 1.4 Export and Start NFS Service

sudo exportfs -a

sudo systemctl start nfs-server

sudo systemctl enable nfs-server

✅ 1.5 Allow NFS Through Firewall (RHEL/CentOS)

sudo firewall-cmd --permanent --add-service=nfs

sudo firewall-cmd --reload

📥 Step 2: Configure AutoFS Client (Machine 2 – 192.168.1.20)

✅ 2.1 Install AutoFS and NFS Client

sudo dnf install autofs nfs-utils -y     # RHEL/CentOS

sudo apt install autofs nfs-common -y    # Ubuntu/Debian

✅ 2.2 Edit /etc/auto.master

sudo vi  /etc/auto.master
Add
/mnt/nfs /etc/auto.nfs

✅ 2.3 Create and Edit Map File /etc/auto.nfs


sudo nano /etc/auto.nfs
Add this line:

shared -rw,sync 192.168.1.10:/srv/nfs/shared

shared will be the subdirectory under /mnt/nfs

It will mount 192.168.1.10:/srv/nfs/shared when accessed

✅ 2.4 Reload AutoFS

sudo systemctl restart autofs

sudo systemctl enable autofs

🔍 Step 3: Test the Configuration

✅ 3.1 Try Accessing the Share

cd /mnt/nfs/shared

ls
You should see the contents of the server’s shared folder. AutoFS will mount it on demand.

✅ 3.2 Check Mount Status

mount | grep nfs
🔄 Step 4: Auto Unmount After Timeout
If no activity happens for 60 seconds, the mount will be automatically unmounted.

✅ Final Directory Structure
On Server:

Shared path: /srv/nfs/shared

On Client:

AutoFS mount path: /mnt/nfs/shared









You said:
j


ChatGPT said:
It looks like you typed "j" — could you please clarify what you need help with?

Would you like:

The AutoFS configuration steps in a downloadable PDF or .md file?

A hands-on assignment based on this setup?

Help with a specific error or issue?

Let me know how I can assist you better!








