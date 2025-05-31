
# Process Management

Process management is a fundamental aspect of operating systems, including Linux, that manages processes and task lists on a system. It's responsible for:
- **Resource management**: Ensuring resources are used efficiently  
- **System stability**: Maintaining the stability of the system  
- **Multitasking**: Enabling seamless multitasking  
- **Program interaction**: Controlling how programs interact with each other  

A **program** when executed becomes a **process**. We give it an input and receive output.  
It generally takes an input, processes it, and gives an appropriate output.

---

## Types of Processes
1. **Foreground Process**
   - Interactive process
   - Started by users

2. **Background Process**
   - Non-interactive process
   - Started by system

---

## Stages of Process

- **New State**: Process is generated  
- **Ready State**: Process is waiting to execute  
- **Running State**: Process is running  
- **Waiting State**: Waits until current process is completed  
- **Terminate State**: Process completed  

---

## Process Cycle

Commands: `ps1`, `ps2`

```text
new → ready → running → terminate  
        ↓         ↑  
     waiting ←   
```

---

## Types of Processes
1. Parent  
2. Child  
3. Zombie  
4. Orphan  
5. Daemon  

---

## Forking Process
When a process starts a new process, it's called a forking process.

```text
Daemon Process  
└── parent  
    ├── zombie  
    └── fork → child  
              ├── fork → Child2  
              └── terminate  
```

---

## Useful Commands

### Viewing Processes

```bash
$ ps              # Show processes  
$ ps -a           # List all processes  
$ ps -o %cpu,pid,uid,%mem,cmd  # Show specified fields  
$ ps -ac          # List process with priority  
$ ps -aux         # List processes like top  
```

---

## TOP Command Usage
- `ctrl+z` : Stop command  
- `ctrl+c` : Terminate the process  

Within `top`:
- `k` : Kill the process  
- `r` : Renice the value  
- `p` : Sort by CPU usage  
- `m` : Sort by memory  
- `t` : Sort by runtime  

---

## Kill Commands

Used to terminate/stop processes.

```bash
# Kill a process
$ kill -9 <process_id>

# Terminate process
$ kill -15 <process_id>

# List all signals
$ kill -l
```

Common signals:
- `9`: SIGKILL  
- `15`: SIGTERM  

---

## Background and Foreground Processes

```bash
# Run in foreground
$ fg %<process_id>

# Run in background
$ bg %<process_id>
```

---

## Jobs
```bash
jobs   # Lists running jobs
```

---

## Changing Process Priority

- **System Priority Values:**
  - 0: Highest  
  - 20: Normal  
  - 40+: Lowest  

- **User Renice Values:**
  - -20: Highest  
  - 0: Normal  
  - +20: Lowest  

### Set the priority:

```bash
$ renice <nice_value> <process_id>
$ renice 19 3513
$ renice -n 15 -p 3513
```
