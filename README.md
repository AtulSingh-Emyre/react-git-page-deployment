# React Git Pages Deployment
This article mainly covers the steps for deploying an already existing react application using gh-pages.
As for the pre-requisites, we mainly require a working react web app which is ready for deployment. The web app should also be present as a repository on github.

## Step 1: gh-pages
Firstly, we install gh-pages in our web app.
I have used gh-pages version 6.1.1 for my purposes most recently.
```
npm install gh-pages --save-dev
```
With this, we will have gh-pages present in the dev dependencies list in the <b>Package.json</b> file, similar to below:
```
"devDependencies": {
    // other dependencies
    "gh-pages": "^6.1.1"
  }
```
## Step 2: Package.json

- Now that we have gh-pages installed, we define the build operation as well as the url configuration in the <b>Package.json</b> file.
we first add <b>homepage</b> key right below the project name key at the top of the file...
```
{
  "name": "portfolio",
  "homepage": "https://AtulSingh-Emyre.github.io/portfolio-website/#/",
```

The value used for homepage is: `https://{username}.github.io/{repo-name}`. The reason for using the extra `/#/` at end of my homepage value will be explained in step 3.

- Next we add a predeploy and deploy script for building the project:
```
"scripts": {
    // other scripts
    "predeploy": "npm run build",
    "deploy": "gh-pages -d build"
  }
```

## Step 3 (case wise): Router 
Now if you are using react-router-dom, you may have some issues with rendering pages once the website is deployed due to routes.
