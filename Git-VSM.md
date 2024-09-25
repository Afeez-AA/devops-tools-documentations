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

### 7. Some Common Git Commands and Their Use Cases:
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

### 28. To return a staged file to unstaged 
```
git restore --staged <file>
```