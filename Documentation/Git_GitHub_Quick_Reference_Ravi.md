# Git + GitHub Quick Reference

A practical reference for using Git and GitHub with Jupyter Notebook, Python, SQL, Power BI, and Machine Learning projects.

---

## 1. My GitHub Setup

**GitHub Username:** `Ravi-Raj-Singh-2022`

**Repository:** `python_ML_practise`

**Repository URL:**  
https://github.com/Ravi-Raj-Singh-2022/python_ML_practise

**Local Project Folder:**

```text
/Users/ravirajsingh/Documents/data-analytics-learning
```

**Current Branch:** `main`

---

## 2. Git vs GitHub

**Git** is a version control system that tracks changes locally.

**GitHub** is an online platform where Git repositories can be stored, shared, and collaborated on.

### Basic Flow

```text
Your Jupyter Notebook
        ↓
     git add
        ↓
   Staging Area
        ↓
   git commit
        ↓
   Local Git
        ↓
     git push
        ↓
      GitHub
```

---

## 3. Check Git Installation

```bash
git --version
```

Example:

```text
git version 2.50.1
```

---

## 4. Create a Git Repository

Go to your project folder:

```bash
cd ~/Documents/data-analytics-learning
```

Initialize Git:

```bash
git init
```

> Run `git init` only once when starting a new local Git repository.

---

## 5. Check Repository Status

```bash
git status
```

This tells you the current branch, modified files, untracked files, staged files, and whether your working tree is clean.

---

## 6. .gitignore

`.gitignore` tells Git which files should not be tracked.

Example:

```text
.DS_Store
__pycache__/
*.pyc
.ipynb_checkpoints/
.env
venv/
.venv/
```

Create a basic macOS `.gitignore`:

```bash
echo ".DS_Store" > .gitignore
```

### Never commit

- Passwords
- API keys
- GitHub tokens
- Database credentials
- `.env` files containing secrets

---

## 7. Add Files to Git

### Add everything

```bash
git add .
```

### Add one file

```bash
git add Python/Day_01/Python_ChatGPT_Practise.ipynb
```

### Add a folder

```bash
git add Documentation/
```

`git add` moves changes into the staging area.

---

## 8. Commit Changes

```bash
git commit -m "Add Python Day 1 practice"
```

Good examples:

```bash
git commit -m "Complete Python Day 2 loops practice"
git commit -m "Add SQL window functions practice"
git commit -m "Update Power BI sales dashboard"
git commit -m "Add customer segmentation project"
```

---

## 9. Connect Local Repository to GitHub

Example:

```bash
git remote add origin https://github.com/Ravi-Raj-Singh-2022/python_ML_practise.git
```

Check the connection:

```bash
git remote -v
```

Expected:

```text
origin  https://github.com/Ravi-Raj-Singh-2022/python_ML_practise.git (fetch)
origin  https://github.com/Ravi-Raj-Singh-2022/python_ML_practise.git (push)
```

---

## 10. First Push

For a new local repository:

```bash
git branch -M main
git push -u origin main
```

After the upstream is configured, normally use:

```bash
git push
```

---

## 11. Daily Jupyter → GitHub Workflow ⭐

Work directly inside your Git project folder:

```text
data-analytics-learning/
└── Python/
    └── Day_02/
        └── Day_02_Loops.ipynb
```

After saving your Jupyter notebook:

```bash
cd ~/Documents/data-analytics-learning
git status
git add .
git commit -m "Complete Python Day 2 loops practice"
git push
```

### Remember

```text
Save
  ↓
git status
  ↓
git add .
  ↓
git commit -m "message"
  ↓
git push
```

---

## 12. Pull Changes from GitHub

```bash
git pull
```

Think:

```text
GitHub
  ↓
git pull
  ↓
Your Mac
```

Whereas:

```text
Your Mac
  ↓
git push
  ↓
GitHub
```

---

## 13. Clone an Existing Repository

