---

# 🌟 Ultimate Kubernetes Learning Guide - Daywise Journal 🚀

> 🎓 *Learning Date:* **18 APR 2025**  
> 🧑‍💻 *Author:* Trinath Ladi  
> 📍 *Location:* Hyderabad, India

---

## 📚 What I Learned Today

- ✅ Kubernetes Architecture 🧱
- ✅ Pods & ReplicaSets 🧪
- ✅ Namespaces, Labels, Selectors 🏷️
- ✅ Deployments 🚀
- ✅ YAML File Creation & Execution 📜
- ✅ Command Practice in Real Time 👨‍💻

---

## ⚙️ Kubernetes Concepts Cheat Sheet 💡

| 🔧 Component | 📄 Description |
|-------------|----------------|
| **Pod** | Smallest deployable unit, encapsulates one or more containers |
| **ReplicaSet** | Ensures a specified number of pod replicas are running |
| **Deployment** | Manages updates to ReplicaSets and allows version control |
| **Namespace** | Logical separation in cluster for managing resources |
| **Label** | Key-value pair attached to K8s objects for filtering & organization |
| **Selector** | Allows controllers to identify objects using label filters |
| **YAML** | Declarative file format for defining K8s resources |

---

## 🧰 Key Commands Practiced

```bash
# Create Cluster
eksctl create cluster --name sumancluster --nodegroup-name 15ng --node-type t3.micro --nodes 4 --managed

# Node Info
kubectl get nodes -o wide

# Pod Creation
kubectl run pod1 --image=tomcat

# Apply YAMLs
kubectl apply -f replicaset2.yaml

# Cleanup Resources
kubectl delete all --all

# Label Filtering & Explanation
kubectl explain pods
kubectl explain pods.spec
kubectl api-resources | grep Deployment

# Node Maintenance
kubectl cordon <node-name>
kubectl uncordon <node-name>
kubectl drain <node-name>

# ReplicaSet Scaling & Description
kubectl scale rs fb-rs --replicas=2
kubectl describe rs replicaset.apps/fb-rs

# Deployment Management
kubectl apply -f 1-deployment-AC-V1.yaml
kubectl apply -f 2-deployment-VC-V2.yaml
kubectl describe deploy fb-deploye
kubectl rollout undo deploy fb-deploye
kubectl rollout history deploy fb-deploye
```

---

## 🧠 Tips & Observations

- Use `kubectl explain` to dive deeper into any K8s object structure 🔍
- `rollout undo` is super helpful to rollback updates 🕐
- Ensure proper indentation in YAML (spaces over tabs) 🧾
- Use `--watch` to monitor resources in real-time 👀

---

## 🗺️ Kubernetes Architecture (Simplified)

```
┌───────────────┐        ┌─────────────┐
│   Master Node │◄──────►│  Worker Node│
└──────┬────────┘        └────┬────────┘
       │                      │
       ▼                      ▼
  📌 API Server            📦 Kubelet
  📌 etcd (DB)             📦 Kube Proxy
  📌 Controller Manager    📦 Pods (Containers)
  📌 Scheduler
```

---

## 🔥 YAML Sample Reference

**replicaset2.yaml**
```yaml
apiVersion: apps/v1
kind: ReplicaSet
metadata:
  name: fb-rs
spec:
  replicas: 2
  selector:
    matchLabels:
      app: fb
  template:
    metadata:
      labels:
        app: fb
    spec:
      containers:
      - name: fb
        image: nginx
```

---

## 🌐 Stay Connected

📩 Email: [ladi.trinath@gmail.com](mailto:ladi.trinath@gmail.com)  
🔗 LinkedIn: [linkedin.com/in/trinath-l-2a5720113](https://www.linkedin.com/in/trinath-l-2a5720113)  
📁 GitHub: [github.com/laditrinath321](https://github.com/laditrinath321)

---

> 💬 "Master the basics, automate the rest – Kubernetes is not just a tool, it's a mindset!" ⚡

---

