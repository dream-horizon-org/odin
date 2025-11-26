# Odin

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

**Production-ready deployment platform for your cloud**

[What is Odin?](#what-is-odin) • [Core Concepts](#core-concepts) • [Installation](#installation) • [FAQ](#frequently-asked-questions)

---

## Table of Contents

- [What is Odin?](#what-is-odin)
- [Core Concepts](#core-concepts)
- [Installation](#installation)
- [FAQ](#frequently-asked-questions)
- [Getting Started Tutorial](https://ds-horizon.github.io/odin/introduction/getting-started/#next-steps-deploy-your-first-service)
- [References](#references-and-links)

---

## What is Odin?

Every high-growth business faces the same bottleneck: engineers debugging broken shared environments instead of building features. Odin solves this by enabling you to **define software once and deploy it anywhere, any number of times**, moving software operations from engineers to machines.

**Watch the introduction**:

[![What is Odin?](https://img.youtube.com/vi/CI1SWkC9hW8/0.jpg)](https://youtu.be/CI1SWkC9hW8)

With Odin, you create simple JSON blueprints of your application called `Service Definitions`. Odin understands these definitions, provisions isolated environments, and deploys all required services automatically. Your developers get the private environments they need without knowing the complex wiring and configuration of other services.

**Key capabilities:**

- **Ephemeral Environments on Demand**: Spin up isolated environments instantly for testing and development—create one or five with a single command
- **Environment Parity**: The same Service Definition works consistently across `development`, `staging`, and most importantly `production`
- **Zero Configuration Knowledge Required**: Deploy services without needing to understand internal dependencies and wiring
- **Guaranteed Deployment**: Built-in validation and rollback capabilities ensure reliable deployments

Odin turns the chaos of shared environments into a factory of parallel innovation, letting your team ship faster without operational overhead.

---

## Core Concepts

New to Odin? **[The Little Odin-er](./THE_LITTLE_ODIN-ER.md)** is a friendly, conversational guide that explains the fundamental concepts through simple questions and answers.

Learn about:
- **Environments**: Logical spaces where services live
- **Services & Components**: How your application is structured
- **Service Definitions**: The JSON blueprints that power Odin
- **Deploy vs Operate**: Understanding the lifecycle
- **Artefact Management**: How Odin handles your builds

No prerequisites, no jargon—just curiosity required.

---

## Installation

Ready to get started? Follow our comprehensive installation guide:

**📖 [Installation Guide](https://ds-horizon.github.io/odin/introduction/getting-started/)**

The guide covers:
- Prerequisites and system requirements
- One-command installation for local development
- CLI setup and configuration
- Cloud deployment options
- Uninstallation instructions

---

## Frequently Asked Questions

### General Questions

**Q: What is the minimum Kubernetes version required?**

A: Kubernetes v1.30 or later. Versions 1.30-1.34 are tested and recommended.

**Q: Can I install Odin on Minikube?**

A: Yes, but Kind is recommended for local development. Minikube may require additional memory configuration.

**Q: How much does Odin cost?**

A: Odin is open-source and free to use under the MIT License. You only pay for the infrastructure it runs on.

### Installation Questions

**Q: Can I use external databases instead of internal ones?**

A: Yes! You can configure external MySQL, Redis, and Elasticsearch:

```yaml
mysql:
  external:
    enabled: true
    master:
      host: "your-rds-endpoint.com"
redis:
  external:
    enabled: true
    host: "your-redis-endpoint.com"
elasticsearch:
  external:
    enabled: true
    host: "your-es-endpoint.com"
```

**Q: How do I customize resource allocations?**

A: Create a custom values file:

```yaml
deployer:
  resources:
    requests:
      cpu: 500m
      memory: 1Gi
    limits:
      cpu: 2
      memory: 4Gi
```

Then install with: `./install.sh --values custom-values.yaml`

### Configuration Questions

**Q: What are ES256 keys and why are they required?**

A: ES256 (ECDSA with P-256 curve and SHA-256) keys are used for secure authentication between components. They're automatically generated during installation or you can provide your own.


**Q: How do I enable high availability?**

A: Increase replica counts in your values file:

```yaml
deployer:
  replicaCount: 3
accountManager:
  replicaCount: 2
mysql:
  mysql:
    size: 3
redis:
  architecture: replication
  master:
    count: 1
  replica:
    replicaCount: 2
```

### Cloud-Specific Questions

**Q: Can I install on EKS/GKE/AKS?**

A: Yes! Odin works on all major cloud Kubernetes platforms.


**Q: How do I expose Odin externally?**

A: Use Kubernetes Ingress or LoadBalancer:

```yaml
deployer:
  service:
    type: LoadBalancer  # or configure Ingress
```

### Operational Questions

**Q: How do I backup Odin data?**

A: Enable automated backups for MySQL:

```yaml
mysql:
  backup:
    enabled: true
    schedule:
      - name: "daily-backup"
        schedule: "0 2 * * *"
        keep: 7
        storageName: s3local
```

Backups are stored in MinIO (`odin-backup-bucket`).

**Q: How do I upgrade Odin?**

A: Use Helm upgrade:

```bash
helm repo update
helm upgrade odin odin/odin -n odin --values your-values.yaml
```

For major version upgrades, always review the release notes and backup your data first.

**Q: How do I completely remove Odin?**

A: See the [Installation Guide](https://ds-horizon.github.io/odin/introduction/getting-started/) for uninstallation instructions.

---


## References and Links

### Official Resources

#### Repositories

- **[odin](https://github.com/ds-horizon/odin)** - Main repository with Helm charts and installation scripts
- **[odin-deployer](https://github.com/ds-horizon/odin-deployer)** - API backend to handle environment, service components deployment & operations data
- **[odin-account-manager](https://github.com/ds-horizon/odin-account-manager)** - Manages organizations and accounts
- **[odin-orchestrator](https://github.com/ds-horizon/odin-orchestrator)** - Main engine that orchestrates the deployments
- **[odin-discovery](https://github.com/ds-horizon/odin-discovery)** - An abstraction over discovery providers to streamline discovery management
- **[odin-discovery-controller](https://github.com/ds-horizon/odin-discovery-controller)** - Kubernetes controller for service discovery
- **[odin-components](https://github.com/ds-horizon/odin-components)** - Production-ready components supported by the Odin team
- **[odin-cli](https://github.com/ds-horizon/odin-cli)** - Command-line interface for Odin

#### Links

- **Issue Tracker**: https://github.com/ds-horizon/odin/issues
- **Releases**: https://github.com/ds-horizon/odin/releases


### Community

- **License**: MIT License (see [LICENSE](LICENSE))
- **Contributing**: See [CONTRIBUTING.md](CONTRIBUTING.md)

### Support

For issues, questions, or contributions:

1. **Check Documentation**: Review this guide and FAQ
2. **Search Issues**: Check if someone else has the same problem
3. **Create Issue**: File a detailed issue on GitHub

---

## Acknowledgments

Odin is built on top of excellent open-source projects:
- Kubernetes community
- Helm project
- KEDA maintainers
- Percona team
- Bitnami chart contributors
- All other open-source dependencies
