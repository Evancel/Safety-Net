
# 📌 Safety-Net Project Stages  
> A detailed breakdown of all project stages, descriptions, objectives, and solutions.

---

## ✅ Stage 1/7: Clone and Switch

### 📋 Description
In modern software development, managing code versions, collaborating with others, and tracking changes is essential. Git allows developers to achieve this effectively.

In this stage, you:
- Clone a remote Git repository
- Fetch all branches
- Switch to a development branch
- Verify available branches

> These steps reflect common practices when joining a new project.

### 🎯 Objectives
1. Clone the remote repository:
   - SSH:  
     `git@github.com:hyperskill-content/Safety-net-study-repository.git`
   - HTTPS:  
     `https://github.com/hyperskill-content/Safety-net-study-repository.git`
2. Move into the repository directory.
3. Switch to the `0.2.x-dev` branch.
4. List all available branches.

### 💻 Solution
```bash
git clone https://github.com/hyperskill-content/Safety-net-study-repository.git
dir
cd "Safety-net-study-repository"
git checkout -b 0.2.x-dev origin/0.2.x-dev
git branch -a
```

---

## ✅ Stage 2/7: New Feature

### 📋 Description
This stage simulates feature development in isolated branches to prevent conflicts and ensure stability.

### 🎯 Objectives
1. Create branch: `feature/math` from `0.2.x-dev`.
2. Create `math_operations.py` with:
```python
def addition(a, b):
    return a + b
```
3. Commit with message:  
`feat: new function addition`
4. Confirm 4 total commits.

### 💻 Solution
```bash
git checkout 0.2.x-dev
git branch feature/math
git checkout feature/math
git status
# create math_operations.py
git add .
git commit -m "feat: new function addition"
```

---

## ✅ Stage 3/7: Merge and Delete

### 📋 Description
Here you integrate the feature into the main codebase using a **fast-forward merge**. Then, clean up the branch.

### 🎯 Objectives
1. Switch to `main`.
2. Merge `feature/math` into `main`.
3. Delete `feature/math`.
4. Verify branches.

### 💻 Solution
```bash
git checkout main
git merge feature/math
git branch -d feature/math
git branch
```

---

## ✅ Stage 4/7: Cherry-pick

### 📋 Description
You mistakenly merged into `main` instead of `0.2.x-dev`. Correct this by cherry-picking the commit.

### 🎯 Objectives
1. Switch to `0.2.x-dev`.
2. Cherry-pick last commit from `main`.
3. Reset `main` to only the initial commit.

### 💻 Solution
```bash
git checkout 0.2.x-dev
git checkout main
git log --name-only    # get the commit hash
git cherry-pick HASH=?1f2d3e4
git commit -m "new function addition"
git checkout main
git log
git reset --hard abc123
```

---

## ✅ Stage 5/7: Restore

### 📋 Description
You restore a file to a previous state — a common task in collaborative work.

### 🎯 Objectives
1. Checkout `feature/case`.
2. Restore `case_operations.py` to commit `6b2ec72`.
3. Commit message:  
`refactor: restored case operations from 6b2ec72`

### 💻 Solution
```bash
git checkout feature/case
git checkout 6b2ec72 case_operations.py
git add .
git commit -m "refactor: restored case operations from 6b2ec72"
git log
```

---

## ✅ Stage 6/7: Another Feature

### 📋 Description
Rebase, merge, and clean up branches post-feature development.

### 🎯 Objectives
1. Rebase `feature/case` on `0.2.x-dev`.
2. Merge into `0.2.x-dev`.
3. Delete `feature/case`.
4. Verify repository state.

### 💻 Solution
```bash
git checkout feature/case
git rebase 0.2.x-dev
git checkout 0.2.x-dev
git merge feature/case
git branch -D feature/case
git show
git status
git branch
```

---

## ✅ Stage 7/7: Release

### 📋 Description
Create a **release branch** for production and fix a bug in `make_upper`.

### 🎯 Objectives
1. Create branch `0.2.x` from `0.2.x-dev`.
2. Fix in `case_operations.py`:
```python
def make_upper(text):
    return text.upper()
```
3. Commit message:  
`fix: bug-fix make_upper`
4. Verify 9 total commits.

### 💻 Solution
```bash
git checkout 0.2.x-dev
git branch 0.2.x
git checkout 0.2.x
# fix the file case_operations.py
git add .
git commit -m "fix: bug-fix make_upper"
git show
git checkout 0.2.x-dev
```

---
