# Indy Center Infrastructure

This repository contains the infrastructure as code (IaC) for the Indy Center platform. We use GitOps principles with ArgoCD to manage our Kubernetes-based infrastructure.

## Architecture Overview

Our infrastructure is built on [k3s](https://k3s.io/), a lightweight Kubernetes distribution, with the following key components:

### Core Infrastructure

- **[ArgoCD](https://argo-cd.readthedocs.io/)**: Manages all deployments using GitOps
- **[Traefik](https://traefik.io/)**: Handles ingress traffic and TLS termination
- **[cert-manager](https://cert-manager.io/)**: Automates certificate management
- **[Sealed Secrets](https://sealed-secrets.netlify.app/)**: Securely manages Kubernetes secrets in Git

### Directory Structure

```
infrastructure/
├── argocd/          # ArgoCD configuration
├── cert-manager/    # Certificate management
├── monitoring/      # Monitoring stack
├── shared-secrets/  # Shared sealed secrets
└── traefik/        # Ingress configuration
```

## GitOps Workflow

We follow GitOps principles:

1. Git is the single source of truth
2. All changes are made through pull requests
3. ArgoCD automatically syncs the cluster state with Git
4. Infrastructure changes are declarative and version controlled

## Cluster Management Links

- ArgoCD - https://argocd.zid-internal.com
- Grafana - https://metrics.zid-internal.com

## Other Org Links

- Main Website - https://zidartcc.org

## Getting Started

### Prerequisites

- kubectl
- kubeseal (for sealed secrets)
- Access to a k3s cluster

## Security

This repository follows security best practices:

- Credentials are managed through sealed secrets
- TLS certificates are automatically managed
- Authentication is handled through identity providers
- Network policies control pod-to-pod communication

## License

MIT License

Copyright (c) 2025 Indy Center

---

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

---

Built with ❤️ by the Indy Center Tech Team
