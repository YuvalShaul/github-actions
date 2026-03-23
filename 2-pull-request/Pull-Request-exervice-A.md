## Pull-Request Lab Part 1: Setting up the Split-Identity Environment

### Phase 1: The Remote Base (GitHub)
1.  **Create the Repo:** Log into GitHub and create a new **Public** repository named `git-identity-lab`. 
2.  **Initialize:** Check the box to **Add a README file**.
3.  **Set the Rules (The "Wall"):**
    * Go to **Settings** > **Branches**.
    * Click **Add branch protection rule**.
    * Branch name pattern: `main`.
    * Check: **Require a pull request before merging**.
    * Click **Create**.
    > **Note:** This is the only way to "block" your own SSH user. Even though you own the repo, GitHub will now reject any direct push to `main`.


### Phase 2: The Local Workspace
We will create one parent folder to keep things clean, then clone the repo twice inside it.

```bash
# 1. Create a workspace and enter it
mkdir github-lab && cd github-lab

# 2. Clone as the "Maintainer"
git clone git@github.com:YOUR_USERNAME/git-identity-lab.git maintainer-dir

# 3. Clone as the "Contributor" 
git clone git@github.com:YOUR_USERNAME/git-identity-lab.git contributor-dir
```

### Phase 3: Identity Isolation (The "Secret Sauce")
Now we configure each directory locally. This ensures that even though you use one SSH key to "ship" the code, the "author" name on the commits will be different.

**Configure the Maintainer:**
```bash
cd maintainer-dir
git config --local user.name "Boss Maintainer"
git config --local user.email "boss@company.com"
cd ..
```

**Configure the Contributor:**
```bash
cd contributor-dir
git config --local user.name "Junior Developer"
git config --local user.email "junior@start-up.com"
cd ..
```

### Phase 4: Testing the "Wall"
To confirm your setup is correct, try to push directly to the protected `main` branch as the "Boss."

```bash
cd maintainer-dir
echo "Boss trying to bypass the rules" >> README.md
git add README.md
git commit -m "Direct push attempt"

# This should FAIL because of the Branch Protection rule you set in Phase 1
git push origin main
```

**Expected Error:**
`remote: error: GH006: Protected branch update failed for refs/heads/main.`
`remote: error: At least 1 approving review is required by reviewers with write access.`

Undo the local commit from main:  
```
# This points your local branch back to exactly where the server (origin) is
git reset --hard origin/main
```

### Phase 5: Preparing for the PR
Since we can't push to `main`, we must prepare a feature branch in the contributor directory.

```bash
cd ../contributor-dir
git checkout -b feature-update
echo "Junior dev adding a cool feature" >> README.md
git add README.md
git commit -m "Added feature update"

# This will SUCCEED because protection rules usually only apply to 'main'
git push origin feature-update
```

---

### Lab Summary Status
* **GitHub:** One repository with a "Locked" main branch.
* **Local:** Two directories with different `user.name` identities.
* **Authentication:** Both use your single SSH key, but GitHub's rules now force you to use a PR to get code into `main`.

