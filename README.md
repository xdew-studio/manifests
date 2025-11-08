<h1 align="center">XDEW Studio - Manifests</h1>

<p align="center">
  Kubernetes deployment manifests for XDEW Studio platform using Kustomize
</p>

---

## Overview

The XDEW Studio Manifests repository contains all Kubernetes deployment configurations for the XDEW platform. Built using Kustomize, it provides a structured approach to managing deployments across different environments with a focus on scalability, security, and maintainability.

## Table of Contents

- [Features](#features)
- [Prerequisites](#prerequisites)
- [Structure](#structure)
- [Installation](#installation)
- [Configuration](#configuration)
- [Contributing](#contributing)

## Features

- **Kustomize-based Deployments** - Structured overlay management for different environments
- **Multi-Environment Support** - Separate configurations for test and production
- **Identity Management** - Keycloak-based authentication and authorization
- **Monitoring Stack** - Complete observability setup
- **Storage Solutions** - Persistent storage configurations
- **API Services** - Core backend API deployments
- **Console Application** - Frontend console deployment
- **API Documentation** - Swagger/OpenAPI documentation service

## Prerequisites

- kubectl CLI tool
- Kubernetes cluster access (1.20+)
- Kustomize (built into kubectl 1.14+)
- Access to container registry for XDEW images

## Structure

```
manifests/
├── apps/                    # Application manifests
│   ├── api/                # Backend API service
│   ├── console/            # Frontend console
│   └── api-docs/           # API documentation
├── identity/               # Keycloak identity management
├── monitoring/             # Monitoring and observability
└── storage/               # Persistent storage configurations
```

Each application follows the Kustomize base/overlay pattern:

- `base/` - Common resources and configurations
- `overlays/test/` - Test environment specific overrides
- `overlays/prod/` - Production environment specific overrides

## Installation

```bash
# Clone the repository
git clone <repository-url>
cd manifests

# Verify cluster access
kubectl cluster-info
```

## Configuration

### Environment Variables

Each overlay can override environment-specific configurations:

- **Test Environment**: Development settings, debug logging, test databases
- **Production Environment**: Production settings, optimized resources, production databases

### Resource Limits

Resource requests and limits are configured per environment:

- CPU and memory allocations
- Storage requirements
- Replica counts

### Secrets Management

Secrets are managed through Kubernetes secrets:

- Database credentials
- API keys
- TLS certificates
- Keycloak configuration

## Contributing

1. Follow Kubernetes best practices
2. Use Kustomize for configuration management
3. Test changes in test environment first
4. Update documentation for new services
5. Validate manifests before committing
6. Submit pull requests for review

### Validation Commands

```bash
# Validate Kubernetes manifests
kubectl apply --dry-run=client -k apps/api/overlays/test/

# Render Kustomize output
kubectl kustomize apps/api/overlays/test/
```

---

<p align="center">
  Part of the <strong>XDEW Studio</strong> ecosystem
</p>
