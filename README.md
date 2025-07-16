# Safety-Net
> 🛠️ **A practical Git workflow simulation project**

This project simulates real-world Git workflows, covering cloning, branching, merging, cherry-picking, restoring files, and creating releases — all essential skills for collaborative software development.

> ✅ **Focus:** Strengthening my Git expertise through hands-on version control scenarios.  
> ✅ **Status:** Completed (7 Stages)

---

## 📌 Key Git Concepts Practiced
- Cloning repositories
- Working with remote and local branches
- Feature development in isolated branches
- Merging and fast-forward merges
- Cherry-picking commits
- Restoring files to a previous commit
- Rebasing for clean history
- Creating release branches
- Fixing bugs before production release

---

## 🚀 Stages Overview
| Stage | Task                  | Git Skills Applied          |
|-------|-----------------------|-----------------------------|
| 1     | Clone & Switch Branch | `git clone`, `git checkout` |
| 2     | New Feature Branch     | `git branch`, `git commit`  |
| 3     | Merge & Delete         | `git merge`, `git branch -d`|
| 4     | Cherry-pick            | `git cherry-pick`, `git reset`|
| 5     | Restore File State     | `git checkout <commit> <file>`|
| 6     | Merge After Rebase     | `git rebase`, `git merge`   |
| 7     | Release & Bug Fix      | `git branch`, `git commit`  |

---

## 💡 Example Git Commands
```bash
# Clone repository
git clone https://github.com/hyperskill-content/Safety-net-study-repository.git
# Create and switch branches
git checkout -b feature/math origin/0.2.x-dev
# Commit new feature
git commit -m "feat: new function addition"
# Merge feature branch into main
git merge feature/math
```

### 🔗 Project Source
[View the Hyperskill project description here](https://hyperskill.org/projects/500)

For detailed solutions by stage, see 👉 **[STAGES.md](STAGES.md)**
