# GitHub Pages Demo

## :bulb: [What is GitHub Pages?](https://docs.github.com/en/github/working-with-github-pages/about-github-pages)

> GitHub Pages is a static site hosting service that takes HTML, CSS, and JavaScript files straight from a repository on GitHub, optionally runs the files through a build process, and publishes a website. 
> You can see examples of GitHub Pages sites in the [GitHub Pages examples collection](https://github.com/collections/github-pages-examples).

> There are three types of GitHub Pages sites: project, user, and organization. 
> Project sites are connected to a specific project hosted on GitHub, such as a JavaScript library or a recipe collection. User and organization sites are connected to a specific GitHub account.

In this demo, we will create a GitHub Pages site connected to a repository.

## :bulb: Prerequisite

- Git supported local environment
- Unix system - We will be using `wget` to retrieve a demo R Markdown file. You can download the file with other means if using other OS.
- R environment
- R [rmarkdown](https://cran.r-project.org/package=rmarkdown) package - we will use the `render` function to generate a HTML document from a R Markdown file.

-----

## :computer: Create a new repository on GitHub

First, we will create a **public** repository to enable Pages. You will be able have Pages in private repositories if you are a *GitHub Pro* user. You can initialize the repository with a README file and/or license if you wish, or add them later.

![Create repository](https://user-images.githubusercontent.com/9032946/93335108-dfc21500-f81d-11ea-886b-c72d6c26f474.png)

## :computer: Set up Pages

Under the **:gear:Settings** tab of the repository page, scroll down to the **GitHub Pages** section. Click on the **Choose a theme** button under **Theme Chooser**.

![GitHub Pages](https://user-images.githubusercontent.com/9032946/93335259-1009b380-f81e-11ea-88cf-d8454bbbb005.png)

We can initialise the **Pages** feature by selecting a theme. Click on the **Select theme** button after selection. Here we will use the default **Cayman** theme.

![Select theme](https://user-images.githubusercontent.com/9032946/93335330-2e6faf00-f81e-11ea-9edb-36d158d0cec1.png)

You will be redirected to the `index.md` file creating page. Click **Cancel** to accept the default content.

![Create index.md](https://user-images.githubusercontent.com/9032946/93336776-20229280-f820-11ea-877b-c3ac0b34e3f4.png)

Now we have a special new branch called **gh-pages**. This branch name is reserved for GitHub look for website content in the repository.

![gh-pages branch](https://user-images.githubusercontent.com/9032946/93337031-78599480-f820-11ea-9cc4-354e657e15da.png)

## :computer: URL of the site

After the **gh-pages** branch is created, go to the **GitHub Pages** section in **:gear:Settings**. It will now show you the URL of your site.

![url](https://user-images.githubusercontent.com/9032946/93337434-09c90680-f821-11ea-8eaf-b882a6b13111.png)

With the **gh-pages** branch created, we can now use this special branch to host web content. 

By default, GitHub will render the `index.md` file and show it as a web page. We can replace it with a `index.html`, or edit `index.md` to show the content we want.

![Default site](https://user-images.githubusercontent.com/9032946/93337866-9b387880-f821-11ea-9516-a9250a00daef.png)

-----

## :computer: Cloning a repository

In most cases, you will be working on a project or software on a local machine, and only push commits to the remote repository when you are ready to share it online. So, we will **clone** the repository from GitHub to the local machine. By doing so, we will obtain a full copy of the data and the commit histories of every file and folder that the GitHub repository has at that point in time. We can obtain the remote URL provided on the GitHub repository page by clicking on the **Code** button.

In this tutorial we will use the follow local directory structure:

### When in the master branch

```
/mnt
├── project
│   └── mtcars
│       ├── index.html (your web page)
│       └── mtcars.Rmd (your source code)
└── github
    └── R-Test-Repo
        ├── .git
        ├── LICENSE
        ├── mtcars.Rmd
        └── README.md     
```

### When in the gh-pages branch

```
/mnt
├── project
│   └── mtcars
│       ├── index.html    
│       └── mtcars.Rmd
└── github
    └── R-Test-Repo
        ├── _config.yml
        ├── .git
        ├── index.html
        └── index.md
```
On your local machine, initiate the cloning process with `git clone`.

```S
$ cd /mnt/github
$ git clone https://github.com/USERNAME/R-Test-Repo.git

Cloning into 'R-Test-Repo'...
remote: Enumerating objects: 7, done.
remote: Counting objects: 100% (7/7), done.
remote: Compressing objects: 100% (4/4), done.
remote: Total 7 (delta 0), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (7/7), done.
```

By default, `git clone` will download the contents in the **master** branch. You can check which branch you are currently in with `git branch`.

```S
$ cd /mnt/github/R-Test-Repo
$ git branch

* master
```

## :computer: Checkout a remote branch

We can download the remote **gh-pages** branch and add it to our local repository with `git checkout`. 

> **Note:** The same `git checkout` command can be use to retrieve any remote branch that exist in the remote repository.

```S
$ git checkout -b gh-pages origin/gh-pages

Branch 'gh-pages' set up to track remote branch 'gh-pages' from 'origin'.
Switched to a new branch 'gh-pages'
```

```S
$ git branch

* gh-pages
  master
```

-----

## :computer: Download `mtcars.Rmd`

We can now start to use `git` as a version-control system to track and monitor changes. For example, we have a project named `mtcars` that we are working on and we would like to track the changes, and share the file and the rendered HTML document on GitHub.

You can create your files inside the `R-Test-Repo` directory on your local machine that is tracked by `git`. For the simplicity of this demonstration, we will download the "mtcars.Rmd" file from [here](https://raw.githubusercontent.com/ycl6/GitHub-Pages-Demo/master/mtcars.Rmd).

```S
$ cd /mnt/project/mtcars
$ wget https://raw.githubusercontent.com/ycl6/GitHub-Pages-Demo/master/mtcars.Rmd
```

## :computer: Convert Rmd to HTML

Next, we use the `render` function in the `rmarkdown` package to generate the HTML document of the R Markdown file that we have just downloaded.

We create the HTML document with the name `index.html` because a file with this name will be used as the default page shown on a website, i.e. the homepage of the website.

```S
$ R -e "rmarkdown::render('mtcars.Rmd', output_file = 'index.html')"

R version 3.6.3 (2020-02-29) -- "Holding the Windsock"
Copyright (C) 2020 The R Foundation for Statistical Computing
Platform: x86_64-conda_cos6-linux-gnu (64-bit)
...
...
...
Output created: index.html
```

## :computer: Add source code to master branch

Go to the local repository, and check which branch you are in now.

```S
$ cd /mnt/github/R-Test-Repo
$ git branch

  gh-pages
* master
```

If you are in another branch, e.g. the **gh-pages** branch, you can switch to the **master** branch with `git checkout`.

```S
$ git checkout master
$ git branch

  gh-pages
* master
```

Copy the `mtcars.Rmd` to current directory, use `git` commands to push it to GitHub.

```S
$ cp /mnt/project/mtcars/mtcars.Rmd .

$ git add .
$ git commit -m "Initial commit"
$ git push origin master 
```

## :computer: Add HTML to gh-pages branch

Use `git checkout` to switch to the **gh-pages** branch and copy the `index.html` to current directory.

```S
$ git checkout gh-pages
$ git branch

* gh-pages
  master
```

```S
$ cp /mnt/project/mtcars/index.html .

$ git add .
$ git commit -m "Initial commit"
$ git push origin gh-pages 
```

## :computer: View site on browser

Use the URL provided in **:gear:Settings** that you saw earlier and go to your site on your browser.

If the site content was not updated, you can do a *force refresh* by pressing both control and F5 to get the latest version of the site.

![New site](https://user-images.githubusercontent.com/9032946/93347546-1e130080-f82d-11ea-9724-4be46d58bb59.png)

-----

## :bulb: Choosing publishing sources

There are 3 publishing sources you can choose for a GitHub repository:

1. in the **master** branch
2. in the `docs` folder of the **master** branch (make sure the `docs` folder already exists in your repository)
3. in the **gh-pages** branch

In this demo, we are using the **gh-pages** branch to publish the website. You can use other sources if you find them more appropriate. For example, I am publishing the web version of this `GitHub-Pages-Demo` repository using the **master** branch, and GitHub renders this `README.md` file and show it as a [web page](https://ycl6.github.io/GitHub-Pages-Demo/).

## :bulb: Extended Reading

- [Using Git](https://docs.github.com/en/github/using-git): Learn common and advanced workflows in Git to enhance your experience using GitHub.
- [Creating, cloning, and archiving repositories](https://docs.github.com/en/github/creating-cloning-and-archiving-repositories): Learn about creating, cloning and archiving a GitHub repository.
- [Writing on GitHub](https://docs.github.com/en/github/writing-on-github): Learn about writing and formatting syntax.
- [Committing changes to your project](https://docs.github.com/en/github/committing-changes-to-your-project): Learn about commits.
- [Working with GitHub Pages](https://docs.github.com/en/github/working-with-github-pages)
- [Git Cheat Sheet](https://training.github.com/downloads/github-git-cheat-sheet/) [[PDF](https://training.github.com/downloads/github-git-cheat-sheet.pdf)]
