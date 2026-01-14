# TrailsEndSRV - Website

Fun personal project/website hosted on AWS EC2 with automated deployment via GitHub Actions.

**About**: This is a public repo to play with DevOps/CI-CD and GitHub. See [SECURITY.md](SECURITY.md) for details.

## Sites

- **Landing Page**: https://trailsendsrv.com
- **Remote Desktop**: https://guac.trailsendsrv.com (secured)
- **Resume**: https://res.trailsendsrv.com

## Structure

```
├── landing/           # Main landing page
├── resume/            # Yep... a Resume :-)
├── .github/workflows/ # GitHub Actions for auto-deployment
└── SECURITY.md        # Security practices documentation
```
The guacamole remote access pages is managed outside of this repository for now.

## Deployment

GitHub Actions used to automatically deploy to EC2 when changes to `main` are approved.


## Technologies

- **Hosting**: AWS EC2
- **Web Server**: Nginx
- **SSL**: Let's Encrypt
- **CI/CD**: GitHub Actions
- **Remote Access**: Apache Guacamole via WireGuard VPN
