# 🚀 KubLand Organization

<div align="center">

![KubLand Logo](https://img.shields.io/badge/KubLand-🏠%20Homelab-blue?style=for-the-badge&logo=kubernetes)
![Kubernetes](https://img.shields.io/badge/Kubernetes-RKE2-326CE5?style=for-the-badge&logo=kubernetes)
![GitOps](https://img.shields.io/badge/GitOps-ArgoCD-EF7B4D?style=for-the-badge&logo=argocd)
![Security](https://img.shields.io/badge/Security-🔒%20Best%20Practices-green?style=for-the-badge)

**🏠 Advanced Multi-Cluster Kubernetes Homelab on Outscale Cloud**

*State-of-the-art infrastructure with maximum security and GitOps excellence*

</div>

---

## 🌟 About KubLand

Welcome to **KubLand** 🏠 - a cutting-edge homelab project that demonstrates enterprise-grade Kubernetes infrastructure using **RKE2** (Rancher Kubernetes Engine 2) on the **Outscale Cloud Provider**. Our organization showcases modern DevOps practices, GitOps workflows, and security-first approaches in a multi-cluster environment.

### 🎯 Mission Statement

> *"Building a secure, scalable, and maintainable Kubernetes homelab that serves as a blueprint for production-ready infrastructure while exploring the latest in cloud-native technologies."*

---

## 🏗️ Architecture Overview

```mermaid
graph TB
    subgraph "🌐 Outscale Cloud"
        subgraph "🏢 Main Cluster"
            MAIN[🏢 Main Cluster with ArgoCD]
            MAIN --> OMI[📦 OMI Image via Packer]
            MAIN --> TOOLS[🔧 Cluster Management Tools]
        end

        subgraph "🏭 Cluster Factory"
            BACKUP[🔄 Backup Cluster]
            AURELIEN[👨‍💻 Apps-Aurelien]
            THOMAS[👨‍💻 Apps-Thomas]
        end
    end

    subgraph "🔄 GitOps Flow"
        GIT[📁 Git Repository]
        ARGO[🚀 ArgoCD in Main Cluster]
    end

    GIT --> ARGO
    ARGO --> MAIN
    ARGO --> BACKUP
    ARGO --> AURELIEN
    ARGO --> THOMAS

    MAIN -.-> "🏭 Cluster Factory"

```

---

## 🛠️ Technology Stack

### 🎛️ Core Infrastructure
- **☸️ Kubernetes**: RKE2 (Rancher Kubernetes Engine 2)
- **☁️ Cloud Provider**: Outscale Cloud
- **🏗️ Infrastructure as Code**: Terraform
- **📦 Container Registry**: Harbor / Outscale Object Storage

### 🔄 GitOps & CI/CD
- **🚀 ArgoCD**: Application deployment and management
- **🔧 GitHub Actions**: CI/CD pipelines

### 💾 Storage & Data
- **🗄️ Rook Ceph**: Distributed storage system
- **🗃️ PostgreSQL**: Database clusters
- **📈 Prometheus**: Metrics collection
- **📊 Grafana**: Monitoring dashboards

### 🔐 Security & Secrets
- **🔑 HashiCorp Vault**: Secrets management
- **🔍 Trivy**: Vulnerability scanning
- **🔒 Kyverno**: Policy enforcement and admission control
  - Validates and mutates Kubernetes resources
  - Generates policies for security best practices
  - Enforces compliance and governance rules
- **🛡️ Network Policies**: Micro-segmentation
- **🔐 Cert-Manager**: TLS certificate management

### 📊 Observability
- **📈 Prometheus**: Metrics collection
- **📊 Grafana**: Visualization
- **📝 Vector + Loki**: Log aggregation and processing
- **📱 AlertManager**: Alerting

---

## 🏗️ Cluster Architecture

### 🚀 Deployment Process

Our homelab follows a **main cluster approach** where the main cluster creates and manages all other clusters:

1. **🏢 Main Cluster**: Primary RKE2 cluster created via `homelab-main` repository
   - Uses OMI (Outscale Machine Image) created with Packer
   - Hosts ArgoCD for GitOps management
   - Contains security components (Vault, Trivy, Kyverno)
   - Deploys other clusters via RKE2

2. **🏭 Cluster Factory**: From the main cluster, we create:
   - **🔄 Backup Cluster**: Disaster recovery and backup services
   - **👨‍💻 Apps-Aurelien**: Personal development environment
   - **👨‍💻 Apps-Thomas**: Personal development environment

3. **🚀 ArgoCD Management**: The main cluster hosts ArgoCD which manages application deployments across all clusters

### 🎯 Key Repositories

| Repository | Description | Status |
|------------|-------------|---------|
| 🏢 `homelab-main` | Main cluster with ArgoCD, security components, and cluster management | 🚧 Active |
| 🔄 `homelab-backup` | Backup cluster for disaster recovery | 🚧 Active |
| 👨‍💻 `homelab-apps-thomas` | Thomas personal development environment | 🚧 Active |
| 👨‍💻 `homelab-apps-aurelien` | Aurelien personal development environment | 🚧 Active |

*Note: Monitoring components (Prometheus, Grafana, Vector, Loki) are deployed in the main cluster*

---

## 🔒 Security Best Practices

### 🛡️ Security-First Approach

Our organization implements enterprise-grade security practices:

- **🔐 Zero-Trust Architecture**: All communications are encrypted and authenticated
- **🔑 Secrets Management**: HashiCorp Vault for centralized secrets
- **🛡️ Runtime Security**: Falco for real-time threat detection
- **🔍 Vulnerability Scanning**: Automated scanning with Trivy
- **📋 Policy Enforcement**: Kyverno for admission control and policy management
- **🌐 Network Segmentation**: Comprehensive network policies
- **🔒 RBAC**: Role-based access control with least privilege
- **📊 Security Monitoring**: Continuous security posture assessment

### 🔐 Security Compliance

- **📋 CIS Kubernetes Benchmark**: Full compliance implementation
- **🔒 Pod Security Standards**: Enforced across all clusters
- **🛡️ Network Policies**: Micro-segmentation for all workloads
- **🔍 Image Scanning**: All container images scanned for vulnerabilities
- **📊 Audit Logging**: Comprehensive audit trails

---

## 🚀 Getting Started

### 📋 Prerequisites

- **🏗️ Terraform**: Infrastructure as Code tool
- **📦 Packer**: For creating OMI images
- **🔑 Outscale Cloud**: Account and credentials
- **🐙 Git**: Version control system

### 🏃‍♂️ Bootstrap Process

1. **🔧 Clone the main repository**
   ```bash
   git clone https://github.com/kubland/homelab-main.git
   cd homelab-main
   ```

2. **📦 Build OMI image with Packer**
   ```bash
   packer build rke2-omi.pkr.hcl
   ```

3. **🏗️ Deploy main cluster**
   ```bash
   terraform init
   terraform plan
   terraform apply
   ```

4. **🏭 Create additional clusters**
   - The main cluster will manage the creation of:
     - Backup cluster (disaster recovery)
     - Apps-Aurelien (personal development)
     - Apps-Thomas (personal development)

---

## 🤝 Contributing

We welcome contributions from the community! Here's how you can get involved:

### 🎯 How to Contribute

1. **🍴 Fork** the repository
2. **🌿 Create** a feature branch (`git checkout -b feature/amazing-feature`)
3. **💾 Commit** your changes (`git commit -m 'Add amazing feature'`)
4. **📤 Push** to the branch (`git push origin feature/amazing-feature`)
5. **🔄 Open** a Pull Request

### 📋 Contribution Guidelines

- **📝 Documentation**: Update documentation for any changes
- **🧪 Testing**: Include tests for new features
- **🔒 Security**: Follow security best practices
- **📊 Monitoring**: Ensure observability for new components

---

## 📊 Project Status

### 🎯 Current Milestones

- [x] **🏗️ Infrastructure Setup**: Multi-cluster RKE2 deployment
- [x] **🔐 Security Foundation**: Vault, Falco, and policy enforcement
- [x] **🔄 GitOps Implementation**: ArgoCD and FluxCD setup
- [x] **📊 Monitoring Stack**: Prometheus, Grafana, and ELK
- [ ] **🚀 Application Deployment**: Core applications and services
- [ ] **🧪 Testing Framework**: Comprehensive testing suite
- [ ] **📚 Documentation**: Complete documentation site

### 📈 Roadmap

- **Q4 2025**: Core infrastructure and security implementation
- **Q1 2026**: Application deployment and GitOps workflows
- **Q2 2026**: Advanced monitoring and observability
- **Q3 2026**: Community features and documentation

---

## 📞 Community & Support

### 💬 Connect With Us

- **💬 Discussions**: [GitHub Discussions](https://github.com/kubland/.github/discussions)
- **🐛 Issues**: [GitHub Issues](https://github.com/kubland/.github/issues)
- **📧 Email**: [contact@kubland.dev](mailto:contact@kubland.dev)
- **🐦 Twitter**: [@KubLandDev](https://twitter.com/KubLandDev)

### 📚 Resources

- **📖 Documentation**: [docs.kubland.dev](https://docs.kubland.dev)
- **🎥 Videos**: [YouTube Channel](https://youtube.com/@kubland)
- **📝 Blog**: [blog.kubland.dev](https://blog.kubland.dev)

---

## 📄 License

This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgments

- **☸️ Kubernetes Community**: For the amazing container orchestration platform
- **🏗️ Rancher Team**: For RKE2 and excellent tooling
- **☁️ Outscale**: For reliable cloud infrastructure
- **🔐 HashiCorp**: For security and infrastructure tools
- **📊 CNCF**: For the cloud-native ecosystem

---

<div align="center">

**🌟 Star this repository if you find it helpful!**

[![GitHub stars](https://img.shields.io/github/stars/kubland/homelab-main?style=social)](https://github.com/kubland/homelab-main)
[![GitHub forks](https://img.shields.io/github/forks/kubland/homelab-main?style=social)](https://github.com/kubland/homelab-main)
[![GitHub watchers](https://img.shields.io/github/watchers/kubland/homelab-main?style=social)](https://github.com/kubland/homelab-main)

---

*Made with ❤️ by the KubLand Community*

</div>
