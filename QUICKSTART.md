# Quick Start: Deploy FourierSynth to GitHub Pages

## What Was Set Up

This repository now automatically deploys the [FourierSynth](https://github.com/Apofenic/FourierSynth) build to GitHub Pages.

## Files Created

- `.github/workflows/deploy-fouriersynth.yml` - GitHub Actions workflow
- `.github/SETUP.md` - Detailed setup and troubleshooting guide
- `README.md` - Updated with deployment information

## Next Steps

### 1. Commit and Push Changes

```bash
git add .
git commit -m "feat: add automated FourierSynth deployment to GitHub Pages"
git push origin main
```

### 2. Enable GitHub Pages

1. Go to https://github.com/Apofenic/Apofenic.github.io/settings/pages
2. Under "Build and deployment":
   - **Source**: Select "GitHub Actions" (NOT "Deploy from a branch")
3. Save

### 3. Configure Workflow Permissions

1. Go to https://github.com/Apofenic/Apofenic.github.io/settings/actions
2. Scroll to "Workflow permissions"
3. Select "Read and write permissions"
4. Check "Allow GitHub Actions to create and approve pull requests"
5. Save

### 4. Trigger First Deployment

The workflow will trigger automatically when you push, OR you can trigger manually:

1. Go to https://github.com/Apofenic/Apofenic.github.io/actions
2. Click "Deploy FourierSynth to GitHub Pages" in the left sidebar
3. Click "Run workflow" → "Run workflow"

### 5. Verify Deployment

- Watch the workflow progress in the Actions tab
- After completion (2-5 minutes), visit: **https://apofenic.github.io/**

## What Happens on Each Deployment

1. ✅ Clones FourierSynth repository
2. ✅ Installs dependencies with Yarn
3. ✅ Builds the React app (`yarn build`)
4. ✅ Clears old content from this repo
5. ✅ Copies new build files
6. ✅ Commits and pushes changes
7. ✅ Deploys to GitHub Pages

## Future Deployments

Every time you push to this repo's `main` branch, it will automatically rebuild and deploy FourierSynth.

To manually trigger a deployment, use the GitHub Actions interface as described in step 4.

## Optional: Auto-Deploy on FourierSynth Updates

See `README.md` for instructions on setting up automatic deployments whenever the FourierSynth repository is updated.

## Troubleshooting

See `.github/SETUP.md` for detailed troubleshooting steps.
