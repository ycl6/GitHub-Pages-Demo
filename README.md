# GitHub Pages Demo

## [What is GitHub Pages?](https://docs.github.com/en/github/working-with-github-pages/about-github-pages)

> GitHub Pages is a static site hosting service that takes HTML, CSS, and JavaScript files straight from a repository on GitHub, optionally runs the files through a build process, and publishes a website. 
> You can see examples of GitHub Pages sites in the [GitHub Pages examples collection](https://github.com/collections/github-pages-examples).

> There are three types of GitHub Pages sites: project, user, and organization. 
> Project sites are connected to a specific project hosted on GitHub, such as a JavaScript library or a recipe collection. User and organization sites are connected to a specific GitHub account.

In this demo, we will create a GitHub Pages site connected to a repository.

## Create a new repository on GitHub

First, we will create a **public** repository to enable Pages. You will be able have Pages in private repos if you are a *GitHub Pro* user. You can initialize the repository with a README file and/or license if you wish, or add them later.

![Create repository](https://user-images.githubusercontent.com/9032946/93335108-dfc21500-f81d-11ea-886b-c72d6c26f474.png)

## Set up Pages

Under the **:gear:Settings** tab of the repository page, scroll down to the **GitHub Pages** section. Click on the **Choose a theme** button under **Theme Chooser**.

![GitHub Pages](https://user-images.githubusercontent.com/9032946/93335259-1009b380-f81e-11ea-88cf-d8454bbbb005.png)

We can initialise the **Pages** feature by selecting a theme. Click on the **Select theme** button after selection. Here we will use the default **Cayman** theme.

![Select theme](https://user-images.githubusercontent.com/9032946/93335330-2e6faf00-f81e-11ea-9edb-36d158d0cec1.png)

You will be redirected to the `index.md` file creating page. Click **Cancel** to accept the deault content.

![Create index.md](https://user-images.githubusercontent.com/9032946/93336776-20229280-f820-11ea-877b-c3ac0b34e3f4.png)

Now we have a special new branch called **gh-pages**. This branch name is reserved for GitHub look for website content in the repository.

![gh-pages branch](https://user-images.githubusercontent.com/9032946/93337031-78599480-f820-11ea-9cc4-354e657e15da.png)

## URL of the site

After the **gh-pages** branch is created, go to the **GitHub Pages** section in **:gear:Settings**. It will now show you the URL of your site.

![url](https://user-images.githubusercontent.com/9032946/93337434-09c90680-f821-11ea-8eaf-b882a6b13111.png)

From now on, you will be able to use the **gh-pages** branch to host web content. 

By default, GitHub will render the `index.md` file and show it as a web page. We can replace it with a `index.html`, or edit `index.md` to show the content we want.

![Default site](https://user-images.githubusercontent.com/9032946/93337866-9b387880-f821-11ea-9516-a9250a00daef.png)
