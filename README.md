# P05 - Git Merge Conflict Demo

This repository demonstrates how merge conflicts occur in Git and how to resolve them manually.

---

## What is a Merge Conflict?

A **merge conflict** happens when two branches make changes to the same lines of a file, and Git doesn’t know which one to choose during a merge.

---

## Scenario Simulated

1. **main** branch has a file `conflict-demo.txt` with initial content.
2. A new branch `feature-a` is created and modifies the same lines in `conflict-demo.txt`.
3. The `main` branch is updated differently on the same lines.
4. When `feature-a` is merged back to `main`, a **conflict occurs**.
5. The conflict is resolved manually by editing the file.

---

## Steps to Simulate

```bash
# Step 1: Create repo and add initial file
echo "This is line 1" > conflict-demo.txt
git add conflict-demo.txt
git commit -m "Initial commit with conflict-demo.txt"

# Step 2: Create and switch to new branch
git checkout -b feature-a

# Step 3: Edit the file in feature-a
echo "This is modified by feature-a" > conflict-demo.txt
git commit -am "Feature A modifies the file"

# Step 4: Switch back to main and make a conflicting edit
git checkout main
echo "This is modified in main branch" > conflict-demo.txt
git commit -am "Main modifies the file"

# Step 5: Try to merge feature-a into main
git merge feature-a
At this point, Git will raise a merge conflict!

# Step 6: How to Resolve It
Open the conflicted file:
You’ll see Git markers like:

<<<<<<< HEAD
This is modified in main branch
=======
This is modified by feature-a
>>>>>>> feature-a

Manually edit to keep the desired version.
Mark conflict as resolved:
git add conflict-demo.txt
git commit -m "Resolved merge conflict"
