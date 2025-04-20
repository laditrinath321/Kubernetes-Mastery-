# 🌐✨ Kubernetes Architecture & Setup Guide (17th April 2025)

Welcome to my interactive GitHub showcase on what I learned today — diving into **Kubernetes Architecture** and essential tools like `eksctl`, `kubectl`, and `VS Code`! 🚀🐳💻

---

## 🎯 Today’s Goals
- ✅ Understand the architecture of Kubernetes ⛩️
- ✅ Install & configure `kubectl` and `eksctl` on Windows 🪟
- ✅ Create a working EKS cluster using `eksctl` 🏗️
- ✅ Use basic `kubectl` commands to explore the cluster 🔍

---

## 🧠 Quick Reference: Kubernetes Core Components

| Component       | Role                                                                 |
|----------------|----------------------------------------------------------------------|
| 📦 **Pod**       | Smallest deployable unit; contains one or more containers           |
| 🎯 **Service**   | Stable IP and DNS entry to access pods                              |
| 🧠 **Master Node** | Controls and manages the cluster; runs the control plane            |
| ⚙️ **Worker Node** | Hosts application workloads                                         |
| 🧭 **Kube-API Server** | Frontend for the control plane                               |
| 📊 **etcd**      | Key-value store for cluster state                                   |
| ⛓️ **Controller Manager** | Ensures desired state of resources                 |
| 🛰️ **Scheduler** | Assigns workloads to nodes                                          |
| 🎛️ **Kubelet**   | Agent running on each node, talks to control plane                 |
| 🔄 **Kube-proxy** | Manages networking & load balancing between pods                    |

---

## 🛠️ Tool Installations on Windows

### 📥 1. Install `kubectl`
```powershell
choco install kubernetes-cli
```
✅ Or manually: [https://kubernetes.io/docs/tasks/tools/](https://kubernetes.io/docs/tasks/tools/)

### 📥 2. Install `eksctl`
```powershell
choco install eksctl
```
✅ Or manually: [https://eksctl.io/introduction/#installation](https://eksctl.io/introduction/#installation)

### 🖥️ 3. Install Visual Studio Code (VS Code)
```powershell
choco install vscode
```
✅ Or visit [https://code.visualstudio.com/](https://code.visualstudio.com/)

---

## ☸️ Create EKS Cluster
```bash
eksctl create cluster \
  --name trinathcluster \
  --nodegroup-name trinath \
  --node-type t3.micro \
  --nodes 4 \
  --managed
```
🔐 Make sure AWS credentials are configured using `aws configure` before this.

---

## 📋 Common `kubectl` Commands
```bash
kubectl get nodes
kubectl get pods --all-namespaces
kubectl get services
kubectl describe node <node-name>
kubectl apply -f app.yaml
```

---

## 📊 Visual Diagram - Kubernetes Architecture
```text
                   +----------------------+
                   |      kubectl CLI     |
                   +----------+-----------+
                              |
                              v
        +------------------ [Kube-API Server] ------------------+
        |                    (Control Plane)                   |
        |                                                       |
        |     +----------------+      +------------------+      |
        |     | Scheduler      | <--> | Controller Mgr   |      |
        |     +----------------+      +------------------+      |
        |                                                       |
        |                +----------------+                     |
        |                |     etcd       |                     |
        |                +----------------+                     |
        +-------------------------------------------------------+
                              |
              +---------------+---------------+
              |                               |
              v                               v
      +---------------+               +---------------+
      |   Node 1      |               |   Node 2      |
      |  +--------+   |               |  +--------+   |
      |  | Kubelet|   |               |  | Kubelet|   |
      |  +--------+   |               |  +--------+   |
      |  | Pods   |   |               |  | Pods   |   |
      |  +--------+   |               |  +--------+   |
      |  | K-proxy|   |               |  | K-proxy|   |
      +---------------+               +---------------+
```

---

## 📚 What I Learned Today
- 🔍 Clear understanding of Kubernetes architecture
- 🧱 How `eksctl` simplifies creating an EKS cluster
- 📡 How `kubectl` interacts with the cluster
- ⚙️ Basic resource inspection using commands
- 🧰 Setup developer tools for a better K8s experience

---

## 📬 Let's Connect
- 💻 GitHub: [@laditrinath321](https://github.com/laditrinath321)
- 🔗 LinkedIn: [Trinath Ladi](https://www.linkedin.com/in/trinath-l-2a5720113)
- 📧 Email: [ladi.trinath@gmail.com](mailto:ladi.trinath@gmail.com)

> 🌟 *“Keep calm and kube on!”* ☸️✨