```bash
git clone REPOSITORY_URL
```

Example:

```bash
git clone https://github.com/Ravi-Raj-Singh-2022/python_ML_practise.git
```

Then:

```bash
cd python_ML_practise
```

> You do not need `git init` after `git clone`.

---

## 14. Branches — Professional Work ⭐

In many professional projects, avoid working directly on `main`.

Create a feature branch:

```bash
git switch -c feature/customer-analysis
```

Or:

```bash
git checkout -b feature/customer-analysis
```

Then:

```bash
git add .
git commit -m "Add customer analysis"
git push -u origin feature/customer-analysis
```

Then create a Pull Request on GitHub to merge the branch into `main`.

---

## 15. View Branches

```bash
git branch
```

Example:

```text
* feature/customer-analysis
  main
```

The `*` indicates the current branch.

---

## 16. Switch Branches

```bash
git switch main
```

Switch to a feature branch:

```bash
git switch feature/customer-analysis
```

---

## 17. View Commit History

Full history:

```bash
git log
```

Short history:

```bash
git log --oneline
```

---

## 18. See Changes Before Committing

```bash
git diff
```

---

## 19. Unstage Files

If you accidentally run:

```bash
git add .
```

and want to unstage everything:

```bash
git restore --staged .
```

---

## 20. Discard Local Changes ⚠️

To discard uncommitted changes to a specific file:

```bash
git restore filename.py
```

> Be careful: this can permanently discard uncommitted changes.

---

## 21. Common Git Errors

### Authentication failed

GitHub does not accept your normal GitHub password for Git over HTTPS.

Use an appropriate authentication method such as a Personal Access Token or SSH.

Never share your token.

### `rejected - fetch first`

The remote repository contains changes that your local repository does not have.

Usually:

```bash
git pull
```

Then:

```bash
git push
```

If Git reports a merge conflict, resolve it before pushing.

### `fatal: not a git repository`

Check:

```bash
pwd
git status
```

Move to the correct project folder:

```bash
cd ~/Documents/data-analytics-learning
```

### `nothing to commit`

There are no new changes to commit.

Check:

```bash
git status
```

### Git opens Vim during a merge

Save and exit:

```text
Esc
:wq
Enter
```

Exit without saving:

```text
Esc
:q!
Enter
```

---

## 22. Recommended Repository Structure

```text
python_ML_practise/
│
├── README.md
├── .gitignore
│
├── Documentation/
│   ├── Git_GitHub_Quick_Reference_Ravi.docx
│   └── Git_GitHub_Quick_Reference_Ravi.md
│
├── Python/
│   ├── Day_01/
│   ├── Day_02/
│   ├── Day_03/
│   └── Projects/
│
├── SQL/
│   ├── Practice/
│   └── Projects/
│
├── PowerBI/
│   └── Projects/
│
└── Machine_Learning/
    ├── Practice/
    └── Projects/
```

### Recommended file types

```text
Python code/notebooks → .py / .ipynb
SQL practice           → .sql
Power BI               → .pbix
Documentation          → .md
Optional documents     → .docx / .pdf
```

---

## 23. Five Commands to Memorize ⭐⭐⭐

```bash
git status
git add .
git commit -m "your message"
git pull
git push
```

---

## 24. Your Current Project Commands

```bash
cd ~/Documents/data-analytics-learning
git status
git add .
git commit -m "Complete Python practice"
git push
```

To get the latest GitHub changes:

```bash
git pull
```

---

## 25. Golden Rule

For your normal learning workflow:

```text
Jupyter
  ↓
Save notebook
  ↓
git status
  ↓
git add .
  ↓
git commit -m "meaningful message"
  ↓
git push
  ↓
GitHub
```

For professional work:

```text
Clone repository
      ↓
Create branch
      ↓
Write / modify code
      ↓
git status
      ↓
git add
      ↓
git commit
      ↓
git push
      ↓
Pull Request
      ↓
Code Review
      ↓
Merge
```
