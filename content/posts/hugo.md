+++
title = 'Introduction To Hugo'
date = 2025-12-02T00:26:26+05:00
draft = false
tags = ["hugo","static-site","github-pages","deployment"]
+++

Hugo is a static site generator based on Go. It is known for its blazing speed and flexibility, allowing it to render sites within a second or less. It has an advanced templating system that makes it incredibly powerful for building modern websites. Hugo comes with its own server having hot reload functionality, so you can see the site changes instantly in your browser.

## Installing Hugo

First, if you already have an older version of Hugo installed, you need to remove it to avoid version conflicts:

```bash
sudo apt remove hugo
```

Next, install the latest version of Hugo from the official releases. Head over to [https://github.com/gohugoio/hugo/releases](https://github.com/gohugoio/hugo/releases) and download the extended version for your system.

Once downloaded, you may install Hugo using the command:

```bash
sudo dpkg -i hugo_extended_*_linux-amd64.deb
```

You may verify the installation using:

```bash
hugo version
```

## Creating a New Hugo Site

Next, you have to create a new Hugo site. For that, you have to use the command:

```bash
hugo new site mysite
```

Replace `mysite` with whatever name you want for your site. This will create a new directory with all the necessary Hugo structure.

## Adding a Theme

Once the site is created, you need to add a theme. For that, navigate to your site directory:

```bash
cd mysite
```

Then you have to initialize Git using:

```bash
git init
```

After that, add your theme as a Git submodule. For example, to add the PaperMod theme:

```bash
git submodule add https://github.com/adityatelange/hugo-PaperMod.git themes/PaperMod
```

You can edit the basic site info like title and subtitle using the `hugo.toml` file. Once you've added the theme, you may need to specify the installed theme in the `hugo.toml` file. For example:

```toml
baseURL = "https://technameer.github.io"
title = "My Hugo Site"
theme = "PaperMod"
```

## Creating Your First Post

Then you have to add a posts page by creating the posts folder in the content directory. You can add a new post using:

```bash
hugo new posts/first-post.md
```

This will add a new post file and you will have your first post created. Now you have to add the markdown content of the post. 

**Important:** You always have to make the `draft` parameter `false` to make it appear on the blog. 

## Running the Development Server

You can run the server using:

```bash
hugo server
```

This will start the development server and you can view your site by opening `localhost:1313` in your browser. Any changes you make will automatically reload in the browser.

## Deploying to GitHub Pages

Now that your site is ready, let's deploy it to GitHub Pages using GitHub Actions and the gh-pages workflow.

### Step 1: Create a GitHub Repository

First, create a new repository on GitHub with the name `username.github.io`, where `username` is your GitHub username. This is important because GitHub automatically serves sites from repositories with this naming pattern.

### Step 2: Push Your Hugo Site to GitHub

Initialize your repository if you haven't already, and push your code:

```bash
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/username/username.github.io.git
git push -u origin main
```

### Step 3: Create GitHub Actions Workflow

You have to create a GitHub Actions workflow file to automate the deployment. Create a new directory `.github/workflows` in your project root:

```bash
mkdir -p .github/workflows
```

There you have to configure the workflow the add the public folders content in the gh-pages branch. 

### Step 4: Configure GitHub Pages

Once you've pushed the workflow file, you need to configure GitHub Pages settings:

1. Go to your repository on GitHub
2. Click on **Settings** > **Pages**
3. Under **Source**, select **GitHub Actions**

### Step 5: Deploy

Now commit and push the workflow file:

```bash
git add .github/workflows/deploy.yml
git commit -m "Add GitHub Actions workflow for deployment"
git push
```

GitHub Actions will automatically build and deploy your site. You can check the progress in the **Actions** tab of your repository. Once the workflow completes successfully, your site will be live at `https://username.github.io`.

## Conclusion

That's it! You now have a fully functional Hugo site deployed to GitHub Pages. Every time you push changes to the main branch, GitHub Actions will automatically rebuild and redeploy your site. You can continue adding new posts, customizing your theme, and enjoying the blazing-fast performance that Hugo provides.

Thank You!