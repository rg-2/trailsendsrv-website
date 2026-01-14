# Security Best Practices for Public Repository

This repository is my **public** playground, with the goal to practice DevOps/CI-CD while keeping infrastructure secure.

## Public
- HTML/CSS/JavaScript files (already publicly accessible via website)
- GitHub Actions workflow files
- Documentation and README files
- Repository structure and code organization

## Private (Secured via GitHub Secrets)
- SSH private keys
- Server IP addresses
- Server credentials
- Any API keys or tokens

## Security Measures Implemented

### 1. GitHub Secrets
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

## Additional Hardening

### GitHub Environments
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

## If Compromised:
1. Rotate all keys immediately in GitHub Secrets
2. Generate new SSH key pair
3. Update EC2 authorized_keys
4. Review GitHub audit logs
5. Check EC2 access logs
