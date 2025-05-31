# Service Management

- Services are programs or processes that run on your server at all times, starting from when the server boots up.
- A service is an application that runs in the background and performs essential tasks.

## Daemons in Linux

- **Daemons (units)**: Background services that do not need any human interactions.
- To identify daemon services, they always end with "d" (e.g., httpd, systemd, firewalld, chronyd).
- Examples of services are `.service`, `.target`, `.path`, `.socket`, etc.

### systemd
- `systemd` is the first service when the booting process starts.
- Its PID is `1`.

---

## Managing Services

- Use the `systemctl` command to list and manage services.

### List Units
```bash
systemctl list-units     # lists daemon processes
systemctl list-units --all   # lists all services
```

---

## Types of Services

| Unit Type      | File Extension | Description                              |
|----------------|----------------|------------------------------------------|
| service unit   | `.service`     | A system service                         |
| target unit    | `.target`      | A group of systemd units                 |
| automount unit | `.automount`   | A file system automate point             |
| device unit    | `.device`      | A device file recognized                 |
| mount unit     | `.mount`       | A file system mount                      |
| path unit      | `.path`        | A file or directory in the file system   |
| socket unit    | `.socket`      | An interprocess communication socket     |
| slice unit     | `.slice`       | Runs in hierarchy                        |

---

## Useful Commands

### Search for a Service Type
```bash
systemctl --type=service
systemctl --type=socket
```

### Check the State of a Service
```bash
systemctl --type=service --state=running
```

### Check Only Daemon Services
```bash
systemctl list-units --type=service --state=running
```

### Check File Related Daemons
```bash
systemctl list-unit-files
```

### Check Service Dependencies
```bash
systemctl list-dependencies
```

---

## Manage Services

### 1. Check the Status
```bash
systemctl status sshd
```

### 2. Stop the Service
```bash
systemctl stop sshd
```

### 3. Start the Service
```bash
systemctl start sshd
```

### 4. Enable the Service
```bash
systemctl enable sshd
```

### 5. Disable the Service
```bash
systemctl disable sshd
```

### 6. Reload the Service
```bash
systemctl reload sshd
```

### 7. Restart the Service
```bash
systemctl restart sshd
```

---

## Service Masking

- Masking prevents any user or service from starting or modifying a service.

```bash
systemctl mask sshd      # Mask the service
systemctl unmask sshd    # Unmask the service
```
