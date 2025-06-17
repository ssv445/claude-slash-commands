# GitHub Actions Workflows

This directory contains GitHub Actions workflows for the Claude Slash Commands Registry.

## Workflows

- **AI Analysis Pipeline**: Automatically analyzes submitted command packages for security and quality
- **Package Publishing**: Handles the publishing of approved packages to the registry
- **Website Deployment**: Builds and deploys the registry website
- **Security Scanning**: Regular security audits of published commands

## Workflow Structure

Each workflow follows our standard pipeline:
1. Security Analysis
2. Quality Assessment  
3. Functionality Verification
4. Auto-approval or Human Review
5. Publishing and CDN Distribution

For more information, see our [CI/CD Documentation](../../docs/cicd.md).