# ALXprodev-advanced_git

---

# 🚀 **Using GitHub Codespaces for Your GitFlow Project**

## **STEP 1 — Create the Repository**

On GitHub make:

```
ALXprodev-advanced_git
```

---

# ✅ **STEP 2 — Open in Codespace**

On your repo page:

**Code → Codespaces → Create codespace on main**

A full VS Code environment will open in your browser.

---

# 🧩 **STEP 3 — Install Git-Flow (inside Codespace)**

Most Codespaces images already have Git installed, but not Git-Flow.
Install it using:

```bash
sudo apt update
sudo apt install git-flow
```

Confirm installation:

```bash
git flow version
```

---

# ✅ **STEP 4 — Complete Project Tasks (Codespace Commands)**

Everything below goes directly in the Codespace terminal.

---

# 🔵 **TASK 0 – Setting Up GitFlow**

### **Clone the repo (already done automatically by Codespaces)**

When you open a Codespace, your repo is already cloned into `/workspaces/ALXprodev-advanced_git`.

Just go inside it:

```bash
cd /workspaces/ALXprodev-advanced_git
```

---

### **Create develop branch**

```bash
git checkout -b develop
git push -u origin develop
```

---

### **Initialize GitFlow**

```bash
git flow init -d
```

---

### **Create README**

```bash
echo "# ALX Advanced GitFlow Project" > README.md
git add README.md
git commit -m "chore: initial README"
git push
```

---

# 🟣 **TASK 1 — Feature Branch (implement-login)**

### Create the feature branch

```bash
git flow feature start implement-login
```

### Add directory + README

```bash
mkdir login-page
echo "Login Feature Coming soon" > login-page/README.md
```

### Commit + push

```bash
git add .
git commit -m "feat: scaffolding login page"
git push -u origin feature/implement-login
```

---

# 🟢 **TASK 2 — Release Branch**

### Create signup feature

```bash
git flow feature start implement-signup
mkdir signup-page
echo "feature coming soon" > signup-page/README.md
git add .
git commit -m "feat: scaffolding signup page"
git push -u origin feature/implement-signup
```

---

### Merge features back into develop

```bash
git checkout develop
git merge feature/implement-login
git merge feature/implement-signup
git push
```

Fix conflicts if needed:

```bash
# After fixing:
git add .
git commit
```

---

### Create release branch

```bash
git flow release start 1.0.0
```

---

### Update signup README inside release branch

```bash
echo "data requirements: email, firstName, lastName, profilePic" >> signup-page/README.md
git add signup-page/README.md
git commit -m "docs: add signup data requirements"
git push -u origin release/1.0.0
```

---

### Finish release (GitFlow auto-merges into main + develop)

```bash
git flow release finish 1.0.0
git push
git push --tags
```

---

# 🟡 **TASK 3 — Git Hooks (Codespaces-Safe Version)**

Git hooks live in:

```
.git/hooks/
```

In Codespaces the `.git` folder is accessible normally.

---

## **1️⃣ Pre-commit Hook**

Create the file:

```bash
nano .git/hooks/pre-commit
```

Paste this:

```bash
#!/bin/bash

echo "Running pre-commit checks..."

missing=0

for dir in */ ; do
    if [[ "$dir" == ".git/" ]]; then
        continue
    fi

    if [[ ! -f "${dir}README.md" ]]; then
        echo "❌ Missing README in: $dir"
        missing=1
    fi
done

if [[ $missing -eq 1 ]]; then
    echo "Commit aborted."
    exit 1
fi

echo "✅ Pre-commit OK"
exit 0
```

Save → exit → make executable:

```bash
chmod +x .git/hooks/pre-commit
```

---

## **2️⃣ Post-merge Hook**

Create:

```bash
nano .git/hooks/post-merge
```

Paste:

```bash
#!/bin/bash

branch=$(git rev-parse --abbrev-ref HEAD)

if [[ "$branch" == "main" ]]; then
    echo "$(date): Merge completed on main" >> merge.log
    echo "📝 merge.log updated"
fi
```

Make executable:

```bash
chmod +x .git/hooks/post-merge
```

---

# 🎉 YOU ARE DONE!

From here:

✔ Commit everything
✔ Push to GitHub
✔ Generate project submission link
✔ Request manual QA review

---

