# GitHub Pages Deployment Setup

## Configuration Checklist

### 1. Enable GitHub Pages

- Go to repository Settings → Pages
- Source: **GitHub Actions** (not "Deploy from a branch")
- This allows the workflow to deploy directly

### 2. Verify Workflow Permissions

- Go to repository Settings → Actions → General
- Under "Workflow permissions", ensure:
  - ✅ "Read and write permissions" is selected
  - ✅ "Allow GitHub Actions to create and approve pull requests" is checked

### 3. Test the Workflow

Run the workflow manually:

```bash
# Or via GitHub UI: Actions → Deploy FourierSynth to GitHub Pages → Run workflow
```

### 4. Monitor Deployment

After pushing or running manually:

1. Check Actions tab for workflow progress
2. Deployment typically takes 2-5 minutes
3. Site will be available at: `https://apofenic.github.io/`

## Workflow Details

**File**: `.github/workflows/deploy-fouriersynth.yml`

**Triggers**:

- Push to `main` branch
- Manual trigger (`workflow_dispatch`)
- Repository dispatch from FourierSynth (optional)

**Process**:

1. Checks out this repository
2. Sets up Node.js 18 with Yarn caching
3. Clones FourierSynth repo
4. Installs dependencies (`yarn install --frozen-lockfile`)
5. Builds the app (`yarn build`)
6. Clears existing content (preserves `.git` and `.github`)
7. Copies build output to root
8. Creates `.nojekyll` file (required for apps with underscored files)
9. Commits and pushes changes
10. Deploys to GitHub Pages

## Troubleshooting

### Build Fails

- Check FourierSynth repository build status
- Verify Node.js version compatibility
- Check workflow logs in Actions tab

### Deploy Fails

- Verify GitHub Pages is set to "GitHub Actions" source
- Check workflow permissions (Settings → Actions → General)
- Ensure Pages is enabled in repository settings

### Site Shows 404

- Wait a few minutes after deployment
- Check if `.nojekyll` file exists
- Verify deployment succeeded in Actions tab

## Optional: Auto-Deploy on Source Changes

To automatically deploy when FourierSynth updates, see README.md for instructions on setting up repository dispatch.
