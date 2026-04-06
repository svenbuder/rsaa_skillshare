# RSAA Skillshare 2026-04 Tutorial: Build Your Academic Website with GitHub Pages

Goal:

Create your own academic website while learning:

- repositories
- branches
- pull requests
- review workflows
- GitHub Pages
- GitHub Actions basics

## Step 0: Create Your Repository

Go to: https://github.com/new

Create public repository named: `username.github.io`

Initialize with README

## Step 1: Clone Your Repository

Open terminal:

```bash
git clone https://github.com/username/username.github.io
```

Enter directory:

cd username.github.io


## Step 2: Create Branch Structure

1. Rename default `main` branch to `production`.  
2. Push the `production` branch.
3. Create a `development` branch.
4. Push the `development` branch.

```bash
git branch -m production
git push -u origin production
git checkout -b development
git push -u origin development
```

## Step 3: Set Default Branch

On GitHub go to Settings → Branches
Set default branch: `development`

## Step 4: Download Website Template

Download a html template, for example https://html5up.net/stellar

Copy files into the repository folder on your computer (unzip if necessary)

## Step 5: Commit Template to Development Branch

First, let's make sure we are on the correct branch with
```
git status
```

If we get the message `On branch development`, we can push the template content from our computer to the online repository

```bash
git add .
git commit -m "Add HTML5UP Stellar template"
git push
```

## Step 6: Enable GitHub Pages

We follow the instructions from https://docs.github.com/en/pages/quickstart, that is:

1. Go to Settings → Pages
2. Under Source: → Deploy from branch Select: → `production` → Save

## Step 7: Edit Your Website

Open `index.html`

Edit something. This could be as simple as changing line 23 from `<h1>Stellar</h1>` to `<h1>FirstName LastName</h1>` and exchanging some information in lines 24+25 (within `<p> ... </p>`) with a few words on you, e.g. `Astrophysicist at the Australian National University`.

## Step 8: Commit Changes

```bash
git add index.html
git commit -m "Adjust basic information"
git push
```

## Step 9: Create Your First Pull Request

On the GitHub repository website: Compare & pull request

Select: development → production

Title:

Initial website version

Create pull request

<!-- 
## Step 10: Review a Partner’s Website

Pair with someone nearby.

Review:

clarity

links

layout

typos

Leave one suggestion comment.


## Step 11: Merge Pull Request

Click:

Merge Pull Request

Now your site is live:

https://username.github.io


## Step 12: Confirm Deployment

Wait 30–60 seconds

Reload page

Your website should appear online.


## Step 13: Add a Publications Section

Open:

index.html

Add section:

Publications

Example:

ADS link

Google Scholar link

ORCID link


## Step 14: Commit via Development Branch Again

git add .

git commit -m "Add publications section"

git push


## Step 15: Open Second Pull Request

development → production

Merge after review


## Step 16: Optional: Enable GitHub Actions

Create directory:

mkdir -p .github/workflows

Create file:

deploy.yml


Paste:

name: Deploy Website

on:
  push:
    branches:
      - production

jobs:
  deploy:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v4


Commit:

git add .

git commit -m "Add deployment workflow"

git push


## Step 17: Suggested Website Structure

Recommended sections:

About

Research

Publications

Software

Teaching

Contact


## Step 18: Optional Improvements

Add:

CV PDF

project pages

figures

press coverage

talk slides


## Step 19: What You Learned Today

You used:

repositories

branches

pull requests

review workflow

GitHub Pages

automation


## Step 20: Why This Matters

This workflow matches:

modern astronomy pipelines

survey collaborations

software engineering

data science teams

machine learning projects

You now have a reproducible research website. -->

## Link your MSO presence to your github website

Use the ANU VPN (or MSO ethernet) and `ssh` onto any of the MSO machines. Then create the `public_html` directory in the home directory via

```bash
mkdir public_html
cd public_html
```

and then create an `index.html` file with the following content (adjust your GitHub `$USERNAME`):

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">

  <!-- Immediate redirect -->
  <meta http-equiv="refresh" content="0; url=https://$USERNAME.github.io">

  <!-- Tell search engines which page is the real homepage -->
  <link rel="canonical" href="https://$USERNAME.github.io">

  <title>Redirecting to personal homepage</title>

  <style>
    body {
      font-family: sans-serif;
      text-align: center;
      margin-top: 10%;
    }
  </style>
</head>

<!-- Display a message in case the automatic redirect does not work -->
<body>

<h1>Welcome!</h1>

<p>
My academic homepage has hosted at
<a href="https://$USERNAME.github.io">$USERNAME.github.io</a>.
</p>

<p>Redirecting automatically…</p>

</body>
</html>
```