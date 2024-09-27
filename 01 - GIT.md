# GIT

### Git Clone
Clone a repository from a remote URL to your local machine.
```bash
git clone <url>
```

### Git Add
Stage changes made to a file, preparing it for the next commit.
```bash
git add <filename>
```

### Git Commit
Commit the staged changes to the repository. The first command uses a message flag; the second stages files that have been modified and commits them.
```bash
git commit -m "<message>"
git commit -am "<message>"
```

### Git Config
Set the email and username for commits globally on your machine.
```bash
git config --global user.email "<email>"
git config --global user.name "<name>"
```

### Git Status
Check the status of your working directory and staging area, showing which files are staged, unstaged, or untracked.
```bash
git status
```

### Git Push
Upload your local repository commits to the remote repository.
```bash
git push
```

### Git Pull
Fetch changes from the remote repository and merge them into your current branch.
```bash
git pull
```

### Git Log
View the commit history for the repository, listing commits in reverse chronological order.
```bash
git log
```

### Git Reset
Reset your current branch to a specific commit (first command) or to the state of the `origin/master` branch (second command), discarding any changes.
```bash
git reset --hard <commit>
git reset --hard orgin/master # Reset to the specified commit or branch
```

## Branching

### Git Branch
List all local branches in the repository.
```bash
git branch
```

### Git Checkout
Switch to a specified branch or create a new branch and switch to it (first command).
```bash
git checkout -b <new_branch_name>  # Create and switch to a new branch
git checkout <branch_name>         # Switch to an existing branch
```

### Git Merge
Merge changes from the specified branch into the current branch.
```bash
git merge <branch_name>
```

## Github Pages
repository name must start with ```your_username``` and end with ```github.io```

for example : ```mrmrprogrammer.github.io```
