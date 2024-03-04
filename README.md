# sass-architecture


# Sass 7-1 Architecture for Code Organization (Setup Guide)

## Summary
Code organization within a software project makes it more manageable, readable, and maintainable. This GitHub repository provides the list of folders and subfiles you need to set up your Sass 7-1 architecture. In the subsequent part of this README, you'll find a guide on how to set up and compile Sass 7-1 architecture in your project.

If you prefer to watch a video demonstration instead, check out [How to setup, and compile Sass 7-1 architecture to CSS in React](https://www.youtube.com/watch?v=a8siiSwEC2w).

## Step by Step Guide

### Step 1:
Install Node.js (if you already have Node installed, you can skip this step).

### Step 2:
Creating your `package.json`. If you already have your React app setup, you do not need to create a `package.json`; you can simply SKIP to Step 4.

### Step 3:
In your terminal, create your first file (`package.json`) using `npm init`.
- You should get a message saying "you're about to install package.json", then press enter till you get back to your directory.

By now, your `package.json` should have already been showing in your explorer. Check to see a template like this:
```json
{
    "name": "my-app", 
    "version": "1.0.0",
    "description": "",
    "main": "index.js",
    "scripts": {
      "test": "echo \"Error: no test specified\" && exit 1"
    },
    "author": "",
    "license": "ISC"
}
```

### Step 4:
Still in your terminal, install the dependencies with the following:
```bash
npm i node-sass concat autoprefixer npm-run-all postcss postcss-cli
```
Once the installation is done, check to see that your `package.json` has been updated to include the dependencies as shown below.

```json
{
    "name": "recent-work", 
    "version": "1.0.0",
    "description": "",
    "main": "index.js",
    "scripts": {
      "test": "echo \"Error: no test specified\" && exit 1",
    },
    "author": "",
    "license": "ISC",
    "dependencies": {
    "autoprefixer": "^10.4.15",
    "concat": "^1.0.3",
    "node-sass": "^9.0.0",
    "npm-run-all": "^4.1.5",
    "postcss": "^8.4.29",
    "postcss-cli": "^10.1.0"
   }
  }
```


### Step 5:
The next step is to create some files/folders:

#### Step 5a:
Create a folder (`SCSS`), then create 1 `main.scss` file and the 7 folders (i.e., abstracts, base, components, layout, pages, themes, vendors). Use `@import` to link all your SCSS files in your 7 folders to your `main.scss` file.

#### Step 5b:
Create a folder (`CSS`) and create 5 CSS files in it named (`main.css`, `additional.css`, `style.comp.css`, `style.concat.css`, `style.prefix.css`).

#### Step 5c:
Link your `main.css` file as the stylesheet link in your `index.html`.

### Step 6:
Back to your `package.json` file, customize the "scripts" by stating the path to find your "SCSS and CSS files" which we just created. The script should look similar to this:


```json
{
    "name": "recent-work", 
    "version": "1.0.0",
    "description": "",
    "main": "index.js",
    "scripts": {
      "test": "echo \"Error: no test specified\" && exit 1",
      "watch-sass": "node-sass scss/main.scss css/main.css --watch",
      "compile-sass": "node-sass scss/main.scss css/style.comp.css",
      "concat-css": "concat -o css/style.concat.css css/additional.css dist/style.comp.css",
      "prefix-css": "postcss --use autoprefixer -b 'last 5 versions' css/style.concat.css -o css/style.prefix.css",
      "compress-css": "node-sass css/style.prefix.css css/style.css --output-style compressed",
      "build-css": "npm-run-all compile-sass concat-css prefix-css compress-css"
    },
    "author": "",
    "license": "ISC",
    "dependencies": {
    "autoprefixer": "^10.4.15",
    "concat": "^1.0.3",
    "node-sass": "^9.0.0",
    "npm-run-all": "^4.1.5",
    "postcss": "^8.4.29",
    "postcss-cli": "^10.1.0"
   }
  }
```

NOTE: The pathing in each line was added according to how the SCSS and CSS Folders/files were named, so always work with what you name your folders/files.


### Intermission:
If you have come this far WITHOUT encountering any errors, well done. 🎉

**SETUP IS COMPLETE...**

### Step 7:
To test if your SCSS and CSS are working correctly/watching for changes, run the below command in your terminal:
```bash
npm run watch-sass
```
You should get a message indicating that the watch is active.

### Step 8:
Now, once you make changes in any of your SCSS files, you would get a success message indicating the compilation.

### Step 9:
When you check your `main.css`, you'd see all the styles you've written in your SCSS, or the ones you `@import`ed to your `main.scss` compiled all-together!

**CONGRATULATIONS!!** 🎉

## Credits
- [John Pels](https://github.com/John-pels)
- [Folawe Rahman](https://github.com/folawerahman)
- [Tunde Sanusi](https://github.com/tuhamworld)
```

