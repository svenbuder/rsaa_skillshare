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

On the GitHub repository website, you will find a yellow/green note button → `Compare & pull request`

Fill out the pull request details:

base: `production` <- compare: `development`  
Title (this may populate automatically): `HTML5-Up template with adjusted basic information`  
Description (this may populate automatically): any additional important information. (For this request, I would not add anything)
→ `Create pull request`

GitHub is now checking if it can automatically merge your `development` content into the `production` branch

## Step 10: Review

This is the place, where in professional coding, another person would look over your code changes (and potential tests to make sure everything is and will keep running as it should).

Things to look into:
`Commits`: what is the person writing about the changes?
`Checks`: Does the new code pass all the background checks to ensure it is and will keep running?
`Files changed`: GitHub will highlight the code changes between `production` and `development`.

Have a look at your code changes. Is what changed exactly what you wanted to do?
If not: you can request changes or perform them yourself (with new commits into the `development` branch).

## Step 11: Merge Pull Request

Once you are happy with the requested changes, click → `Merge Pull Request`

Now latest changes will now be propagated to the website that is live (aka whatever was deployed from your `production` branch before): https://$USERNAME.github.io

## Step 12: Confirm Deployment

GitHub is now starting to *deploy* your website, that is, translate the html code into what people can see at your website. To do that, it is following a *workflow*.

If you want to see how this process looks like, you can go to your repository's `Actions` tab and look at the latest *workflow run*. Within a few seconds, it should run through a `build` → `report-build-status` → `deploy` chain.

Once the deployment is complete (green tick in front of `deploy`), you can go

https://$USERNAME.github.io

The latest changes to your website should appear now - you may need to reload the site to see them.

## Step 13: Add a picture and important links

Find a picture of yourself for the website and add it to the `images/` directory.

Now open `index.html` and change the image source for the image of the first section (`<img src="images/pic01.jpg" alt="" />`) from `pic01.jpg` to your image.

For researchers, we usually use a few important links to showcase ourselves and our work:
- our email address
- a unique [ADS link](https://ui.adsabs.harvard.edu/) (this is very important if you share a very common name) that will list not only your papers, but also track citations etc.  
- [ORCID link](https://orcid.org/) to keep track of your papers

One html-example:

GitHub: <a href="https://github.com/$USERNAME$" target="_blank" rel="noopener noreferrer" class="icon brands fa-github" title="GitHub"><span class="label">GitHub</span></a>

This would create a link with a GitHub logo in front of it and open a new tab (because `target="_blank"`) when clicked.

## Step 14: Commit via Development Branch Again

```bash
git add .
git commit -m "Add picture and links"
git push
```

## Step 15: Open Second Pull Request

development → production

Merge after review

## Step 16: Keep Adjusting Your Website

Recommended sections:
- About (with a CV file to download)  
- Research  
- Publications  
- (Teaching)  
- (Supervision)  
- (Software)
- (Press Coverage)
- Contact  

Keep it short and interesting (pictures always help)!
And find your own style!

## Step 17: What You Learned Today

You used:
- repositories  
- branches  
- pull requests  
- review workflow  
- GitHub Pages  
- automation

## Step 18: Why This Matters

This workflow matches:  
- modern astronomy pipelines  
- survey collaborations  
- software engineering  
- data science teams  
- machine learning projects

You now have a reproducible research website.

## Step 19L Link your MSO presence to your github website

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