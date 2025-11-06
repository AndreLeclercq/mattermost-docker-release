# Mattermost Team Edition
This repository automatically syncs official Mattermost files and builds a Docker image always up-to-date with the latest v10.11 ESR version.

## 🎯 Objective
- Fetch the latest v10.11.x ESR version from the official Mattermost repo
- Download official files (Dockerfile, passwd, entrypoint.sh)
- Build and publish to Docker Hub with the `esr-10.11` tag

## 🐳 Docker Image
**Available image:** `andreleclercq/mattermost-team-edition:esr-10.11`

## 🔄 How it works
1. **Daily check** at 6 AM UTC
2. **Find the latest v10.11.x release** from GitHub
3. **Download official files** from Mattermost repo
4. **Build and push** to Docker Hub (only if new version or forced)

## 🏷️ Available tags
- `andreleclercq/mattermost-team-edition:esr-10.11` ← **Main tag (tracks v10.11.x)**
- `andreleclercq/mattermost-team-edition:esr-latest` ← **Always latest ESR tracked**
- `andreleclercq/mattermost-team-edition:10.11.6` (exact version)
- `andreleclercq/mattermost-team-edition:v10.11.6` (with v prefix)

## ⚙️ Configuration
Required GitHub secrets:
- `DOCKER_USERNAME`: Docker Hub username  
- `DOCKER_PASSWORD`: Docker Hub token

Required environment variable (in workflow):
- `ESR_MAJOR_VERSION`: Set to `"10.11"` to track v10.11 ESR

## 🔨 Manual trigger
You can manually trigger a build from GitHub Actions:
1. Go to **Actions** tab
2. Select **"Sync Mattermost ESR from Official Repo"**
3. Click **"Run workflow"**
4. Check **"Force rebuild"** to rebuild even if version already exists

## 📁 Structure
```
.
├── .github/workflows/sync-mattermost-esr.yml  # Automatic workflow
├── Dockerfile                                  # Downloaded automatically
├── entrypoint.sh                               # Downloaded automatically
├── passwd                                      # Downloaded automatically  
└── README.md                                   # This file
```

The `Dockerfile`, `entrypoint.sh` and `passwd` files are automatically synced from the official Mattermost repository.

## 🚀 Usage
Simply pull the image with the `esr-10.11` tag to always get the latest v10.11.x version:
```bash
docker pull andreleclercq/mattermost-team-edition:esr-10.11
```

## 📋 About ESR
v10.11 is Mattermost's Extended Support Release (ESR), supported until August 15, 2026. ESR versions receive security fixes and are ideal for production environments prioritizing stability.

The automation ensures your Docker image stays updated without manual intervention!
