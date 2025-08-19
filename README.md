# Mattermost Team Edition - Always Updated v10.x

This repository automatically syncs official Mattermost files and builds a Docker image always up-to-date with the latest v10.x version.

## 🎯 Objective

- Fetch the v10.x version tagged as "latest" from the official Mattermost repo
- Download official files (Dockerfile, passwd)
- Build and publish to Docker Hub with the `release-10` tag

## 🐳 Docker Image

**Available image:** `andreleclercq/mattermost-team-edition:release-10`

## 🔄 How it works

1. **Daily check** at 6 AM UTC
2. **If the "latest" GitHub release is v10.x** → automatic sync
3. **Download official files** from Mattermost repo
4. **Build and push** to Docker Hub

## 🏷️ Available tags

- `andreleclercq/mattermost-team-edition:release-10` ← **Main tag**
- `andreleclercq/mattermost-team-edition:10.11.0` (exact version)
- `andreleclercq/mattermost-team-edition:v10.11.0` (with v prefix)

## ⚙️ Configuration

Required GitHub secrets:
- `DOCKER_USERNAME`: Docker Hub username  
- `DOCKER_PASSWORD`: Docker Hub token

## 📁 Structure

```
.
├── .github/workflows/docker-build.yml  # Automatic workflow
├── Dockerfile                          # Downloaded automatically
├── passwd                              # Downloaded automatically  
└── README.md                           # This file
```

The `Dockerfile` and `passwd` files are automatically synced from the official Mattermost repository.

## 🚀 Usage

Simply pull the image with the `release-10` tag to always get the latest v10.x version:

```bash
docker pull andreleclercq/mattermost-team-edition:release-10
```

## 📋 Requirements

- GitHub repository with this workflow
- Docker Hub account with push permissions
- GitHub secrets configured properly

The automation ensures your Docker image stays updated without manual intervention!
