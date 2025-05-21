# 🚀 Advanced Git Version Control System Guide

This document explains advanced Git commands and workflows as depicted in the shared visuals. These techniques are crucial for managing complex codebases, resolving conflicts, and collaborating effectively.

---

## 📂 Table of Contents

1. Git Branching and Merging
2. Git Rebase (Interactive & Regular)
3. Git Cherry-pick
4. Git Reflog & Recovery
5. Conflict Resolution
6. Git Stash
7. Git Tagging
8. Git Clean & Reset

---

## 1⃣ Git Branching and Merging

Git branching allows you to work on different features or fixes in isolated environments.

```bash
git checkout -b feature/login
# Work on the branch, then merge
git checkout main
git merge feature/login
```

Use `--no-ff` for explicit merge commits:

```bash
git merge --no-ff feature/login
```

<!-- No image provided for this section -->

---

## 2⃣ Git Rebase (Regular and Interactive)

### Regular Rebase

Rebase lets you move or combine a sequence of commits to a new base commit.

```bash
git checkout feature
git rebase main
```

This reapplies your feature branch commits on top of main for a linear history.

![Rebase](https://github.com/user-attachments/assets/ef153459-67d4-4430-91bc-10a581f57d1b)

### Interactive Rebase

Useful for editing, squashing, or reordering commits:

```bash
git rebase -i HEAD~3
```

Options include:
- pick: use commit
- squash: merge with previous
- reword: change commit message
- drop: remove commit

![Interactive Rebase](https://github.com/user-attachments/assets/715b1a73-3288-453b-a612-2da916abc375)

---

## 3⃣ Git Cherry-pick

Cherry-pick allows you to apply a specific commit from one branch to another.

```bash
git checkout main
git cherry-pick <commit-hash>
```

Useful when you want to apply a hotfix or isolated change without merging the entire branch.

![Cherry Pick](https://github.com/user-attachments/assets/1355085c-6d91-41f0-b341-a959726295bc)

---

## 4⃣ Git Reflog – Restore Lost Commits

Use `git reflog` to recover deleted or lost commits.

```bash
git reflog
git checkout <commit-hash>
# Or create a new branch
git checkout -b recovered-branch <commit-hash>
```

![Reflog](https://github.com/user-attachments/assets/f6f270c2-69e0-47e3-b9d4-2d45ad05a08e)

---

## 5⃣ Conflict Resolution

When Git cannot auto-merge changes, a conflict occurs. You'll see:

```bash
<<<<<<< HEAD
Your changes
=======
Incoming changes
>>>>>>> branch-name
```

Steps to resolve:

1. Manually edit the file
2. Stage resolved file:
   ```bash
   git add <file>
   ```
3. Continue rebase or merge:
   ```bash
   git rebase --continue
   # or
   git commit
   ```

Abort a rebase/merge if needed:

```bash
git rebase --abort
git merge --abort
```

![Conflict Resolution](https://github.com/user-attachments/assets/73166094-8dfb-4609-9075-702b82c3de1a)

---

## 6⃣ Git Stash – Temporary Save

Stash your current changes without committing:

```bash
git stash
```

Apply stashed changes later:

```bash
git stash apply
```

List all stashes:

```bash
git stash list
```

Drop or pop a stash:

```bash
git stash drop
git stash pop
```

![Git Stash](https://github.com/user-attachments/assets/eddfe452-1016-40bc-a112-b7893857edff)

---

## 7⃣ Git Tagging – Marking Releases

Lightweight and annotated tags are used for marking release points.

```bash
git tag v1.0.0        # Lightweight
git tag -a v1.0.0 -m "Release v1.0.0"   # Annotated
git push origin --tags
```

<!-- No image provided for this section -->

---

## 8⃣ Git Clean and Reset

To remove untracked files:

```bash
git clean -f
```

Reset working directory:

```bash
git reset --hard HEAD
```

Undo local commits:

```bash
git reset --soft HEAD~1     # Keep changes staged
git reset --mixed HEAD~1    # Keep changes unstaged
git reset --hard HEAD~1     # Discard changes
```

![Git Clean and Reset](https://github.com/user-attachments/assets/2c076dd3-94ac-4d3b-bef5-7996329aa5a5)

---

## 🧠 Pro Tips

- Use aliases for convenience:
  ```bash
  git config --global alias.s "status"
  git config --global alias.co "checkout"
  git config --global alias.cm "commit"
  ```

- Combine logs with graph:
  ```bash
  git log --oneline --graph --all
  ```

---
<section class="section">
  <h2>📸 Sample Output</h2>
  <p>Here's a visual output of the Git commands or workflow from the terminal:</p>
  <img src="https://github.com/user-attachments/assets/3f85d5d2-efc0-4710-8614-2a97acd5fa5e" alt="Git Output Screenshot">
</section>


## 📌 Final Thoughts

Advanced Git workflows are essential for efficient collaboration, especially on large teams. Mastering rebase, stash, cherry-pick, and reflog ensures you can recover, modify, and enhance your codebase with confidence.

Happy committing! 🚀
