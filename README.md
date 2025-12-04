# 📘 **ALX Advanced GitFlow Project**

This repository contains my work for the **ALX ProDev Backend – Advanced Git Techniques & GitFlow Workflow** project.
The goal of this project is to practice **professional Git workflows** including Git-Flow, feature isolation, release management, hotfixing, Git hooks, and collaborative branching strategies.

---

# 🚀 **Project Overview**

Git-Flow is a branching model that helps organize large codebases and coordinate multiple developers working simultaneously.
It separates production-ready code, ongoing development, features, releases, and urgent fixes into well-defined branches.

For this project, I implemented:

* Proper branch structure (`main`, `develop`, `feature/*`, `release/*`)
* Git-Flow initialization
* Feature development using feature branches
* Release branching and tagging
* Git hooks automation
* Clean commit messages and workflow discipline

---

# 🧩 **Repository Structure**

```
ALXprodev-advanced_git/
│
├── README.md                     # Project documentation
├── login-page/
│   └── README.md                 # Login feature placeholder
├── signup-page/
│   └── README.md                 # Signup feature placeholder + data requirements
└── merge.log                     # Auto-generated merge history log
```

---

# 🏗️ **What Was Implemented**

## ✅ 1. GitFlow Setup

Inside the newly created GitHub repository, the workflow was initialized:

* Created and pushed the `develop` branch
* Initialized GitFlow with default settings:

```bash
git flow init -d
```

* Added a base README.md

This established the required branch structure used by all future tasks.

---

## ✅ 2. Feature Development (Feature Branching)

### **Feature 1: implement-login**

A new feature branch was created:

```bash
git flow feature start implement-login
```

Inside this branch:

* `login-page/` directory was created
* A placeholder README.md was added containing:

  ```
  Login Feature Coming soon
  ```

Commit message used:

```
feat: scaffolding login page
```

Feature branch pushed to GitHub.

---

### **Feature 2: implement-signup**

```bash
git flow feature start implement-signup
```

Inside this branch:

* `signup-page/` directory created
* `README.md` added with:

  ```
  feature coming soon
  ```

Both feature branches were later merged into the `develop` branch.

---

## 🧪 **3. Release Branch Creation and Preparation**

Once both features were merged, a release branch was created:

```bash
git flow release start 1.0.0
```

Inside this branch:

* The signup README was updated with required data fields:

  ```
  data requirements: email, firstName, lastName, profilePic
  ```

These changes simulate last-minute release preparation tasks such as documentation improvements, metadata updates, and cleanup.

### Release completion:

```bash
git flow release finish 1.0.0
```

This automatically:

* merged the release into `main`
* merged the release into `develop`
* created a Git tag
* asked for a tag message

Finally, tags were pushed:

```bash
git push --tags
```

---

# 🧷 **4. Git Hooks Automation**

Git hooks were added to automate common quality checks.

---

## 🔒 **Pre-Commit Hook**

**File:** `.git/hooks/pre-commit`

This hook checks whether **every directory in the repository contains a README.md file**.
If any directory is missing a README, the commit is blocked.

Purpose:

* Enforce documentation standards
* Prevent undocumented folders from entering the repo

The hook prints an error and stops the commit if the rule is violated.

---

## 📝 **Post-Merge Hook**

**File:** `.git/hooks/post-merge`

When a merge is completed into the `main` branch, the hook automatically records:

* the timestamp
* a message indicating a merge occurred

Logged into:

```
merge.log
```

Purpose:

* Maintain a local auto-generated merge history
* Useful for debugging, auditing, and deployment tracking

---

# 🧠 **Key GitFlow Commands Used**

| Purpose            | Command                                        |
| ------------------ | ---------------------------------------------- |
| Initialize GitFlow | `git flow init -d`                             |
| Start feature      | `git flow feature start <name>`                |
| Finish feature     | `git flow feature finish <name>`               |
| Start release      | `git flow release start <version>`             |
| Finish release     | `git flow release finish <version>`            |
| Create a tag       | `git tag -a v1.0.0 -m "Release version 1.0.0"` |
| Push tags          | `git push --tags`                              |

---

# 🤝 **Why GitFlow Matters**

This workflow teaches:

* Structured development practices
* Cleaner code integration
* Improved collaboration
* Controlled release cycles
* Reduced merge conflicts
* Proper version tagging
* Safe hotfix application

Understanding GitFlow is essential for backend teams, DevOps cycles, and CI/CD pipelines.

---

# 📦 **Final Result**

By the end of this project, the repository contains:

### ✔ Git-Flow initialized

### ✔ Feature branches properly created and merged

### ✔ Release branch completed and tagged

### ✔ Auto-generated logging from Git hooks

### ✔ Clear and professional project documentation

This reflects a production-ready branching strategy used in real software engineering teams.

---

# 🎉 **Completed for ALX ProDev Backend (Month 2)**

This submission fulfills all mandatory requirements and demonstrates understanding of:

* Advanced Git Concepts
* Feature isolation
* Release pipelines
* Git hooks automation
* Professional Git workflows

---
