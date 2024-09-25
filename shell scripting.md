## Shell scritpting 

### 1. Commonly Used Shell Commands for a DevOps Engineer:
- `ls`, `cd`, `pwd` – Directory and file navigation.
- `cat`, `less`, `head`, `tail` – File viewing.
- `ps`, `top`, `htop` – Process monitoring.
- `grep`, `awk`, `sed` – Text processing.
- `ssh`, `scp` – Remote access and file transfer.
- `df`, `du` – Disk usage analysis.
- `systemctl`, `service` – Service management.
- `docker`, `kubectl` – Container and Kubernetes management.

### 2. Shell Script to List All Processes:
```bash
#!/bin/bash
ps -ef
```

### 3. Script to Print Only Errors from a Remote Log:
```bash
#!/bin/bash
curl "remote log url" | grep ERROR
```

### 4. Shell Script to Print Even Numbers, Odd Numbers, and Numbers Divisible by 3 and 5 (but not 15) from 1 to 1000:
```bash
#!/bin/bash
for i in {1..1000}; do
  if (( i % 2 == 0 )); then
    echo "Even: $i"
  elif (( i % 2 == 1 )); then
    echo "Odd: $i"
  fi

  if (( i % 3 == 0 && i % 5 == 0 && i % 15 != 0 )); then
    echo "Divisible by 3 & 5 but not 15: $i"
  fi
done
```

### 5. Script to Count the Number of "s" in "statistics":
```bash
#!/bin/bash
echo -n "statistics" | grep -o "s" | wc -l
```

### 6. How Do You Debug a Script?
- Use `bash -x script.sh` to execute the script in debug mode.
- Insert `set -x` to enable debugging and `set +x` to disable within the script.

### 7. Explain Cronjob:
- **Cronjob** is a time-based scheduler in Unix-like systems that runs scripts or commands at specified intervals.
- Use `crontab -e` to edit cron jobs.
- Example: `0 5 * * * /path/to/script.sh` (Runs the script every day at 5:00 AM).

### 8. Script to Report the Health of the Server:
```bash
#!/bin/bash
echo "Disk Usage:"
df -h

echo "Memory Usage:"
free -h

echo "CPU Load:"
uptime

echo "Top 5 Memory Consuming Processes:"
ps aux --sort=-%mem | head -n 6
```

### 9. Difference Between Soft Link and Hard Link:
- **Soft Link**: A pointer to a file's path; breaks if the target file is moved or deleted.
- **Hard Link**: A pointer to the file's data (inode); remains valid even if the original file is deleted.

### 10. Difference Between `break` and `continue` Statements:
- **break**: Exits the loop entirely.
- **continue**: Skips the current iteration and moves to the next one.

### 11. Types of Loops and Their Use Cases:
- **for loop**: Iterates over a range or list.
  - Use case: Iterating over files in a directory.
- **while loop**: Continues until a condition is false.
  - Use case: Reading a file line by line.
- **until loop**: Continues until a condition becomes true.
  - Use case: Polling a service until it’s available.

### 12. Is Bash Dynamic or Statically Typed? Explain the Difference:
- **Bash is dynamically typed**.
  - In dynamically typed languages, variable types are determined at runtime.
  - In statically typed languages, variable types are declared at compile time.

### 13. Top Networking Troubleshooting Tools:
- **ping**: Check network connectivity.
- **traceroute**: Track packet route to a host.
- **netstat**: Display network connections.
- **ifconfig/ip**: Show network interface configurations.
- **tcpdump**: Capture and analyze network traffic.
- **nslookup/dig**: DNS resolution testing.

### 14. What Does `sort` Do?
- Sorts lines of text files based on ASCII or numerical values.
- Example: `sort file.txt` (sorts lines alphabetically).

### 15. How Do You Manage Logs of a System?
- Use tools like `logrotate` to manage log rotation.
- Send logs to external logging services (e.g., ELK stack, Splunk).
- Use `tail -f /var/log/syslog` to monitor logs in real-time.

### 16. Explain `systemd` and Its Use Cases:
- **systemd** is a system and service manager for Linux.
- It manages services, mount points, and can control the startup process.
- Use case: Start/stop services (`systemctl start/stop service_name`).

### 17. Explain `stdin`, `stdout`, and Their Use Cases:
- **stdin**: Standard input (keyboard input or input from a file).
- **stdout**: Standard output (typically the terminal or redirected to a file).
- **stderr**: Standard error (used for error messages).
  
  **Example Use Cases**:
  - Redirect output: `command > output.txt` (stdout to a file).
  - Redirect errors: `command 2> error.txt` (stderr to a file).
  - Use stdin: `command < input.txt` (read input from a file).
  
21. **How do you make a script executable?**
- Use `chmod +x script.sh` to make the script executable.

22. **How to run a command every 10 seconds in a loop?**
```bash
while true; do
  your_command
  sleep 10
done
```

23. **How to find files modified in the last 7 days?**
```bash
find /path/to/directory -type f -mtime -7
```

24. **How to archive and compress a directory using tar?**
```bash
tar -czvf archive_name.tar.gz /path/to/directory
```

25. **How to check if a directory exists in a shell script?**
```bash
if [ -d "/path/to/directory" ]; then
  echo "Directory exists."
else
  echo "Directory does not exist."
fi
```

26. **How to pass arguments to a shell script?**
- You can access arguments using `$1`, `$2`, and so on.
  - Example: `./script.sh arg1 arg2`
    - `$1` refers to `arg1`, and `$2` refers to `arg2`.
