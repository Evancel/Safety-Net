# Safety-Net
the second project to work with Git commands

## Work on project. Stage 1/7:Clone and switch

### Description
In modern software development, managing code versions, collaborating with others, and keeping track of changes is essential. Git, a widely used version control system, allows developers to do just that. In this stage, you will start by setting up a local copy of a remote Git repository. This is a common first step when joining a new project or contributing to an existing one. You will clone a repository, fetch all remote branches, switch to a specific development branch, and verify that all the needed branches are available.

By completing this stage, you will have a local repository synchronized with the remote repository. This way, you will ensure you are working with the latest code and on the correct branch. These steps are critical in real-world projects where multiple developers collaborate and work on different branches simultaneously.

You may corrupt the repository while working on this project. It may be helpful to understand the status of the repository and branches. The commands git branch --all and git log --oneline can help you view branches and the commit history. If you want to start over, you can clone the repository again.

### Objectives
Let's break this task into steps:

Open a terminal and clone the remote Git repository to your local machine at the project root. This will create a local copy of the remote repository. You can use either SSH or HTTPS:

For SSH: git@github.com:hyperskill-content/Safety-net-study-repository.git

For HTTPS: https://github.com/hyperskill-content/Safety-net-study-repository.git

After cloning, move into the newly created repository directory to work with the project files.

Switch to the development branch 0.2.x-dev to work on the latest development code. Ensure you create a local copy from the remote.

List all available branches in your local repository to confirm that the correct branches are present.

### Solution:
 $ git clone https://github.com/hyperskill-content/Safety-net-study-repository.git  
 $ dir
 $ cd "Safety-net-study-repository"
 $ git checkout -b 0.2.x-dev origin/0.2.x-dev
 $ git branch -a


 ## Work on project. Stage 2/7:New feature
 ### Description
In this stage, you will delve deeper into feature development. In our project, new features are developed in isolated branches to avoid conflicts with the main codebase. This approach is critical for maintaining code stability and ensuring that new features are thoroughly tested before being merged into the main branch.

Your task is to create a new feature branch from an existing development branch, create a new file, implement a simple mathematical function, and commit the changes. This process mirrors real-world software development practices where teams work on new features in separate branches and merge them together when done.

### Objectives
Let's break this task into steps:

Create a new branch named feature/math from the existing 0.2.x-dev branch. This branch will serve as the isolated environment where you will add new functionality. Ensure that this new branch is active before proceeding to the next steps.

In the newly created feature/math branch, create a file named math_operations.py in the root directory of the project.

The file should contain a basic mathematical function that performs the addition of two integers and returns the result:

def addition(a, b):
    return a + b

Stage and commit the changes with the commit message: feat: new function addition
At this point, there should be a total of 4 commits in the feature/math branch, including the one you just made.

### Solution:
$ git checkout 0.2.x-dev
$ git branch feature/math
$ git checkout feature/math
$ git status
$ git add .
$ git commit -m "feat: new function addition"

## Work on project. Stage 3/7:Merge and Delete
### Description
Congratulations on successfully developing your feature in the feature/math branch! Since your new feature has passed all tests and reviews, it's time to show the world what you've been working on. In this stage, you will integrate your new feature into the main codebase.

Because the main branch hasn't been modified since you branched off, the merge will be a fast-forward merge. This type of merge simply moves the branch pointer forward to include the new commits without creating a merge commit. Once the merge is complete, you'll clean up by deleting the feature/math branch, as it's no longer needed.

### Objectives
Let's break this task into a few steps:

Switch to the main branch. This is the branch where the production-ready version of the project is stored.

Merge feature/math into the main. This will integrate the new file containing the new feature into the main codebase.

Delete the feature/math branch as it's no longer needed. This helps keep the repository clean and avoids clutter from unused branches.

Examples
Example 1: Merging the feature/math branch into the main branch:
$ git <command>
Updating d2d1138..ffd209d
Fast-forward
 main.py            | 24 ++++++++++++++++++++++++
 math_operations.py |  2 ++
 2 files changed, 26 insertions(+)
 create mode 100644 math_operations.py

 Example 2: Verifying the branch deletion.
 $ git branch
  0.2.x-dev
* main

  ### Solution:
  $ git checkout main
  $ git merge feature/math
  $ git branch -d feature/math
  $ git branch

  ## Work on project. Stage 4/7:Cherry-pick
  ### Description
Typically, features are merged into development branches rather than directly into the main branch. This branch is reserved for production-ready code. Since feature/math was designated a feature branch, we should have merged it into the 0.2.x-dev development branch instead of the main branch.

In this stage, you will correct this mistake. You will use Git's cherry-pick command to transfer the necessary commit from main to 0.2.x-dev and then reset the main branch to its original state, ensuring that only the initial commit remains. This is a common task in real-world projects when managing multiple branches.

When you reset the main branch, only the feat: Initial commit should remain.

### Objectives
Let's break this task into a few steps:

Switch to the 0.2.x-dev branch: this is your development branch, where new features should be integrated. Ensure that you are working from this branch before proceeding;

Cherry-pick the last commit from the main branch: use the appropriate command to transfer the most recent commit from main to 0.2.x-dev. This will allow the feature to be correctly integrated into the development branch.

After cherry-picking the commit, return to the main branch to prepare for the reset;

Reset the main branch to its original state: reset the main branch to the state it was in before the last merge, leaving only the initial commit (feat: Initial).

