# Security Best Practices for Public Repository

This repository is **public** to demonstrate DevOps/CI-CD skills while keeping infrastructure secure.

## What's Public (Safe)
✅ HTML/CSS/JavaScript files (already publicly accessible via website)  
✅ GitHub Actions workflow files (demonstrates CI/CD expertise)  
✅ Documentation and README files  
✅ Repository structure and code organization  

## What's Private (Secured via GitHub Secrets)
🔒 SSH private keys  
🔒 Server IP addresses  
🔒 Server credentials  
🔒 Any API keys or tokens  

## Security Measures Implemented

### 1. GitHub Secrets
All sensitive data stored as encrypted secrets:
- `SSH_PRIVATE_KEY` - Never visible in code or logs
- `EC2_HOST` - Server IP hidden from public
- `EC2_USER` - Login credentials protected

### 2. Repository Protection
```yaml
if: github.repository == 'YOUR-USERNAME/trailsendsrv-website'
```
Prevents forks from running deployments, even if they somehow got secrets.

### 3. Branch Protection (Recommended)
Enable in GitHub Settings → Branches:
- Require pull request reviews before merging to `main`
- Require status checks to pass
- Prevents accidental direct pushes to production

### 4. EC2 Security Group
Limit SSH access:
- Only allow SSH (port 22) from GitHub Actions IPs or your IPs
- Use AWS security groups to whitelist IP ranges
- Consider using GitHub's published IP ranges

### 5. Separate Deployment Key
Use a dedicated SSH key for deployments:
- Not your personal SSH key
- Limited permissions (only needs to copy files to /tmp)
- Can be revoked without affecting other access

## What Potential Employers See

When someone views your public repo, they see:
- Clean, organized code structure
- Professional CI/CD pipeline
- Automated deployment workflow
- Security-conscious practices
- Real-world infrastructure management skills

They **cannot** see:
- Your server IP or credentials
- SSH keys or access tokens
- Any secrets defined in GitHub

## Additional Hardening (Optional)

### Use GitHub Environments
Create a "production" environment with:
- Required reviewers
- Deployment protection rules
- Environment-specific secrets

### Audit Logs
GitHub provides audit logs showing:
- Who accessed secrets (you can't see values, but can see access)
- Deployment history
- Permission changes

### IP Whitelisting
Lock down EC2 SSH to only GitHub Actions IPs:
```bash
# GitHub Actions IP ranges (check docs for current list)
# Add to EC2 Security Group port 22 rules
```

## If Something Goes Wrong

If secrets are ever compromised:
1. Rotate all keys immediately in GitHub Secrets
2. Generate new SSH key pair
3. Update EC2 authorized_keys
4. Review GitHub audit logs
5. Check EC2 access logs

## Demonstrating This Project

When sharing this repo in job applications:
- Highlight the automated deployment pipeline
- Explain the security measures implemented
- Show how secrets are managed safely
- Demonstrate understanding of least-privilege access
- Discuss the trade-off between public showcase and security

This approach shows you understand **both** modern DevOps practices **and** security considerations.
