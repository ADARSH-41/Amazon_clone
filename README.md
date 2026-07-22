# Amazon home page clone using React and Deployment with GitHub Actions

This repository is configured to automatically build and deploy the React application to **GitHub Pages** using **GitHub Actions** whenever changes are pushed to the `main` branch.

---

## ⚙️ Want to run locally?
1. Clone the repository into your local file system using the command `git clone https://github.com/ADARSH-41/Amazon_clone.git`
2. Make sure node with latest version is installed in your system. you can check the node version with the command `node -v`
3. Now install the dependencies using the command `npm install`
4. Remove `"homepage": "https://adarsh-41.github.io/Amazon_clone"` from `package.json`
5. After installation of all the dependencies, execute the command `npm start` to start the application on localhost 3000 port.

---

## 🚀 Setting Up Deployment for Your Own Repository

If you are cloning or setting up this project from scratch, ensure the following GitHub configurations are enabled:

### 1. Enable GitHub Actions for GitHub Pages
1. Navigate to your repository on GitHub.
2. Go to **Settings** > **Pages**.
3. Under **Build and deployment** > **Source**, select **GitHub Actions** (do NOT select "Deploy from a branch").

### 2. Configure Base Path (If Applicable)
Depending on your build tool, ensure your app is configured for GitHub Pages routing:

-> If you are using vite, make sure to add  `base: '/<repository-name>/'` in your vite.config.js.
- **Vite (`vite.config.js`)**:
  ```js
  export default defineConfig({
    base: '/<repository-name>/',
    plugins: [react()],
  });

-> If you are using create-react-app, ensure to add 
```json 
"homepage": "https://<your-username>.github.io/Amazon_clone"
```
   in your `package.json` file.

### 3. Handle Static Assets (.nojekyll)
GitHub Pages defaults to processing sites with Jekyll, which ignores files starting with underscores ( _ ). To prevent build assets from breaking: Include a `.nojekyll` file in your repository root or public/ folder.

### 4. Update path variable in deploy.yml file.
Based on your build tool, update `path` as follows:

- for vite use  `path: ./dist`
- for Create React App use  `path: ./build`

---

## 🛠️ How the Github Deployment Works?

The deployment pipeline is managed by a custom GitHub Actions workflow located at `.github/workflows/deploy.yml`.

### Automated Workflow Steps:
1. **Trigger**: Triggers automatically on every `push` to the `main` branch (or via manual trigger from the **Actions** tab).
2. **Environment Setup**: Provisions an `ubuntu-latest` runner and installs Node.js.
3. **Build Stage**:
   - Runs `npm ci` to install project dependencies.
   - Runs `npm run build` to compile static assets.
4. **Artifact Upload**: Packages the output directory (`dist/` or `build/`) as a GitHub Pages artifact.
5. **Deployment**: Deploys the built artifact directly to GitHub Pages using official GitHub Actions.

---

In past, I had deployed the application in codesandbox.io the below is the deployment source code repository and deployed web app's page.
- codesandbox.io repository : https://codesandbox.io/s/ancient-dawn-7y6k6u
- Deployed web app : https://7y6k6u.csb.app/
