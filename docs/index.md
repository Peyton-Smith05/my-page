# Peyton's tutorial for Mkdocs and GitHub Pages

## Step 1 - Setting up the repository
* Create your repository.
* Add mkdocs.yml and docs directory with the index.md page.
* Commit all changes to main.

## Step 2 - Using GitHub Actions
* Create a new directory titled .github/workflows within the repository.
* Create a .yml file in the workflows directory.
* Insert the following lines into the .yml file.
``` yaml
name: ci 
on:
  push:
    branches:
      - master 
      - main
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - uses: actions/setup-python@v2
        with:
          python-version: 3.x
      - run: pip install mkdocs-material 
      - run: mkdocs gh-deploy --force
```
* The above code creates a GitHub action that executes everytime there is a push to the repository. In this case it is installing all the prerequisites and executing the command ```mkdocs gh-deploy --force``` which deploys the mkdocs again on GitHub Pages.
* Push this directory and file to the main branch and an action is created and will run on push
    * Note: I experienced up to 5-7 minute wait times for the update to occur on the page.

## Step 3 - You're done
* Make changes the mkdocs and commit them to main and {==vualah!==} :thumbsup:

## Issues I came across
* Error message in GitHub Desktop when trying to commit changes:
``` 
error: couldn't set 'refs/remotes/origin/main'
From https://github.com/Peyton-Smith05/my-page
 ! 35ec70b..c5d2301  main       -> origin/main  (unable to update local ref)
 ```
    * Resolution: Running this command ```git gc --prune=now``` on linux command line in workflows directory
        * Source: https://stackoverflow.com/questions/10068640/git-error-on-git-pull-unable-to-update-local-ref

## Sources
* Github actions code:
    * https://squidfunk.github.io/mkdocs-material/publishing-your-site/
    * More on GitHub Actions--> https://docs.github.com/en/actions/quickstart
* Deploying mkdocs on GitHub Pages
    * https://www.mkdocs.org/user-guide/deploying-your-docs/#custom-domains
        * Note: There is a second way mentioned in this site for User Pages
* Mkdocs styling and formatting:
    * https://squidfunk.github.io/mkdocs-material/reference/lists/#using-definition-lists
* Creating a GitHub Page:
    * https://pages.github.com/