# Reproducible Research & Websites with GitHub

RSAA Skillshare — April 2026

Patrick Armstrong & Sven Buder

---

## Why Version Control?

Typical research workflow:

analysis.py  
analysis_final.py  
analysis_final_v2.py  
analysis_final_v2_really_final.py

Problems:

- not reproducible
- not collaborative
- not reviewable
- not transparent
- not reusable

Version control solves all of these.

---

## What Git Actually Does

Git records:

- what changed
- when it changed
- who changed it
- why it changed

Think of Git as:

a time machine  
a lab notebook  
a collaboration layer


---

## Why This Matters in Astronomy

Modern astronomy depends on reproducible pipelines:

- survey reductions
- catalogue generation
- spectral modelling
- simulations
- figures for papers
- data releases

Examples:

- surveys like GALAH, SkyMapper  
- workflows for telescopes like the 2.3m or SKA  
- any type of code that more than one person uses
- any type of simulation  

All rely on version control workflows.

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