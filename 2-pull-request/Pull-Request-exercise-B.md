## Pull-Request Lab Part 2: The Pull Request Lifecycle

### Phase 1: Proposing the Change (The "Junior Developer")
In Part 1, you pushed a branch called `feature-update` from your `contributor-dir`. Now, you need to formally ask the Maintainer to accept it.

1.  **Go to GitHub.com:** Navigate to your `git-identity-lab` repository.
2.  **Open the PR:** You should see a yellow banner: *"feature-update had recent pushes..."*
    * Click **Compare & pull request**.
3.  **Describe the Work:** * **Title:** "Update README with new feature details"
    * **Description:** "This change adds the core feature documentation as requested."
4.  **Create:** Click the green **Create pull request** button.


### Phase 2: The Code Review (The "Boss Maintainer")
Now, imagine you have switched hats. You are the "Boss" responsible for code quality.

1.  **View Changes:** On the PR page, click the **Files changed** tab.
2.  **Line Comment:** Hover over the new line of text in the README. Click the blue **+** icon.
    * **Comment:** "Could you make this description a bit more specific?"
    * Click **Start a review**.
3.  **Finish Review:** Click **Finish review** at the top right.
    * Select **Request changes**.
    * Click **Submit review**.

> **Note:** The PR status will now turn red/yellow, indicating that "Changes were requested."


### Phase 3: The Iteration (The "Junior Developer")
Back in your terminal, the Junior Developer needs to fix the work based on the feedback.

```bash
cd ~/github-lab/contributor-dir

# 1. Make the fix
echo "Specific details about the feature: Version 1.0 is live." >> README.md

# 2. Commit and Push the fix
git add README.md
git commit -m "Addressing review feedback"
git push origin feature-update
```

**Observation:** You don't need to open a *new* PR. GitHub automatically updates the existing PR with your new commit!

### Phase 4: Approval & The Merge (The "Boss Maintainer")
Now that the changes look good, it’s time to bring them into `main`.

1.  **Approve:** On GitHub, go back to the PR. You’ll see the new commit.
2.  **Review again:** Click **Files changed** → **Review changes** → **Approve** → **Submit review**.
3.  **The Merge:** Since the branch protection rules are satisfied (you have a PR and an approval), the **Merge pull request** button is now green.
    * Click **Merge pull request**.
    * Click **Confirm merge**.
4.  **Delete Branch:** Click the **Delete branch** button that appears. (Cleanliness is key in Git!)


### Phase 5: Syncing the Local Environments
Your GitHub `main` is now ahead of your local folders. You need to sync them up.

```bash
# Sync the Maintainer folder
cd ~/github-lab/maintainer-dir
git checkout main
git pull origin main

# Sync the Contributor folder
cd ../contributor-dir
git checkout main
git pull origin main
```

### Lab Summary Status
- **GitHub:** The `main` branch now contains the Junior Developer's code.
- **History:** If you run `git log` in either directory, you will see a "Merge Commit" and the specific names ("Junior Developer") attached to the work.
- **Cleanliness:** Both local folders are now perfectly in sync with the remote `main`.

