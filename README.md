# GitHub Workflow Cheatsheet

## ✅ Pre-requisites

- Git installed: `git --version`
- GitHub account created: [github.com](https://github.com)
- Git configured (only once):

```bash
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
```

---

## 🚀 Step 1 — Initial Setup 

```bash
git init
git remote add origin https://github.com/YOUR_USERNAME/YOUR_PROJECT_NAME.git
git branch -M main
git add .
git commit -m "Initial commit for YOUR_PROJECT_NAME"
git push -u origin main
```

### কমান্ড ব্যাখ্যা:

| Command | কাজ |
|--------|------|
| `git init` | Local folder-কে Git repository বানায় |
| `git remote add origin <url>` | GitHub-এর remote repo-র সাথে connect করে |
| `git branch -M main` | Default branch-এর নাম `main` করে |
| `git add .` | সব file stage করে (track করার জন্য প্রস্তুত) |
| `git commit -m "message"` | Staged files-এ একটা snapshot নেয় |
| `git push -u origin main` | প্রথমবার GitHub-এ push করে এবং tracking set করে |

> ⚠️ `YOUR_USERNAME` এবং `YOUR_PROJECT_NAME` replace করতে ভুলবে না।  
> ⚠️ GitHub-এ আগে repository তৈরি করতে হবে (Initialize without README)।

---

## 🔄 Step 2 — Regular Update (পরবর্তী প্রতিটা Push)

```bash
git add .
git commit -m "Your commit message here"
git push origin main
```

### কমান্ড ব্যাখ্যা:

| Command | কাজ |
|--------|------|
| `git add .` | নতুন ও পরিবর্তিত সব file stage করে |
| `git commit -m "message"` | Change-এর description সহ commit করে |
| `git push origin main` | GitHub-এ push করে |

> 💡 Commit message-এ meaningful কিছু লেখো, যেমন:  
> `"Add product search feature"` বা `"Fix invoice total bug"`

---

## 🔍 Useful Extra Commands

```bash
# Current status দেখো (কোন file changed, staged, untracked)
git status

# Commit history দেখো
git log --oneline

# Remote URL চেক করো
git remote -v

# Latest changes GitHub থেকে Pull করো
git pull origin main

# Specific file stage করো (সব না)
git add filename.txt
```

---

## ⚠️ Common Errors & Fix

| Error | কারণ | সমাধান |
|-------|------|--------|
| `remote origin already exists` | Remote আগে থেকেই add করা | `git remote set-url origin <new-url>` |
| `failed to push — non-fast-forward` | Remote-এ নতুন commit আছে | আগে `git pull origin main` করো |
| `Permission denied (publickey)` | SSH key নেই | HTTPS URL ব্যবহার করো অথবা SSH key set করো |
| `src refspec main does not match any` | কোনো commit নেই | আগে `git add .` ও `git commit` করো |

---

## 🔐 Authentication

GitHub এখন **password support বন্ধ** করে দিয়েছে। এর বদলে ব্যবহার করো:

**Option 1 — Personal Access Token (PAT) — সহজ:**
1. GitHub → Settings → Developer Settings → Personal Access Tokens → Generate New Token
2. Push করার সময় password-এর জায়গায় এই token ব্যবহার করো

**Option 2 — SSH Key — একবার setup, বারবার ব্যবহার:**
```bash
ssh-keygen -t ed25519 -C "your@email.com"
# Public key (~/.ssh/id_ed25519.pub) GitHub-এ add করো
# Settings → SSH and GPG Keys → New SSH Key
```

---

## 📁 .gitignore (Important!)

কিছু file GitHub-এ push করা উচিত না। Project root-এ `.gitignore` file বানাও:

```
# Environment variables
.env
.env.local

# Dependencies
node_modules/
vendor/

# Database files
*.sqlite
*.db

# OS files
.DS_Store
Thumbs.db

# IDE files
.idea/
.vscode/
```

---

*Last updated: June 2026*
