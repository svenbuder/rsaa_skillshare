# Reproducible Research & Websites with Git

RSAA Skillshare — April 2026

Patrick Armstrong & Sven Buder

---

## Why I think Git is hard to learn

- What to do:
  - `git add -A`, `git commit -m "commit"`, `git push`

- Why to do this:
  - ???

- What to do when it breaks:
  - !!!

---

## **Core Concept:** Version Control Systems (VCS)

A VCS *must* provide:

1. A way to record the current `state` of a `project` (a set of files, such as source code, papers, research notes, daily journals, etc...) into a fixed `version` of that project.
2. A way to traverse through all recorded versions of a project, allowing you to `revert` to old versions, and `advance` to new ones.

---

## **Core Concept:** Version Control Systems (VCS)

A **good** VCS should provide:

- Transparency: How easy is it to see what changed between versions? How easy is it to tell why those changes were made?
- Specificity: Can you record and traverse changes in individual files or only the project as a whole?
- Collaboration: How easy is it to share a new version with others? Can multiple people work on the project independently? 
- Simplicity: How easy is it to use? How easy is it to break? When things do break, how easy is it to fix?

---

## You don't need Git for Version Control, but it helps!

- `analysis.py`
- `analysis_2.py`
- `analysis_final.py`
- `analysis_final_update.py`

[$\sim$] Transparency: `diff analysis.py analysis_2.py`, but unclear why.

[$\sim$] Specificity: `analysis_2.py`, `plotting_fix.py` but easy to mismatch.

[$\times$] Collaboration: `analysis.py` + `analysis_fix.py` = ???

[$\sim$] Simplicity: Low barrier to entry, but easy to break and hard to fix. Can irreversibly overwrite previous versions!!!

---

## VCS with Git: Initialisation

Install Git, then

```
mkdir git_project
cd git_project
git init
echo 'print("Hello World!")' > analysis.py
```

---

## VCS with Git: Explore the state of the project.

```
ls -al
git status
```

`.git/`: Where Git stores the files it needs to function.

You get a "Version 0" for free which is when your project consisted of nothing.

---

## VCS with Git: Explore the state of the project.

```
On branch main # <- Which version history are we traversing?

No commits yet # <- Have we created any versions?

Untracked files: # <- What changes exist but aren't yet tracked?
  (use "git add <file>..." to include in what will be committed)
        analysis.py

# Summary of state and suggested actions.
nothing added to commit but untracked files present
    (use "git add" to track)
```

---

## VCS with Git: Record the state into a new version.

1. `git add analysis.py`: Tell Git what we want to include in the new version.
    - `git status`
2. `git commit -m "Created analysis.py with dummy code."`: Create a new version.
    - `git status`

---

## VCS with Git: Record the state into a new version.

- `git add analysis.py`
- `git status`

```
On branch main

No commits yet

Changes to be committed: # <- What changes to the state are we tracking?
  (use "git rm --cached <file>..." to unstage)
        new file:   analysis.py
```

---

## VCS with Git: Record the state into a new version.

- `git commit -m "Created analysis.py with dummy code."`
```
#                   vvvvvvv Version ID
[main (root-commit) b95884e] Created analysis.py with dummy code.
#        Version Description ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
# What changed:
 1 file changed, 1 insertion(+)
 create mode 100644 analysis.py
```

- `git status`
```
On branch main
nothing to commit, working tree clean
```

---

## VCS with Git: Make a change, and create a new version.

```
echo 'print("So long, and thanks for all the fish.")' >> analysis.py
git add analysis.py
git commit -m "Added a goodbye message to analysis.py"
```

---

## VCS with Git: Make a change, and create a new version.

- `echo 'print("So long, and thanks for all the fish.")' >> analysis.py`
- `git status`

```
On branch main
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   analysis.py

no changes added to commit (use "git add" and/or "git commit -a")
```

---

## VCS with Git: Make a change, and create a new version.

- `git add analysis.py`
- `git status`

```
On branch main
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   analysis.py
```

---

## VCS with Git: Make a change, and create a new version.

- `git commit -m "Added a goodbye message to analysis.py"`

```
[main 30bb59f] Added a goodbye message to analysis.py
 1 file changed, 1 insertion(+)
```

- `git status`

```
On branch main
nothing to commit, working tree clean
```

---

## VCS with Git: Traverse version history

```
git checkout HEAD~1 # To go to the previous version
# or
git checkout b95884e # To go to a specific version
git checkout main # To go to the latest version
```

---

## VCS with Git: Traverse version history

- `git checkout b95884e` (or `HEAD~1`)

