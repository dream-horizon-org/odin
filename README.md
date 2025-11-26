# Odin

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

**Production-ready deployment platform for your cloud**

[What is Odin?](#what-is-odin) • [Core Concepts](#core-concepts) • [Installation](#installation)

---

## Table of Contents

- [What is Odin?](#what-is-odin)
- [Core Concepts](#core-concepts)
- [Installation](#installation)
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

1. **Check Documentation**: Review this guide
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
