# TrailsEnd SRV Website

Personal website hosted on AWS EC2 with automated deployment via GitHub Actions.

**Note**: This repository is public to demonstrate DevOps/CI-CD practices while keeping infrastructure secure through GitHub Secrets. See [SECURITY.md](SECURITY.md) for details.

## Sites

- **Landing Page**: https://trailsendsrv.com
- **Remote Desktop**: https://guac.trailsendsrv.com (secured)
- **Resume**: https://res.trailsendsrv.com

## Structure

```
├── landing/           # Main landing page with navigation
├── resume/            # Professional resume
├── .github/workflows/ # GitHub Actions for auto-deployment
└── SECURITY.md        # Security practices documentation
```

## Deployment

This repository uses GitHub Actions to automatically deploy to EC2 when changes are pushed to the `main` branch.

### Manual Deployment

You can also trigger deployment manually from the Actions tab in GitHub.

## Local Development

Edit files locally and push to deploy:

```bash
# Edit files
nano landing/index.html
nano resume/index.html

# Commit and push
git add .
git commit -m "Update content"
git push
```

Changes will be live within ~30 seconds of pushing.

## Technologies

- **Hosting**: AWS EC2
- **Web Server**: Nginx
- **SSL**: Let's Encrypt
- **CI/CD**: GitHub Actions
- **Remote Access**: Apache Guacamole via WireGuard VPN