```
Note: switching to 'b95884ec9c91525bc47e64580cfc4cacd6600dd4'.
You are in 'detached HEAD' state.
...
HEAD is now at b95884e Created analysis.py with dummy code.
```

- `cat analysis.py`

```
print("Hello World!")
```

---

## VCS with Git: Traverse version history

- `git checkout main`

```
Previous HEAD position was b95884e Created analysis.py with dummy code.
Switched to branch 'main'
```

- `cat analysis.py`

```
print("Hello World!")
print("So long, and thanks for all the fish.")
```

---

## **Core Concept:** Git terminology and the basic Git workflow

**Terminology**

- A `commit` is a recorded version of your project
- `staging` a file means adding any changes made to that file to the list of things to record in the next version
- `committing` creates a new version of your project by recording all staged changes
- `checkout` is the act of reverting to an old version or advancing to a new one

**Workflow**

1. `git add <file>` to include changes to that file in the next version
2. `git commit -m "<message>"` to record all staged changes into a new version
3. Traverse version history via `git checkout <commit id>` or `git checkout HEAD~<n>`

---

## VCS with Git: Transparency

- `git log`

```
commit 30bb59fad3b9a9afe20c01bd08253894e05369e2 (HEAD -> main)
Author: Patrick Armstrong <patrick.james.1998@gmail.com>
Date:   Sat Apr 11 19:33:54 2026 +1000
    Added a goodbye message to analysis.py
commit b95884ec9c91525bc47e64580cfc4cacd6600dd4
Author: Patrick Armstrong <patrick.james.1998@gmail.com>
Date:   Sat Apr 11 19:18:01 2026 +1000
    Created analysis.py with dummy code.
```

---

## VCS with Git: Transparency

`git diff HEAD~1 main`

```
diff --git a/analysis.py b/analysis.py
index f301245..eb3da09 100644
--- a/analysis.py
+++ b/analysis.py
@@ -1 +1,2 @@
 print("Hello World!")
+print("So long, and thanks for all the fish.")
```

---

## VCS with Git: Specificity

```
cp analysis.py another_analysis.py
echo 'print("This is a test message")' >> another_analysis.py
git add another_analysis.py
git commit -m "Created another_analysis.py and added a test message"
git checkout b95884e analysis.py # or HEAD~2
git checkout main analysis.py
```

---

## VCS with Git: Specificity

- `git checkout b95884e analysis.py`

```
Updated 1 path from 2773e93
```

- `git status`

```
On branch main
Changes to be committed: # As if you've already run `git add analysis.py`
  (use "git restore --staged <file>..." to unstage)
        modified:   analysis.py
```

- `git checkout main analysis.py`

```
Updated 1 path from 2aaf275
```

---

## VCS with Git: Collaboration

Two powerful tools for collaboration:

1. Branches: For collaborating with others on the same system (including "collaboration" with yourself!)
    - Broadly similar to copy-pasting your entire project into a new folder.
2. Repositories: For collaborating with others on multiple systems.
    - Broadly similar to copy-pasting your entire project into a cloud storage server (Google Drive, OneDrive, etc...)

---

## **Core Concept:** Branches

A `branch` is a copy of your project with its own, independent version history. `main` is a branch created by Git automatically, and is usually where you store code that is ready for others to use (production code).

---

## VCS with Git: Using Branches

```
main
1: Create project
2: Create analysis.py
|\
| dev
| 2.1: Create another_analysis.py
3: Add farewell to analysis.py
| 2.2: Have analysis.py call another_analysis.py
|/
4: Merge dev branch into main
```

---

## VCS with Git: Using Branches

1. Before branching
```
mkdir git_project
cd git_project/
git init
echo 'print("Hello World!")' > analysis.py
git add analysis.py
git commit -m "Created analysis.py with dummy code."
```

---

## VCS with Git: Using Branches

2. Create and modify `dev` branch
```
git checkout -b dev
echo 'print("This is a test message.")' > another_analysis.py
touch __init__.py
echo 'import another_analysis' >> analysis.py
git add another_analysis.py
git commit -m "Created another_analysis.py with dummy code."
git add __init__.py analysis.py
git commit -m "Have analysis.py call another_analysis.py"
```

---

## VCS with Git: Using Branches

3. Modify `main`
```
git checkout main
echo 'print("So long, and thanks for all the fish.")' >> analysis.py
git add analysis.py
git commit -m "Added a goodbye message to analysis.py"
```

---

## VCS with Git: Using Branches

4. Merging

- If `main` had **no** changes, we'd be able to run `git merge dev` and `main` would `fast-forward` the `dev` changes, basically acting as if we had made those changes in `main` to begin with.
    - Side note, this just adds all of `dev`s version history directly onto `main`'s. If instead you want all of `dev`'s version history to be compressed into a single commit, you can `git merge --squash dev`.
