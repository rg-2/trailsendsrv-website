# Security Best Practices for this Repo

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
- Forks prevented from running deployments, even if they somehow got secrets.
### 3. Branch Protection
- Require pull requests before merging to `main`
### 4. EC2 Security Group
Limit SSH access:
- Dedicated SSH key used for deployments:
- IDEAL: Implement to OIDC
    - Until Then: Whitelist IP ranges

### Audit Logs
Periodically Review
- Who accessed secrets (you can't see values, but can see access)
- Deployment history
- Permission changes

## If Compromised:
1. Rotate all keys immediately in GitHub Secrets
2. Generate new SSH key pair
3. Update EC2 authorized_keys
4. Review GitHub audit logs
5. Check EC2 access logs
