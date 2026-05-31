# Deploying Gemini Shader Pilot to GitHub Pages 🚀

This project has been fully optimized and pre-configured to be hosted as a static website on **GitHub Pages**! 

All asset paths are relative, ensuring that your app loads successfully whether it is opened directly, in sub-directories, or custom domains. We have added both **Automated CI/CD (GitHub Actions)** and a **Manual Deploy Script** so you can pick whichever deploy method you prefer.

---

## 🛠️ Configuration Completed For You
1. **GitHub Actions Workflow:** Created `.github/workflows/deploy.yml` which automatically builds and publishes the website to the `gh-pages` branch on every push.
2. **Deploy Scripts:** Added `deploy` and `predeploy` scripts to `package.json` for super simple manual deployments.
3. **Relative Build Paths:** Updated `vite.config.ts` (`base: './'`) and `index.html` to resolve static assets correctly across all subfolders.
4. **Local API Key Fallback:** Modified `/services/GeminiService.ts` to dynamically fetch the Gemini API Key from your browser's local storage first, ensuring you can use AI features in your static deployment.

---

## 🚀 Option 1: Automatic Deployment (Recommended)

GitHub Actions will build and deploy your application automatically every time you push code to your default branch (`main` or `master`).

### Step 1: Push your code to GitHub
If you haven't uploaded your repository to GitHub yet, run the following commands in your local directory terminal:
```bash
# Initialize a local Git repository (if not already done)
git init

# Add all files to the repository
git add .
git commit -m "Configure GitHub Pages automated hosting"

# Link your local repository to GitHub
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git

# Push your code to GitHub
git push -u origin main
```

### Step 2: Configure GitHub Repository Permissions
Once the code is on GitHub:
1. Open your repository on **GitHub.com**.
2. Go to **Settings** ⚙️ → **Actions** → **General**.
3. Under **Workflow permissions**, select **"Read and write permissions"** (this is required so the runner can publish the compiled folder to the `gh-pages` branch).
4. Click **Save**.

### Step 3: Enable Pages Branch
1. Under **Settings** ⚙️ → **Pages**.
2. In the **Build and deployment** section:
   - **Source:** Deploy from a branch.
   - **Branch:** Select `gh-pages` and folder `/ (root)`.
3. Click **Save**.
4. Within 1-2 minutes, you will see your live live URL, e.g., `https://<YOUR_USERNAME>.github.io/<YOUR_REPO_NAME>/`.

---

## 💻 Option 2: Manual Terminal Deployment

If you prefer to deploy manually using your local machine's command-line interface, we pre-configured the `gh-pages` package.

### Build and upload in one command:
Whenever you want to deploy latest updates, run:
```bash
npm run deploy
```
*Behind the scenes, this will compile the React bundle inside `/dist` and upload those assets directly onto the `gh-pages` branch for you.*

---

## 🔑 Activating Gemini AI Features on your Website

Because GitHub Pages is a static site host, your confidential server-side environment variables (like `GEMINI_API_KEY`) won't be exposed or bundled inside the static code for safety.

To use the AI Shader & Soundtrack features on your hosted site:
1. Open your deployed live URL.
2. Under the controls panel, tap the **System** tab.
3. Paste your personal **Google Gemini API Key** inside the **Custom Gemini API Key** password field.
4. The key is securely saved directly in your browser's local storage (`localStorage`) and is only sent directly to Google's official Gemini endpoint. It is never transmitted anywhere else.
