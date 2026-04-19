# Janken

A static website hosted on GitHub Pages, built with plain HTML and CSS.

## Project structure

```
Janken/
  .github/
    workflows/
      deploy.yml      ← Automated deployment workflow
  src/
    index.html         ← Main page of the website
    styles.css         ← Stylesheet shared across pages
  LICENSE
  README.md
```

All website files live inside the `src/` folder. Everything in that folder is published to GitHub Pages exactly as-is — no build step, no framework, just your HTML and CSS served directly.

## How deployment works

This project uses **GitHub Actions** to automatically publish the site whenever changes are pushed to the `main` branch. You do not need to run any commands to deploy — it happens on its own.

Here is what happens step by step:

1. You push your changes to the `main` branch on GitHub.
2. GitHub detects the push and runs the workflow defined in `.github/workflows/deploy.yml`.
3. The workflow takes every file inside the `src/` folder and uploads it to GitHub Pages.
4. After a few seconds your changes are live on the website.

You can check the status of a deployment by going to the **Actions** tab in your GitHub repository. Each run shows whether it succeeded or failed, and you can click into it for details.

## How to work on the site

### What you need

- [Git](https://git-scm.com/downloads) installed on your computer.
- A code editor. [Visual Studio Code](https://code.visualstudio.com/) (VS Code) is a great free option.
- A GitHub account with access to this repository.

### Getting started (first time only)

1. Open a terminal (Command Prompt, PowerShell, or the built-in terminal in VS Code).
2. Navigate to the folder where you want to store the project:
   ```
   cd Documents/GitHub
   ```
3. Clone the repository:
   ```
   git clone https://github.com/afagizmo/Janken.git
   ```
4. Open the project folder in VS Code:
   ```
   code Janken
   ```

You now have a local copy of the project. You can open and edit any file in the `src/` folder.

### Making changes and publishing them

After you have edited your files, follow these steps to push your changes live:

1. **Save your files** in VS Code (Ctrl+S).
2. Open the **Source Control** panel in VS Code by clicking the branch icon in the left sidebar (or press Ctrl+Shift+G).
3. You will see a list of changed files. Click the **+** icon next to each file to **stage** it (this tells Git which changes you want to include).
4. Type a short description of what you changed in the message box at the top, for example: `Update homepage heading`.
5. Click the **Commit** button (checkmark icon) to save the changes locally.
6. Click **Sync Changes** (or the push/pull arrows) to upload your commit to GitHub.

That's it. GitHub Actions will pick up your push and deploy the updated site automatically.

**Using the terminal instead of the VS Code UI:**

```
git add .
git commit -m "Update homepage heading"
git push
```

### Pulling the latest changes

If someone else has pushed changes, you need to pull them before you start working so you have the latest version:

- In VS Code: click the **Sync Changes** button, or
- In the terminal:
  ```
  git pull
  ```

Always pull before you start editing to avoid conflicts.

## How to add new pages

1. Create a new HTML file inside the `src/` folder, for example `src/about.html`.
2. Write your HTML in that file. Make sure to link the shared stylesheet in the `<head>`:
   ```html
   <link rel="stylesheet" href="styles.css">
   ```
3. To let visitors navigate to your new page, add a link to it from `index.html` (or any other page):
   ```html
   <a href="about.html">About</a>
   ```
4. Commit and push your changes. The new page will be available at `https://<your-username>.github.io/Janken/about.html`.

You can also organise pages into subfolders. For example, `src/guides/setup.html` would be available at `.../Janken/guides/setup.html`. If you do this, adjust relative paths to the stylesheet accordingly (e.g. `href="../styles.css"`).

## Setting up GitHub Pages (one-time setup)

Before the deployment workflow can publish your site, you need to configure GitHub Pages in the repository settings:

1. Go to your repository on GitHub: https://github.com/afagizmo/Janken
2. Click **Settings** (the gear icon near the top of the page).
3. In the left sidebar, click **Pages**.
4. Under **Build and deployment**, find the **Source** dropdown.
5. Select **GitHub Actions** from the dropdown.
6. Click **Save** if prompted.

No other configuration is needed. The next time you push to `main`, the workflow will deploy your site. Your site will be available at:

```
https://afagizmo.github.io/Janken/
```
