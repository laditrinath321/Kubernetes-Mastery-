# 🌟 Kubernetes Advanced Concepts (18 APR 2025)

Welcome to today's hands-on Kubernetes learning notes! This README is a walkthrough of **Resources**, **ENV vs ConfigMap vs Secret**, **Annotations vs Labels**, and more — made ✨interactive✨ and beginner-friendly.

---

## 🔧 Resource Requests & Limits

### 💡 What are Resource Requests?
> Requests define the minimum CPU/Memory a container needs. Kubernetes ensures the pod gets at least this much resource.

### 🚧 What are Resource Limits?
> Limits define the max CPU/Memory a container can use. If it crosses, it may get **throttled** (CPU) or **killed** (Memory).

### ✅ Real-World Use Case:
Imagine you're running a customer-facing website. One microservice suddenly gets high traffic and hogs all CPU. This slows down other services! Requests & Limits **prevent resource hogging** by isolating and capping usage.

### 🧪 YAML Example
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: example-pod
spec:
  containers:
  - name: example-container
    image: nginx
    resources:
      requests:
        cpu: "500m"
        memory: "128Mi"
      limits:
        cpu: "1"
        memory: "256Mi"
```

---

## 📦 ENV vs CONFIGMAP vs SECRET

| Feature        | ENV Var           | ConfigMap           | Secret                 |
|----------------|-------------------|----------------------|-------------------------|
| 🔐 Sensitivity | Not Sensitive     | Not Sensitive        | Sensitive (base64)      |
| 📦 Storage     | In Pod Spec       | Separate Object      | Separate Object         |
| 🔁 Reusability | Limited           | Reusable Across Pods | Reusable & Secure       |
| 🔍 Visibility  | Visible in Pod    | Visible in Pod       | Hidden (Encoded)        |
| 🧑‍💻 Use Cases | Feature Flags     | App Configs          | Passwords, API Keys     |

### 📜 ENV Example
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: environment
spec:
  containers:
  - name: nginx
    image: nginx
    env:
      - name: course
        value: aws devops
      - name: trainer
        value: "Madhu kiran Gorekar"
      - name: Institute
        value: MindCircuit
```

### ⚙️ ConfigMap Example
```yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: nginx-config
data:
  course: aws devops
  trainer: Madhukirna gorekar
  Institute: Mindcircuit
```

#### Pod using ConfigMap:
```yaml
kind: Pod
apiVersion: v1
metadata:
  name: pod-config
spec:
  containers:
  - name: nginx
    image: nginx
    envFrom:
    - configMapRef:
        name: nginx-config
```

### 🔐 Secret Example
#### base64 Encoded:
```bash
echo -n "Aws DevOps" | base64 # => QXdzIERldk9wcw==
echo -n "Madhukiran Gorekar" | base64 # => TWFkaHVraXJhbiBHb3Jla2Fy
```

#### Secret YAML:
```yaml
apiVersion: v1
kind: Secret
metadata:
  name: pod-secret
type: Opaque
data:
  course: QXdzIERldk9wcw==
  trainer: TWFkaHVraXJhbiBHb3Jla2Fy
```

#### Pod using Secret:
```yaml
kind: Pod
apiVersion: v1
metadata:
  name: pod-secret
spec:
  containers:
  - name: nginx
    image: nginx
    envFrom:
    - secretRef:
        name: pod-secret
```

---

## 🏷️ Labels vs 📝 Annotations

| Feature        | Labels                     | Annotations                    |
|----------------|-----------------------------|--------------------------------|
| 🔍 Used for    | Grouping & Selecting Pods  | Attaching metadata             |
| 🧩 Format      | Key-Value                  | Key-Value                      |
| 🔄 Editable    | Yes                        | Yes                            |
| 🧠 Example     | env: prod, app: frontend   | prometheus.io/scrape: "true"   |

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: fbpod
  labels:
    app: facebook
    env: lab
  annotations:
    imageregistry: "https://hub.docker.com/"
    build-url: "https://jenkins.example.com/build/142"
    prometheus.io/scrape: "true"
    prometheus.io/port: "8080"
spec:
  containers:
  - name: nginx
    image: nginx
```

---

## 🧠 Quick Commands Cheatsheet

```bash
# 🐚 Access Pod shell
kubectl exec -it <podname> -- /bin/bash

# 🔍 View env variables
kubectl exec -it <podname> -- env

# 🕵️ Get secrets
kubectl get secrets

# 🔍 Explain a resource
kubectl explain pods
kubectl explain pods.spec
```

---

## 🚀 Real World Problem Solvers:

### ✅ Problem: A container hogs all the CPU in shared cluster
➡️ **Solved By**: Resource Limits & Requests

### ✅ Problem: Passwords visible in Pod YAML
➡️ **Solved By**: Secrets (base64 encoded)

### ✅ Problem: Repeating config in multiple Pods
➡️ **Solved By**: ConfigMaps and envFrom usage

### ✅ Problem: Need to scrape metrics only from specific pods
➡️ **Solved By**: Labels + Annotations for Prometheus

---

## 🔗 Connect with Me

- GitHub: [@laditrinath321](https://github.com/laditrinath321)
- LinkedIn: [Trinath Ladi](https://www.linkedin.com/in/trinath-l-2a5720113)
- Email: [ladi.trinath@gmail.com](mailto:ladi.trinath@gmail.com)

---

> "Master the config, secure your secrets, control your resources — that's the Kubernetes way!" 🚀

