# Apofenic.github.io

Automated deployment of [FourierSynth](https://github.com/Apofenic/FourierSynth) to GitHub Pages.

## How It Works

This repository automatically builds and deploys the FourierSynth app using GitHub Actions:

1. **Automatic Deployment**: Triggered on every push to this repo's `main` branch
2. **Manual Deployment**: Can be triggered manually via GitHub Actions
3. **Build Process**:
   - Clones the FourierSynth repository
   - Installs dependencies with Yarn
   - Builds the React app (`yarn build`)
   - Copies the build output to this repo
   - Deploys to GitHub Pages

## Manual Deployment

To trigger a manual deployment:

1. Go to the [Actions tab](https://github.com/Apofenic/Apofenic.github.io/actions)
2. Select "Deploy FourierSynth to GitHub Pages"
3. Click "Run workflow"

## Optional: Auto-Deploy on FourierSynth Updates

To automatically deploy when FourierSynth is updated, add this workflow to the FourierSynth repo:

```yaml
# .github/workflows/trigger-deploy.yml
name: Trigger Deployment

on:
  push:
    branches:
      - main

jobs:
  trigger:
    runs-on: ubuntu-latest
    steps:
      - name: Trigger deployment in Apofenic.github.io
        run: |
          curl -X POST \
            -H "Accept: application/vnd.github.v3+json" \
            -H "Authorization: token ${{ secrets.DEPLOY_TOKEN }}" \
            https://api.github.com/repos/Apofenic/Apofenic.github.io/dispatches \
            -d '{"event_type":"fouriersynth-updated"}'
```

**Note**: You'll need to create a Personal Access Token with `repo` scope and add it as `DEPLOY_TOKEN` secret in the FourierSynth repository settings.
