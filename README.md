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

  