Examples
Example 1: Resetting the main branch to its original state:

$ git <command>
HEAD is now at abc123 feat: Initial

Example 2: Verifying the commit history in the main branch:

$ git log --oneline
abc123 feat: Initial

Example 3: Verifying the commit history in the 0.2.x-dev branch:

$ git log --oneline
1f2d3e4 feat: new function addition
4g5h6i7 feat: new function get_letters
7j8k9l0 feat: new function get_numbers
abc123 feat: Initial

 ### Solution:
 $ git checkout 0.2.x-dev
 $ git show
 $ git cherry-pick 1f2d3e4
 $ git checkout main
 $ git reset --hard abc123

 ## Work on project. Stage 5/7:Restore
 ### Description
Now that your main codebase is stable, let's focus on another essential task in collaborative software development: restoring files to a previous state. This is a common scenario when unwanted or incorrect changes have been introduced into a codebase. You may often need to revert specific files or entire sections of a project back to a known, stable version. This ability to "undo" changes is crucial in maintaining code quality and stability, especially when working with multiple collaborators on a shared repository.

Your colleagues have accidentally introduced unrequested features into the feature/case branch. Your task is to help them by restoring the case_operations.py file to a previous commit and committing the changes with a clear and descriptive message.

### Objectives
Let's break this task into clear steps:

Switch to the feature/case branch: create a local copy of feature/case from the remote repository.

Restore case_operations.py to a previous state: using the commit 6b2ec72, restore the file case_operations.py to its state from that commit. This will undo changes that were made from that point.

Commit the changes: after restoring the file, stage and commit the changes with the following commit message: refactor: restored case operations from 6b2ec72.

Verify the branch: ensure that the feature/case branch contains the correct number of commits and that the restored file matches the content from the 6b2ec72 commit.

 ### Solution:
 $ git branch feature/case origin/feature/case
 $ git checkout 6b2ec72 case_operations.py
 $ git add .
 $ git commt -m "refactor: restored case operations from 6b2ec72"
 $ git log

## Work on project. Stage 6/7:Another feature
### Description
In collaborative software development, completing a feature is only part of the process. Once the feature is ready, it must be integrated into the main development branch to ensure that all team members can access the updated code. Merging feature branches into the development branch is a common practice that helps maintain a clean, organized repository while ensuring that the latest features are available for further testing and development.

In this stage, you will finalize your work on the feature/case branch by merging it into the 0.2.x-dev development branch. After merging, the feature/case branch will no longer be needed, so you will delete it to keep the repository clean. Finally, you will verify that the merge was successful and that the repository is in the correct state.

This process mirrors real-world software development, where teams frequently merge feature branches into development branches to integrate new code while maintaining a clean, streamlined repository.

### Objectives
To complete this stage, you need to follow these steps:

Rebase the feature/case branch with 0.2.x-dev: before merging, rebase the feature/case branch with the 0.2.x-dev branch to ensure that it includes the latest changes from the development branch. This is necessary to avoid conflicts and ensure that the feature branch is up to date.

Switch to the 0.2.x-dev branch: after rebasing, switch to the 0.2.x-dev branch. This is the development branch where the latest features are integrated.

Merge the feature/case branch into 0.2.x-dev: perform the merge operation to integrate the changes from the feature/case branch into the 0.2.x-dev branch. This will bring the new feature into the development branch without creating a separate merge commit.

Delete the feature/case branch: once the merge is complete, delete the feature/case branch. This helps keep the repository clean by removing branches that are no longer needed.

Verify the repository state: ensure that the 0.2.x-dev branch now contains the commits from the feature/case branch and that the feature/case branch has been successfully deleted.

### Solution:
$ git checkout feature/case
$ git rebase 0.2.x-dev
$ git checkout 0.2.x-dev
$ git merge feature/case
$ git branch -D feature/case
$ git show
$ git status
$ git branch


## Work on project. Stage 7/7:Release
### Description
Creating a release branch is an essential step in preparing your project for production. It allows you to freeze the current state of your development branch and focus on final testing and bug fixing before deploying the code to production. This ensures the code is stable, thoroughly tested, and ready for release.

In this stage, you will create a release branch from the development branch (0.2.x-dev). During testing, you discover and fix a bug in the make_upper function, which incorrectly prints the output instead of returning it. After fixing the bug, you will commit the changes, ensuring your project is ready for production deployment.

This process reflects real-world scenarios where developers create release branches to isolate production-ready code and address any last-minute issues before going live.

### Objectives
To complete this stage, you need to follow these steps:

Create a release branch (0.2.x): create a new branch named 0.2.x from the 0.2.x-dev branch. This branch will serve as the release branch, containing the final version of the code that will be deployed to production;

Fix the bug in the make_upper function: in the case_operations.py file, the make_upper function currently prints the uppercase version of the text instead of returning it. Modify the function so that it returns the uppercase text, as shown in the provided code snippet:

def make_upper(text):
    return text.upper()

Commit the bug fix: after fixing the bug, commit the changes to the 0.2.x branch with the commit message: fix: bug-fix make_upper.

Verify the repository: ensure that the 0.2.x branch contains the correct number of commits (9 commits in total, including the bug fix), and that the make_upper function has been correctly updated.

Your project is now prepared for production deployment.
 
### Solution:
$ git checkout 0.2.x-dev
$ git branch 0.2.x
$ git checkout 0.2.x
$ git add .
$ git commit -m "fix: bug-fix make_upper"
$ git show
