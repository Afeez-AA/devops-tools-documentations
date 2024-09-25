# Commo Devops Tools Documentations

## Common Shell Scripting Questions

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

---

Git and GitHub


Here’s an expanded list of Git and GitHub-related interview questions that you can document on your GitHub account for DevOps interviews:

---

## Common Git and GitHub Interview Questions

### 1. What’s the Difference Between Git and GitHub?
- **Git**: A distributed version control system used for tracking changes in source code during software development.
- **GitHub**: A web-based platform that hosts Git repositories and provides tools for collaboration, issue tracking, and CI/CD.

### 2. What’s the `.git` Directory Used For?
- The `.git` directory contains all the metadata and configuration files for a repository, including commit history, branch information, and references. It's the internal database of Git where everything about the repository is stored.

### 3. How Do You Create/Initialize a Repo Through CLI and Web Browser?
- **CLI**:
  ```bash
  git init
  ```
  - Initializes an empty Git repository in the current directory.
  
  **Web Browser**:
  - Sign in to GitHub → Click `New Repository` → Provide a repository name → Click `Create Repository`.

### 4. Explain the Basic Git Lifecycle:
- **Working Directory**: Where you modify and create new files.
- **Staging Area**: Where you add changes before committing (via `git add`).
- **Repository**: Where committed changes are stored (via `git commit`).
- **Remote Repository**: Where you push changes to share with others (via `git push`).

### 5. Explain the Concept of Branching:
- Branching allows you to create isolated versions of your project. You can work on a new feature without affecting the `main` branch.
  - Example: `git branch feature-branch` creates a new branch called `feature-branch`.

### 6. Explain the Difference Between `git merge`, `git rebase`, and `git cherry-pick`:
- **git merge**: Combines two branches, creating a new merge commit. It maintains the original history.
  
- **git rebase**: Moves or re-applies commits from one branch on top of another branch, creating a linear history.
  
- **git cherry-pick**: Selectively applies specific commits from one branch to another.
  - Example: `git cherry-pick <commit-hash>`.

### 7. List All Common Git Commands and Their Use Cases:
- `git init` – Initialize a new repository.
- `git clone` – Clone an existing repository from a remote.
- `git add` – Stage changes for commit.
- `git commit` – Commit changes to the repository.
- `git status` – Check the status of your working directory.
- `git log` – View commit history.
- `git branch` – Manage branches.
- `git checkout` – Switch to another branch or restore files.
- `git merge` – Merge branches.
- `git rebase` – Rebase branches.
- `git pull` – Fetch and merge changes from the remote repository.
- `git push` – Push local changes to the remote repository.
- `git stash` – Temporarily save changes without committing.
- `git reset` – Undo changes by resetting the HEAD.
- `git tag` – Create, list, delete, or verify tags.

### 8. **How Do You Undo a Commit That Hasn’t Been Pushed Yet?**
- You can use `git reset --soft HEAD~1` to undo the last commit but keep the changes in the working directory.
- Use `git reset --hard HEAD~1` to remove both the commit and the changes.

### 9. **What is Git Stash and When Do You Use It?**
- `git stash` temporarily saves your uncommitted changes without committing them. It is useful when you want to switch branches or pull in changes without committing incomplete work.
  - Example: `git stash` followed by `git stash pop` to retrieve stashed changes.

### 10. **How Do You Resolve Merge Conflicts?**
- When Git cannot automatically merge changes, conflicts occur. You will need to manually edit the conflicting files, then mark them as resolved using:
  ```bash
  git add <file>
  git commit
  ```

### 11. **What is Git Reflog?**
- `git reflog` allows you to view the history of all changes made to the HEAD of the repository, including orphaned or dangling commits.

### 12. **How Do You Revert a Pushed Commit?**
- Use `git revert <commit-hash>` to create a new commit that undoes the changes from the specified commit.
  
  Alternatively, you can use `git reset --hard <commit-hash>` followed by `git push --force`, but this is a more destructive option and should be used with caution.

### 13. **What is the Difference Between `git fetch` and `git pull`?**
- `git fetch` downloads commits, files, and references from a remote repository into your local repository but doesn’t merge them.
- `git pull` does a `git fetch` followed by a `git merge`.

### 14. **How Do You Handle Large Files in Git?**
- Use **Git LFS (Large File Storage)** to track large files without bloating the repository.
  - Example: `git lfs track "*.zip"` tracks all `.zip` files with LFS.

### 15. **Explain Forking and When You Would Use It:**
- Forking creates a copy of a repository under your own account, allowing you to make changes and experiment without affecting the original repository. This is typically used in open-source projects for contributing.

### 16. **How Do You Use Git Hooks?**
- Git hooks are scripts that run automatically on specific Git events like committing or pushing.
  - Example: `pre-commit` hook runs before a commit is made, allowing you to perform actions like linting code.

### 17. **How Do You Squash Commits?**
- Squashing combines multiple commits into one. This is typically done during interactive rebase:
  ```bash
  git rebase -i HEAD~n  # n is the number of commits back from the current HEAD
  ```
  - Mark commits as `squash` to combine them into one.

### 18. **What’s the Difference Between `git reset`, `git revert`, and `git checkout`?**
- `git reset`: Moves the HEAD to a previous commit and optionally modifies the working directory and index.
- `git revert`: Creates a new commit that undoes the changes of a specific commit.
- `git checkout`: Switches branches or restores specific files from a commit.

### 19. **How Do You Secure Git Repositories?**
- Use **GitHub Actions** or **pre-commit hooks** for automated security checks.
- Limit access with **SSH keys** and enforce **2-factor authentication** for GitHub.
- Use **GPG signatures** to verify commit authenticity.

### 20. **How Do You Manage Multiple Remotes?**
- You can add multiple remote repositories using:
  ```bash
  git remote add <remote-name> <url>
  ```
  - To fetch from a specific remote: `git fetch <remote-name>`.
  - Push to a specific remote: `git push <remote-name> <branch>`.

### 21. **What is Git Bisect and How Is It Used for Debugging?**
- `git bisect` is a tool for finding the commit that introduced a bug by using binary search. You mark a commit as good or bad, and Git helps you identify which commit caused the issue.
  ```bash
  git bisect start
  git bisect bad <commit>
  git bisect good <commit>
  ```

### 22. **How Do You Sync a Forked Repository?**
- Fetch changes from the original repository and merge them into your fork:
  ```bash
  git remote add upstream <original-repo-url>
  git fetch upstream
  git merge upstream/main
  ```

### 23. **How Do You Track Only Specific Files in a Git Repository?**
- Use `.gitignore` to exclude files and directories from being tracked. Files listed in `.gitignore` will not appear in Git status or be committed.

### 24. **Explain Git Submodules:**
- Submodules allow you to include a repository as a subdirectory within another repository.
  - Example: `git submodule add <repo-url> <path>` adds a repository as a submodule.
  - Update submodules: `git submodule update --init`.

### 25. **How Do You Perform a Force Push and When Should You Avoid It?**
- `git push --force` overwrites the remote branch with your local changes. This should be avoided on shared branches as it can overwrite others' work.

### 26. Quick-Setup-- create a new repository on the command line
```
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin "url"
git push -u origin main

```

### 27. Quick Setup--push an existing repository from the command line
```
git remote add origin "url"
git branch -M main
git push -u origin main
```

---
Ansible 
