# Git & GitHub Documentation

# Git

- A free version control system.
- Tool for managing source code changes.
  - Save code snapshots (“Commits”).
  - Work with alternative code versions (“Branches”).
  - Move between branches and commits.
- Easily rollback to older code snapshot or develop new features without braking production code.

## Configuring Git

### Set a Username and Email address

```git
git config --global user.name "your-username"
git config --global user.email "your-email"
```

Learn more about Git's configuration options here: https://git-scm.com/docs/git-config

## Git Repositories

- Git Features can be used in projects with Git Repositories.
- Repository is a folder used by Git to track all changes of a given project.
- Git commands require a repository in a project.

## Create/Initialize a Git Repository

Create a Git local repository using

```git
git init
```

## Git Commits

Create commits contains two steps:

- Stage changes for next commit

```git
git add <file(s)>
```

- Commit the changes

```git
git commit
```

## Add files for staging

```git
git add file1.txt file2.py subfolder/file3.txt
```

- You can specify the names of the file(s) or the directories separated with spaces.

```git
git add .
```

- You can also select all the files using dot (.) and Git will take care of adding only the changed files to the staging.

## Check status

```git
git status
```

- The above command will display the status of the files changed, files untracked and files added to staging for commit.

## Commit

To commit the changes, there are two ways to do so:

```git
git commit
```

- The above command will open a text editor where it will ask for the commit message. There is no restriction on the message length.

```git
git commit -m "COMMIT MESSAGE GOES HERE..."
```

- Git also provides a flag to specify the commit message in the command line. However, the commit message can not be too long.

## Logs

**Code:**

```git
git log
```

**Output:**

```git
commit d3cbd544b901109401216de67ca83e3279e91072 (HEAD -> master)
Author: Author Name <author.name@gmail.com>
Date: Sat Oct 7 12:12:32 2023 +0530

    Initial Commit
```

**Explanation:**

- The output shows the commit ID (d3cbd544b901109401216de67ca83e3279e91072) and the commit message.
- HEAD indicated in the Output means that the current pointer points to the master/main branch.
- This pointer is used to show which commit is currently loaded.
- We can move between commits using this commit ID and Git will move the HEAD pointer to that commit ID.

## Move between Commits

```git
git checkout COMMIT_ID
```

- Using this command, we can move to any commit by specifying the ID of the commit.
- Git will move the HEAD pointer to this commit ID and this will load the code snapshot captured at that commit.
- However, after using this command, the new changes will still be there.

## Reverting Commits

```git
git revert COMMIT_ID
```

- Used to undo commits by creating a new commit.
- Will revert the changes and load the code snapshot of the previous commit.
- However, the new code will still be present in the cache.

## Reverting Code

```git
git reset --hard COMMIT_ID
```

- Undo changes by deleting all commits since COMMIT_ID.
- Remove the changes permanantly.
- Revert commit should be preffered option as will not delete the changes permanantly.

## Staging Multiple Files and Ignoring with .gitignore

- Create a new file with name ".gitignore" in the project location.
- Add all those files which needs to be ignored while commiting the changes.

## Branches

- Branches are used to work on a code parallely without breaking the code in the master/main branch.
- We need to work on different branches if we are working on a bug fix or creating a new feature.
- This will make sure that the code in master branch remains intact and it does not get broken.

## Create a New Branch

```git
git branch BRANCH_NAME
```

- This command will create a new branch with name BRANCH_NAME.

```git
git checkout BRANCH_NAME
```

- This command will switch to the BRANCH_NAME.

```git
git checkout -b BRANCH_NAME
```

- We can specify -b flag to combine the outcome of above two commands.
- This will create a new branch with BRANCH_NAME and will switch to this branch.

## List All Branches

```git
git branch --list
```

- Shows the list of branches and the active branch marked with \*.

## Deleting a Branch

```git
git branch -D BRANCH_NAME
```

- To delete an existing branch, -D flag can be used as shown above.

## Merging Branches (Locally)

To merge the changes of a branch (e.g. feature) to master branch, following commands can be used.

```git
git checkout master
git merge BRANCH_NAME
```

- This will merge all the changes from BRNACH_NAME to master branch.
- Git is powerful enough to handle the conflicts caused while merging in most of the cases.
- However, sometimes Git fails to merge the code due to conflicts in the code, hence manual efforts are required to handle the conflict.

# GitHub

- Cloud Git repository & services provider.
- Allows user to store and manage Git repository.

#### Could Git repository storage (Push & Pull):

- Backup, Sync-up work accross machines, work in teams.
- Public & Private, Team management

#### Code Management & Collaborative development:

- Via Issues, Projects, Pull Requests & more

#### Automation & CI/CD:

- Via GitHub Actions, GitHub Apps & more

## Connecting Local & Remote Repository

```git
git remote add origin REMOTE_REPO_URL
```

- Connect Local and Remote repository by adding the remote repository URL with an identifier.
- Here, origin is the identifier for remote repo.
- However, we can use any identifier name.

## Adding User for Pushing Changes to GitHub

```git
git remote set-url origin https://user-name@github.com/repository_name
```

- This command will tell Git which user account to use while pushing the changes to GitHub.
- If the user does not have permission to push to the owner's repo, then it may show permission error.

## Push Changes to GitHub

```git
git push --set-upstream origin BRANCH_NAME
```

- Push the local code on BRANCH_NAME to remote repository with the same BRANCH_NAME.

## Pull Changes from GitHub

```git
git checkout master
git pull
```

- Pull the latest changes from remote repository to local repository.
- This will pull the changes from master/main branch.

## Cloning Repositories (Master Branch)

```git
git clone REMOTE_REPO_URL FOLDER_NAME
```

- This command will clone the code from remote repository's master branch and will store it locally inside FOLDER_NAME.

## Cloning Repositories (Local Branch)

```git
git clone -b BRANCH_NAME REMOTE_REPO_URL FOLDER_NAME
```

- This command will clone the code from BRANCH_NAME of remote repository's and will store it locally inside FOLDER_NAME.

## View List of Connected Remote Repositories

```git
git remote
```

- Shows the list of identifiers of connected remote repos.

```git
git remote get-utl origin
```

- Shows the remote repo URL of origin.
