## 🛠️ The Rebase Lab: "The Conflict Resolution"

### Phase 1: Setup the Divergence
Run these commands to create a repository where `main` and `feature` both edit the **same line** of a file.

```bash
mkdir rebase-lab && cd rebase-lab
git init

# Create the initial state
echo "Welcome to the App" > index.txt
git add index.txt
git commit -m "Initial commit"

# Create a feature branch and make a change
git checkout -b feature-header
echo "Welcome to the AMAZING App" > index.txt
git add index.txt
git commit -m "Update header text"

# Go back to main and simulate a 'remote' change
git checkout main
echo "Welcome to the Secure App" > index.txt
git add index.txt
git commit -m "Security update to header"
```

### Phase 2: The Goal
Your `feature-header` branch is now "behind" `main`. If you merge, you get a messy merge commit. Instead, we want to **rebase** so it looks like you started your work *after* the security update.

### Phase 3: The Exercise
1.  **Start the Rebase:**
    Switch to your feature branch and tell Git to rewrite its history based on `main`.
    ```bash
    git checkout feature-header
    git rebase main
    ```

2.  **Fix the Conflict:**
    Git will stop and say: *CONFLICT (content): Merge conflict in index.txt*.
    Open `index.txt`. You will see the conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`).
    * **Task:** Edit the file so it says: `"Welcome to the AMAZING Secure App"`.
    * Remove the Git markers.

3.  **Complete the Process:**
    Once the file is saved:
    ```bash
    git add index.txt
    git rebase --continue
    ```

## 🔍 How to check if you succeeded
Run this command to see your new, linear history:
```bash
git log --oneline --graph --all
```

**The Gold Standard:** You should see one straight line. Your "Update header text" commit should now be at the very top, sitting directly above the "Security update" commit.

### Pro-Tip for the future
If you ever get hopelessly lost during a rebase, you can always go back to safety with:
```bash
git rebase --abort
```

