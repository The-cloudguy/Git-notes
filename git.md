# Git

-   git is Distributed Version Control System.

-   3 statges : 
    -   Working Area
    -   Staging/Index Area
    -   Local Repo/Git Database

-   Distributed version control system means all code will be stored to all nodes(clients).

-   Repository is the place where all code will be stored and which have capability to store versions.

-  git will only see files. If new folder will created, git will not consider folders.

-  Newely created file will consider as **untracked files** and those have no history stored in local repo.

-  **Modified** means it has history which is stored already and now any new change happend in existing file.

-  **Deleted** means file is deleted from repository but its version is stored in local repo.

-  In git we add changes not files.

-  Every changes moved from staging Area to Local Repo is called **COMMIT**

-  Every Commit has ID

-  Using Git we can move to any commit in History

-  **HEAD** is commit id where working Tree is pointing at.

-  Branch is a independent line of development in a project or sprint.

-  **Merge** means bringing changes from one branch to another branch. 2 types **FastForward** and **Merge**

-  **FastForward** - When no extra commit has done by parent and we want to merge from child into parent at that time **FF** is used.

-  **Merge** -- We have created fearure branch from master and If any commit has made by master, at that if we want to merge from feature into master then that time new merged commit will be created.

-  **Rebase** is the process of moving or combining a sequence of commits to a new base commit.

- **cherry-pick** -- sometimes it happend that some branch has certain change which we wanted into our branch. In that case we can cherry-pick(copy) that commit to our branch.

- **revert** -- it will revert back to that commit ID and make an entry of that revert change in git history. It will delete the file.

- **reset**
    - **soft** - it will revert back to that commit but will keep the change in staging area
    - **hard** - it will revert back to that commit and will delete file

-  **git diff** to view difference between two branches if you are adding then it will show + and if you delete something it will show 
    - it can give difference between two commit ID as well

-  **git cat-file** to view parent and tree and blob detail of commit

-  **git stash** it will save changes from index area so you can work someother part then when needed you can pop it back.

-  **git bisect** This command uses a binary search algorithm to find which commit in your project’s history introduced a bug. it can be used to find the commit that changed any property of your project

-  **git tag** used to tag perticular commit to release versions

-  **git blame** the display of author metadata attached to specific committed lines in a file. This is used to examine specific points of a file's history and get context as to who the last author was that modified the line. This is used to explore the history of specific code and answer questions about what, how, and why the code was added to a repository

-  **git reflog** Git keeps track of updates to the tip of branches using a mechanism called reference logs, or "reflogs."

    https://dzone.com/articles/top-35-git-commands-with-examples-and-bonus


# Commands

-  **git init** -  initialize git folder which will give capability to store versions. Make empty folder to repository.
- **git init --bare {path}** - create bare repo at path location
#
-  **git config --global user.name "username"** --
                                                > to configure username and email
-  **git config --global user.email "email"**
#
- **git add {filename}** -  to add untracked or modified files into staging area
- **git add .**  -  add changes in one shot
- **git add -u** -  add only modified file
#
-  **git commit -m "commit message"** -  commit staged file to local repo
#
-  **git status** -  to check the status of updated files
#
- **git revert {commit ID}** - revert back to that commit ID and remove the change but it will create history of reverting in git history
#
- **git reset --soft HEAD~1** - reset last commit but keep the change in staging area
- **git reset --hard** -  Head reaches to last commit change
- **git reset --hard -q {commit id}** -  Head reaches to perticular commit id
- **git reset --hard HEAD~1** - reset last commit and delete changes
- **git reset {file name}** -  change reverted for perticular file
#
- **git checkout {commit id}** -  to move HEAD to perticular commit id
- **git checkout master** -  revert HEAD to Master
- **git checkout -- {file name}** -  revert back changes which has done any file (only in Working Tree)
#
- **git log** - Print log of commits in detail
- **git log --oneline** - Print log of commits in one line
- **git log --name-only** - Print changed file as well with log
- **git log --graph --decorate** - Print log of branch and its parent branches as well
#
- **git clean -df** - clean working area forcefully
- **git clean -di** - clean working area interactivelly 

#
- **git branch {branch name}** - Create a branch
- **git checkout {branch name}** - Change a branch
- **git checkout -b {branch name}** - create branch and change head to that branch directly
#

- **git checkout master**
- **git merge sprint-1** - merge sprint-1 to master
#
- **git checkout -b sprint-2**
- **git rebase master** - rebase sprint-2 on top of master
- **git rebase -i master** - do interactive rebase with master commits
- **git rebase -i HEAD~3** - do interactive rebase with last 3 commits(we can do fixup, delete, reword, squash, pick etc.. actions on commits in this interactive rebasing)
#
- checkout to branch where you want to copy commit
    - **git cherry-pick {commit hash}** - will copy commit to the branch
#
- **git remote add {alias name(usually use origin)} {connection string}** - add remote repo to a local project
    ```
    e.g. git remote add origin https://.../.../[name].git
    ```
- **git remote -v** - list all remote repo
#
- **git push {remote repo alias name} {current branch we are on}** - push local code to remote repo
    ```
    e.g. git push origin master
    ```
#
- **git clone {ssh link}** - clone remote repo to local machine
# 
Fetch and merge to local repo
- **git fetch {remote repo alias name} {current branch we are on}** - fetch remote repo to local
- **git merge origin/master** - merge remote repo to local repo
#
Fetch and merge to local repo direct
- **git pull {remote repo alias} {current branch we are on}** - Pull remote repo and merge to local repo direct
    ```
    e.g. git pull origin master
    ```
#
- **git stash** -  works in index area (only staged files)(it will pile up on other stashes)

- **git stash list** - list all stashed items

- **git stash show {stash@{number}}** - show perticular stashed item

- **git stash pop {stash@{number}}** - pop perticular stashed item

- **git stash -u** -  covers untracked files as well from working tree

- **git stash -a** -  covers ignored files as well

- **git stash pop** -  remove changes from stash and reapply to working copy

- **git stash apply** -  keep changes in stash and reapply to working copy