- Because `main` does have changes we instead need to run `git merge --no-ff dev`. Now Git will try its best to automatically merge the two branches together. It's able to do this for `__init__.py` and `another_analysis.py` since there's no conflict, but `analysis.py` has an issue that we'll need to manually fix.

---

## VCS with Git: Fixing merge conflicts

- `git merge --no-ff dev`

```
Auto-merging analysis.py
CONFLICT (content): Merge conflict in analysis.py
Automatic merge failed; fix conflicts and then commit the result.
```

---

## VCS with Git: Fixing merge conflicts

- `git status`

```
On branch main
You have unmerged paths.
  (fix conflicts and run "git commit")
  (use "git merge --abort" to abort the merge)

Changes to be committed:
        new file:   __init__.py
        new file:   another_analysis.py
```

---

## VCS with Git: Fixing merge conflicts

Git needs to know which version of this file you want to keep:

- `cat analysis.py`

```
print("Hello World!")
<<<<<<< HEAD # How the file looks according to HEAD
print("So long, and thanks for all the fish.") # End of HEAD's version
||||||| 760788b # How the file looked when dev and main split
======= # End of split's version and start of dev's version
import another_analysis
>>>>>>> dev # End of dev's version
```

---

## VCS with Git: Fixing merge conflicts

To resolve the merge conflict, we edit the file to produce our desired merge. This could mean pick one version or another, keeping multiple versions, or adding new code altogether!

- `cat analysis.py`

```
print("Hello World!")
import another_analysis

print("This didn't exist before the merge")
print("So long, and thanks for all the fish.")
```

---

## VCS with Git: Fixing merge conflicts

Once you've fixed up all merge conflicts, `git add` any files that needed to be manually fixed:

- `git add analysis.py; git status; git commit`

```
On branch main
All conflicts fixed but you are still merging.
  (use "git commit" to conclude merge)

Changes to be committed:
        new file:   __init__.py
        modified:   analysis.py
        new file:   another_analysis.py
```

---

## **Core Concept:** Branches and Merges

- `git checkout -b <branch name>` to create a new branch
- `git checkout <branch name>` to move between existing branches
- `git checkout <to_branch>; git merge <from_branch>` to merge changes from `<from_branch>` into `<to_branch>`
- `git merge --no-ff <from_branch>` if `<to_branch>` has commits that `<from_branch>` doesn't.
    - Alternatively, `git checkout <from_branch>; git merge <to_branch>` regularly to avoid branches diverging too much over time.
- Fix merge conflicts by editing the files to your desired state, then add and commit to finish merging.

---

## Local vs Remote Repositories

Local repository: your laptop
Remote repository: GitHub
Workflow: edit → commit → push


---

## The Basic Git Cycle

Core commands:

git add  
git commit  
git push

Meaning:

stage changes  
record snapshot  
push update online


---

## Branches: Safe Experimentation

Instead of editing directly on main:

create branches:

main  
new-continuum-model  
selection-function-test  
velocity-bugfix

Branches allow experimentation without breaking working code.


---

## Production vs Development Workflow

Today we will use:

production  
development

Only stable code goes to production.

Workflow:

development → pull request → review → production


---

## Pull Requests = Scientific Discussion

Pull requests allow:

structured review  
comments  
suggestions  
documentation improvements  

This is similar to referee reports — but for code.


---

## Why Code Review Improves Research

Review prevents:

hidden assumptions  
silent bugs  
untracked figure changes  

Encourages:

clarity  
documentation  
reproducibility


---

## GitHub Pages

GitHub can host websites directly from repositories.

Examples:

personal academic page  
project documentation  
software manuals  
teaching material  

Free and automatic deployment.


---

## Example: Your Own Research Website

Repository name:

username.github.io

Example:

svenbuder.github.io

GitHub automatically publishes:

https://username.github.io


---

## GitHub Actions

GitHub Actions automate workflows.

Examples:

build websites  
compile LaTeX  
run tests  
generate figures  
deploy documentation

Think:

robot collaborator


---

## Example Action Workflow

Push to repository:

→ Action runs automatically  
→ website updates automatically  

No manual upload required.


---

## Why This Matters for Careers

Research workflow:

code → figure → paper

Modern workflow:

branch → review → test → release

Industry workflow:

exactly the same


---

## Today’s Hands-On Session

You will:

create a GitHub Pages site

create production branch

create development branch

edit website in development

open pull request

merge into production

deploy automatically


---

## Outcome

After this session you will have:

a personal academic website

experience with branching workflows

experience with pull requests

experience with review

experience with automation

These are core research AND industry skills.
