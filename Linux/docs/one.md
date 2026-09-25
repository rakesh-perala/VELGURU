1 What Is Linux?
Linux is an open-source operating system kernel.

In everyday conversation, people commonly use the term "Linux" to refer to a complete operating system distribution built around the Linux kernel.

Examples:

Ubuntu
Debian
Red Hat Enterprise Linux
Rocky Linux
AlmaLinux
Amazon Linux
SUSE Linux Enterprise
Linux is heavily used in enterprise infrastructure because it provides:

Stability
Automation capabilities
Strong networking support
Security controls
Process management
Flexible configuration
Excellent command-line tooling
Strong cloud support

# 4. Linux Command Categories

| Category             | Main Commands                        |
| -------------------- | ------------------------------------ |
| Directory creation   | `mkdir`, `mkdir -p`                  |
| Directory navigation | `pwd`, `cd`, `ls`                    |
| Move and rename      | `mv`                                 |
| Copy                 | `cp`, `cp -r`, `cp -a`               |
| Permissions          | `chmod`, `umask`, `stat`             |
| Users                | `useradd`, `adduser`, `passwd`, `id` |
| Groups               | `groupadd`, `usermod`, `gpasswd`     |
| Ownership            | `chown`, `chgrp`                     |
| File content         | `cat`, `less`, `head`, `tail`, `nl`  |
| Filtering            | `grep`, `cut`, `sort`, `uniq`, `awk` |
| Search               | `find`, `locate`, `grep -r`          |
| Tar archives         | `tar`                                |
| Zip archives         | `zip`, `unzip`                       |
| Validation           | `ls -l`, `stat`, `file`, `du`, `id`  |

---

# 2. Linux Introduction

## 2.1 What is Linux?

Linux is an open-source operating system kernel.

A Linux distribution combines:

```text
Linux Kernel
     +
System Utilities
     +
Package Manager
     +
Libraries
     +
Applications
```

Examples:

* Ubuntu
* Debian
* Red Hat Enterprise Linux
* Rocky Linux
* AlmaLinux
* Amazon Linux

---
# Kubernetes Zero to Hero

## Complete Beginner → Practical → Enterprise Training Guide

> **Trainer Edition**
>
> This README is designed for a DevOps trainer who is teaching Kubernetes to students/juniors who are completely new to Kubernetes.
>
> Teaching philosophy:
>
> ```text
> Understand
>     ↓
> Why?
>     ↓
> Real-Time Problem
>     ↓
> Kubernetes Solution
>     ↓
> Object
>     ↓
> YAML
>     ↓
> Hands-On
>     ↓
> Break It
>     ↓
> Troubleshoot
>     ↓
> Enterprise Usage
>     ↓
> Interview
> ```

---

# Table of Contents

1. [How to Teach Kubernetes](#1-how-to-teach-kubernetes)
2. [What is Kubernetes?](#2-what-is-kubernetes)
3. [Why Kubernetes?](#3-why-kubernetes)
4. [Kubernetes Architecture](#4-kubernetes-architecture)
5. [Kubernetes Cluster Components](#5-kubernetes-cluster-components)
6. [Lab Environment](#6-lab-environment)
7. [Introduction Lab 1 - Minikube](#7-introduction-lab-1---minikube)
8. [Introduction Lab 2 - AWS EKS](#8-introduction-lab-2---aws-eks)
9. [Kubernetes Object Learning Strategy](#9-kubernetes-object-learning-strategy)
10. [Pod](#10-pod)
11. [ReplicaSet](#11-replicaset)
12. [Deployment](#12-deployment)
13. [Service](#13-service)
14. [Namespace](#14-namespace)
15. [ConfigMap](#15-configmap)
16. [Secret](#16-secret)
17. [DaemonSet](#17-daemonset)
18. [StatefulSet](#18-statefulset)
19. [Job](#19-job)
20. [CronJob](#20-cronjob)
21. [Ingress](#21-ingress)
22. [Storage](#22-storage)
23. [Health Probes](#23-health-probes)
24. [Resource Requests and Limits](#24-resource-requests-and-limits)
25. [HPA](#25-hpa)
26. [RBAC](#26-rbac)
27. [NetworkPolicy](#27-networkpolicy)
28. [Kubernetes Networking](#28-kubernetes-networking)
29. [Helm](#29-helm)
30. [GitOps](#30-gitops)
31. [Monitoring](#31-monitoring)
32. [Logging](#32-logging)
33. [Enterprise Kubernetes Architecture](#33-enterprise-kubernetes-architecture)
34. [Troubleshooting Framework](#34-troubleshooting-framework)
35. [Trainer Method](#35-trainer-method)
36. [Final Enterprise Project](#36-final-enterprise-project)
37. [Kubernetes Interview Preparation](#37-kubernetes-interview-preparation)

---

# 1. How to Teach Kubernetes

## Do NOT start like this

```text
Here is a Deployment YAML.

Memorize it.

Next topic.
```

This creates students who can write YAML but don't understand Kubernetes.

Instead teach:

```text
Real-Time Problem
       ↓
Why is this problem happening?
       ↓
How does Kubernetes solve it?
       ↓
Which Kubernetes object solves it?
       ↓
How does that object work?
       ↓
YAML
       ↓
Command
       ↓
Hands-On
       ↓
Troubleshooting
```

---

# 2. What is Kubernetes?

## Simple Definition

Kubernetes is a **container orchestration platform**.

It helps us:

* Deploy containerized applications
* Manage containers
* Scale applications
* Restart failed workloads
* Provide networking
* Perform rolling updates
* Roll back releases
* Manage configuration
* Manage storage
* Control access
* Run applications reliably

## Trainer Explanation

Tell students:

> Docker can run containers. Kubernetes manages containerized applications across machines.

---

# 3. Why Kubernetes?

Imagine a company has:

```text
100 Applications
500 Containers
20 Servers
```

Managing everything manually becomes difficult.

Problems:

```text
Container crashes
Server crashes
Traffic increases
Application needs scaling
New version needs deployment
Old version needs rollback
Application needs networking
Application needs configuration
Application needs storage
```

Kubernetes provides mechanisms for these problems.

---

# 4. Kubernetes Architecture

```text
                     Kubernetes Cluster
                            |
              +-------------+-------------+
              |                           |
        Control Plane                Worker Nodes
              |                           |
       +------+-------+             +-----+-----+
       |      |       |             |           |
    API     etcd  Scheduler      Worker 1    Worker 2
    Server         Controller        |           |
                     Manager         Pod         Pod
                                      |           |
                                  Container   Container
```

---

# 5. Kubernetes Cluster Components

## Control Plane

Important components:

```text
API Server
etcd
Scheduler
Controller Manager
Cloud Controller Manager
```

### Trainer Explanation

> The Control Plane is responsible for managing the Kubernetes cluster.

---

## Worker Node

Important components:

```text
kubelet
kube-proxy
Container Runtime
```

Applications run inside Pods on worker nodes.

---

# 6. Lab Environment

For beginner training:

```text
kubectl
Minikube
Docker
Linux / WSL2
```

For AWS:

```text
AWS CLI
kubectl
eksctl
EKS
```

Recommended working directory:

```bash
mkdir -p ~/k8s/lab
cd ~/k8s/lab
```

---

# 7. Introduction Lab 1 - Minikube

## Objective

Deploy a real application locally.

Application:

```text
Hotstar
```

Docker image:

```text
dockerperala/hotstar
```

Application port:

```text
8080
```

Application context:

```text
/hotstar/
```

---

## Architecture

```text
Laptop
   |
   ↓
WSL2
   |
   ↓
Minikube
   |
   ↓
Kubernetes
   |
   ↓
Deployment
   |
   ↓
ReplicaSet
   |
   +---------+
   ↓         ↓
 Pod 1     Pod 2
   ↓         ↓
Hotstar   Hotstar
   |
Tomcat :8080
```

---

## Start Minikube

```bash
minikube start --driver=docker
```

Verify:

```bash
minikube status
```

Verify Kubernetes:

```bash
kubectl get nodes
```

---

# Deployment YAML

```yaml
apiVersion: apps/v1
kind: Deployment

metadata:
  name: hotstar-deployment

spec:
  replicas: 2

  selector:
    matchLabels:
      app: hotstar

  template:
    metadata:
      labels:
        app: hotstar

    spec:
      containers:
        - name: hotstar-container
          image: dockerperala/hotstar
          ports:
            - containerPort: 8080
```

Apply:

```bash
kubectl apply -f deployment.yaml
```

Verify:

```bash
kubectl get deployment
kubectl get replicaset
kubectl get pods
```

---

# Service YAML

```yaml
apiVersion: v1
kind: Service

metadata:
  name: hotstar-service

spec:
  type: NodePort

  selector:
    app: hotstar

  ports:
    - port: 8080
      targetPort: 8080
      nodePort: 30080
```

Apply:

```bash
kubectl apply -f service.yaml
```

Verify:

```bash
kubectl get service
```

---

## Port Forward

```bash
kubectl port-forward service/hotstar-service 8080:8080
```

Open:

```text
http://localhost:8080/hotstar/
```

Test:

```bash
curl -I http://127.0.0.1:8080/hotstar/
```

Expected:

```text
HTTP/1.1 200
```

---

# 8. Introduction Lab 2 - AWS EKS

## Objective

Run the same application on AWS EKS.

Local:

```text
Laptop
 ↓
Minikube
 ↓
Kubernetes
```

AWS:

```text
AWS
 ↓
EKS
 ↓
Worker Nodes
 ↓
Pods
```

---

## Configure AWS

```bash
aws configure
```

Verify:

```bash
aws sts get-caller-identity
```

Set region:

```bash
export AWS_REGION=ap-south-1
```

---

## Create EKS Cluster

```bash
eksctl create cluster \
  --name hotstar-eks \
  --region ap-south-1 \
  --nodes 2 \
  --node-type t3.medium
```

Connect kubectl:

```bash
aws eks update-kubeconfig \
  --region ap-south-1 \
  --name hotstar-eks
```

Verify:

```bash
kubectl get nodes
```

---

## EKS Service

```yaml
apiVersion: v1
kind: Service

metadata:
  name: hotstar-service

spec:
  type: LoadBalancer

  selector:
    app: hotstar

  ports:
    - port: 80
      targetPort: 8080
```

Apply:

```bash
kubectl apply -f service.yaml
```

Verify:

```bash
kubectl get service hotstar-service
```

Retrieve the external hostname:

```bash
kubectl get service hotstar-service \
  -o jsonpath='{.status.loadBalancer.ingress[0].hostname}'
```

Test:

```bash
curl -I http://<LOAD_BALANCER_HOSTNAME>/hotstar/
```

---

# 9. Kubernetes Object Learning Strategy

After the introduction labs, teach Kubernetes objects individually.

Recommended sequence:

```text
Pod
 ↓
ReplicaSet
 ↓
Deployment
 ↓
Service
 ↓
Namespace
 ↓
ConfigMap
 ↓
Secret
 ↓
DaemonSet
 ↓
StatefulSet
 ↓
Job
 ↓
CronJob
 ↓
Ingress
 ↓
Storage
 ↓
Probes
 ↓
Resources
 ↓
HPA
 ↓
RBAC
 ↓
NetworkPolicy
 ↓
Helm
 ↓
GitOps
 ↓
Monitoring
 ↓
Logging
```

---

# 10. Pod

## What is a Pod?

A Pod is the smallest deployable unit in Kubernetes.

Basic architecture:

```text
Pod
 |
 +-- Container
       |
       +-- Application
```

## Real-Time Example

Imagine a Java application:

```text
Java Application
       ↓
Docker Container
       ↓
Pod
```

---

# Pod Lab 1 — Create Pod

```bash
kubectl run nginx --image=nginx
```

Verify:

```bash
kubectl get pods
```

---

# Pod Lab 2 — Describe Pod

```bash
kubectl describe pod nginx
```

Teach students to inspect:

```text
Status
Image
Container
Node
IP
Events
Conditions
```

---

# Pod Lab 3 — Logs

```bash
kubectl logs nginx
```

Explain:

> Logs help us understand what the application is doing.

---

# Pod Lab 4 — Execute Inside Pod

```bash
kubectl exec -it nginx -- /bin/bash
```

Inside:

```bash
hostname
ls
pwd
```

Exit:

```bash
exit
```

---

# Pod Lab 5 — Delete Pod

```bash
kubectl delete pod nginx
```

Then:

```bash
kubectl get pods
```

Trainer question:

> What happens when we delete a Pod created directly using `kubectl run`?

Explain:

> A standalone Pod is not automatically recreated by a Deployment or ReplicaSet.

This creates the reason for the next object.

---

# Pod Important Commands

```bash
kubectl get pods
kubectl get pods -o wide
kubectl describe pod <pod>
kubectl logs <pod>
kubectl exec -it <pod> -- /bin/bash
kubectl delete pod <pod>
kubectl get events
```

---

# Pod Interview Questions

### Q1. What is a Pod?

Smallest deployable unit in Kubernetes.

### Q2. Can a Pod contain multiple containers?

Yes.

### Q3. Can containers in the same Pod communicate?

Yes, they share the Pod network namespace and can communicate through localhost.

### Q4. Is Pod IP permanent?

No.

### Q5. Should we normally create production Pods directly?

Usually no. Higher-level controllers such as Deployments are generally used.

---

# 11. ReplicaSet

## Problem

Pod can disappear.

```text
Pod ❌
```

We want:

```text
3 Pods
```

ReplicaSet maintains the desired number of Pods.

```text
ReplicaSet
   |
   +--- Pod
   +--- Pod
   +--- Pod
```

---

# ReplicaSet Lab 1 — Create ReplicaSet

```yaml
apiVersion: apps/v1
kind: ReplicaSet

metadata:
  name: nginx-rs

spec:
  replicas: 3

  selector:
    matchLabels:
      app: nginx

  template:
    metadata:
      labels:
        app: nginx

    spec:
      containers:
        - name: nginx
          image: nginx
```

Apply:

```bash
kubectl apply -f replicaset.yaml
```

---

# ReplicaSet Lab 2 — Verify

```bash
kubectl get rs
kubectl get pods
```

---

# ReplicaSet Lab 3 — Delete Pod

```bash
kubectl delete pod <pod-name>
```

Then:

```bash
kubectl get pods
```

Observe that ReplicaSet creates a replacement.

---

# ReplicaSet Lab 4 — Scale

```bash
kubectl scale rs nginx-rs --replicas=5
```

Verify:

```bash
kubectl get pods
```

---

# ReplicaSet Lab 5 — Scale Down

```bash
kubectl scale rs nginx-rs --replicas=2
```

Verify:

```bash
kubectl get pods
```

---

# Important Relationship

```text
ReplicaSet
     ↓
Maintains
     ↓
Desired number of Pods
```

---

# 12. Deployment

## Problem

ReplicaSet maintains Pods.

But application deployments require:

```text
Rolling Update
Rollback
Version Management
Declarative Updates
```

Deployment solves this.

```text
Deployment
     ↓
ReplicaSet
     ↓
Pods
```

---

# Deployment Lab 1 — Create Deployment

```yaml
apiVersion: apps/v1
kind: Deployment

metadata:
  name: nginx-deployment

spec:
  replicas: 3

  selector:
    matchLabels:
      app: nginx

  template:
    metadata:
      labels:
        app: nginx

    spec:
      containers:
        - name: nginx
          image: nginx:1.27
```

Apply:

```bash
kubectl apply -f deployment.yaml
```

---

# Deployment Lab 2 — Scale

```bash
kubectl scale deployment nginx-deployment --replicas=5
```

Verify:

```bash
kubectl get pods
```

---

# Deployment Lab 3 — Rolling Update

```bash
kubectl set image deployment/nginx-deployment \
  nginx=nginx:1.28
```

Check:

```bash
kubectl rollout status deployment/nginx-deployment
```

---

# Deployment Lab 4 — Rollout History

```bash
kubectl rollout history deployment/nginx-deployment
```

---

# Deployment Lab 5 — Rollback

```bash
kubectl rollout undo deployment/nginx-deployment
```

Verify:

```bash
kubectl rollout status deployment/nginx-deployment
```

---

# Deployment Interview Question

> Why Deployment instead of directly creating ReplicaSet?

Because Deployment provides higher-level application lifecycle management such as rolling updates and rollback.

---

# 13. Service

## Problem

Pod IPs are temporary.

```text
Pod
10.244.0.10
```

Pod recreated:

```text
10.244.0.20
```

Users cannot depend on Pod IPs.

Service provides stable access.

```text
Client
  |
  ↓
Service
  |
  +--- Pod
  +--- Pod
  +--- Pod
```

---

# Service Lab 1 — ClusterIP

```yaml
apiVersion: v1
kind: Service

metadata:
  name: nginx-service

spec:
  selector:
    app: nginx

  ports:
    - port: 80
      targetPort: 80
```

Apply:

```bash
kubectl apply -f service.yaml
```

Verify:

```bash
kubectl get svc
```

---

# Service Lab 2 — Test ClusterIP

```bash
kubectl run test-pod \
  --image=curlimages/curl \
  -it --rm -- sh
```

Inside:

```bash
curl http://nginx-service
```

---

# Service Lab 3 — NodePort

```yaml
type: NodePort
```

Example:

```yaml
ports:
  - port: 80
    targetPort: 80
    nodePort: 30080
```

---

# Service Lab 4 — LoadBalancer

```yaml
spec:
  type: LoadBalancer
```

Commonly used with cloud providers.

---

# Service Lab 5 — Selector Troubleshooting

Check:

```bash
kubectl get svc
kubectl get endpoints
kubectl get endpointslice
```

If endpoints are empty:

```text
Service selector
        ↓
does not match
        ↓
Pod labels
```

Fix the labels/selector.

---

# Service Types

```text
ClusterIP
NodePort
LoadBalancer
ExternalName
```

---

# 14. Namespace

Namespaces provide logical separation.

Example:

```text
dev
test
staging
prod
monitoring
```

---

# Namespace Lab 1

```bash
kubectl create namespace dev
```

---

# Namespace Lab 2

```bash
kubectl get namespaces
```

---

# Namespace Lab 3

```bash
kubectl run nginx \
  --image=nginx \
  -n dev
```

---

# Namespace Lab 4

```bash
kubectl get pods -n dev
```

---

# Namespace Lab 5

```bash
kubectl delete namespace dev
```

---

# 15. ConfigMap

## Problem

Application configuration should not always be hard-coded into the container image.

Example:

```text
APP_ENV=dev
LOG_LEVEL=INFO
DATABASE_HOST=db.example.com
```

ConfigMap stores non-sensitive configuration.

---

# ConfigMap Lab 1

```bash
kubectl create configmap app-config \
  --from-literal=APP_ENV=dev
```

---

# ConfigMap Lab 2

```bash
kubectl get configmap
```

---

# ConfigMap Lab 3 — Environment Variable

```yaml
env:
  - name: APP_ENV
    valueFrom:
      configMapKeyRef:
        name: app-config
        key: APP_ENV
```

---

# ConfigMap Lab 4 — Multiple Values

```bash
kubectl create configmap app-config \
  --from-literal=APP_ENV=dev \
  --from-literal=LOG_LEVEL=INFO
```

---

# ConfigMap Lab 5 — Troubleshooting

```bash
kubectl describe configmap app-config
```

Verify environment inside the Pod.

---

# 16. Secret

Secrets are designed for sensitive configuration.

Examples:

```text
Database password
API token
Username
Credentials
```

Important:

> Base64 encoding is not the same as encryption.

---

# Secret Lab 1

```bash
kubectl create secret generic db-secret \
  --from-literal=username=admin \
  --from-literal=password=change-me
```

---

# Secret Lab 2

```bash
kubectl get secrets
```

---

# Secret Lab 3

Use Secret as environment variable.

```yaml
env:
  - name: DB_PASSWORD
    valueFrom:
      secretKeyRef:
        name: db-secret
        key: password
```

---

# Secret Lab 4

Use Secret as volume.

---

# Secret Lab 5

Troubleshoot:

```bash
kubectl describe secret db-secret
```

Enterprise discussion:

```text
AWS Secrets Manager
External Secrets Operator
HashiCorp Vault
```

---

# 17. DaemonSet

## Problem

We need one Pod on every node.

Examples:

```text
Logging Agent
Monitoring Agent
Security Agent
```

Architecture:

```text
Node 1 → Agent
Node 2 → Agent
Node 3 → Agent
```

---

# DaemonSet Lab 1

```yaml
apiVersion: apps/v1
kind: DaemonSet

metadata:
  name: node-agent

spec:
  selector:
    matchLabels:
      app: node-agent

  template:
    metadata:
      labels:
        app: node-agent

    spec:
      containers:
        - name: agent
          image: nginx
```

---

# DaemonSet Lab 2

```bash
kubectl get daemonset
```

---

# DaemonSet Lab 3

```bash
kubectl get pods -o wide
```

Observe one Pod per eligible node.

---

# DaemonSet Lab 4

Add another worker node and observe scheduling behavior.

---

# DaemonSet Lab 5

Troubleshoot:

```bash
kubectl describe daemonset node-agent
kubectl get events
```

---

# 18. StatefulSet

Used for stateful applications requiring stable identity and storage patterns.

Examples:

```text
PostgreSQL
MySQL
Kafka
Redis
```

Example Pod identities:

```text
postgres-0
postgres-1
postgres-2
```

---

# StatefulSet Lab 1

Create a basic StatefulSet.

---

# StatefulSet Lab 2

Observe ordered Pod creation.

```bash
kubectl get pods -w
```

---

# StatefulSet Lab 3

Delete a Pod.

```bash
kubectl delete pod postgres-0
```

Observe its stable identity.

---

# StatefulSet Lab 4

Add PersistentVolumeClaim templates.

---

# StatefulSet Lab 5

Scale:

```bash
kubectl scale statefulset postgres --replicas=3
```

---

# 19. Job

A Job runs a task until completion.

Examples:

```text
Database migration
Batch processing
Data processing
```

Architecture:

```text
Job
 ↓
Pod
 ↓
Task
 ↓
Completed
```

---

# Job Lab 1

```yaml
apiVersion: batch/v1
kind: Job

metadata:
  name: hello-job

spec:
  template:
    spec:
      restartPolicy: Never
      containers:
        - name: hello
          image: busybox
          command:
            - sh
            - -c
            - echo "Hello Kubernetes"
```

---

# Job Lab 2

```bash
kubectl get jobs
```

---

# Job Lab 3

```bash
kubectl get pods
kubectl logs <pod>
```

---

# Job Lab 4

Configure retries using:

```yaml
backoffLimit: 3
```

---

# Job Lab 5

Delete:

```bash
kubectl delete job hello-job
```

---

# 20. CronJob

CronJob creates Jobs according to a schedule.

Example:

```text
Every day at 2 AM
```

Architecture:

```text
CronJob
   ↓
Job
   ↓
Pod
```

---

# CronJob Lab 1

```yaml
apiVersion: batch/v1
kind: CronJob

metadata:
  name: hello-cronjob

spec:
  schedule: "*/5 * * * *"

  jobTemplate:
    spec:
      template:
        spec:
          restartPolicy: Never
          containers:
            - name: hello
              image: busybox
              command:
                - sh
                - -c
                - date
```

---

# CronJob Lab 2

```bash
kubectl get cronjobs
```

---

# CronJob Lab 3

```bash
kubectl get jobs
```

---

# CronJob Lab 4

```bash
kubectl get pods
```

---

# CronJob Lab 5

Troubleshoot:

```bash
kubectl describe cronjob hello-cronjob
kubectl get events
```

---

# 21. Ingress

Ingress manages HTTP/HTTPS routing into Services.

Example:

```text
shop.example.com
       |
       ↓
    Ingress
    /     \
   ↓       ↓
User     Product
Service  Service
```

---

# Ingress Lab 1

Create an Ingress resource.

---

# Ingress Lab 2

Route:

```text
shop.example.com/users
```

to User Service.

---

# Ingress Lab 3

Route:

```text
shop.example.com/products
```

to Product Service.

---

# Ingress Lab 4

Configure TLS.

---

# Ingress Lab 5

Troubleshoot:

```bash
kubectl get ingress
kubectl describe ingress <name>
```

Enterprise EKS:

```text
Ingress
   ↓
AWS Load Balancer Controller
   ↓
ALB
```

---

# 22. Storage

Applications such as databases need persistent storage.

Basic concepts:

```text
Pod
 ↓
PVC
 ↓
PV
 ↓
Storage
```

Important objects:

```text
Volume
PersistentVolume
PersistentVolumeClaim
StorageClass
```

---

# Storage Lab 1 — EmptyDir

Understand temporary Pod storage.

---

# Storage Lab 2 — PersistentVolume

Create a PV.

---

# Storage Lab 3 — PersistentVolumeClaim

Create a PVC.

---

# Storage Lab 4 — Mount PVC

Mount PVC into a Pod.

---

# Storage Lab 5 — StorageClass

Understand dynamic provisioning.

Enterprise AWS:

```text
PVC
 ↓
StorageClass
 ↓
EBS / EFS
```

---

# 23. Health Probes

Applications need health checks.

Three important probes:

```text
Liveness
Readiness
Startup
```

---

## Liveness

Question:

> Is the application alive?

If not, Kubernetes may restart the container.

---

## Readiness

Question:

> Can this application receive traffic?

If not ready, traffic should not be sent to it.

---

## Startup

Question:

> Has the slow-starting application finished starting?

---

# Probe Lab 1

Create liveness probe.

---

# Probe Lab 2

Create readiness probe.

---

# Probe Lab 3

Create startup probe.

---

# Probe Lab 4

Intentionally configure a failing probe.

---

# Probe Lab 5

Troubleshoot:

```bash
kubectl describe pod <pod>
kubectl get events
```

---

# 24. Resource Requests and Limits

Kubernetes needs to know how much CPU and memory an application needs.

Example:

```yaml
resources:
  requests:
    cpu: "250m"
    memory: "256Mi"

  limits:
    cpu: "500m"
    memory: "512Mi"
```

---

# Resource Lab 1

Configure CPU request.

# Resource Lab 2

Configure memory request.

# Resource Lab 3

Configure CPU limit.

# Resource Lab 4

Configure memory limit.

# Resource Lab 5

Intentionally create an unsuitable memory limit and investigate container behavior.

Useful commands:

```bash
kubectl describe pod <pod>
kubectl top pod
kubectl top node
```

---

# 25. HPA

Horizontal Pod Autoscaler automatically adjusts replica count based on metrics.

Architecture:

```text
Traffic
  ↓
CPU / Memory
  ↓
HPA
  ↓
Pods increase/decrease
```

Example:

```text
Normal
 ↓
2 Pods

High load
 ↓
4 Pods

Very high load
 ↓
5 Pods
```

---

# HPA Lab 1

Install/configure Metrics Server where appropriate.

---

# HPA Lab 2

Create HPA:

```bash
kubectl autoscale deployment nginx \
  --min=2 \
  --max=5 \
  --cpu-percent=70
```

---

# HPA Lab 3

Check:

```bash
kubectl get hpa
```

---

# HPA Lab 4

Generate load.

Observe:

```bash
kubectl get pods -w
```

---

# HPA Lab 5

Troubleshoot metrics:

```bash
kubectl describe hpa
kubectl top pods
```

---

# 26. RBAC

RBAC means:

```text
Role Based Access Control
```

Example:

```text
Developer
   |
   +-- get Pods
   +-- list Pods
   X-- delete Production Deployment
```

Objects:

```text
Role
ClusterRole
RoleBinding
ClusterRoleBinding
ServiceAccount
```

---

# RBAC Lab 1

Create ServiceAccount.

---

# RBAC Lab 2

Create Role.

---

# RBAC Lab 3

Create RoleBinding.

---

# RBAC Lab 4

Test allowed action.

```bash
kubectl auth can-i get pods
```

---

# RBAC Lab 5

Test denied action:

```bash
kubectl auth can-i delete deployments
```

Trainer lesson:

> Always follow least privilege.

---

# 27. NetworkPolicy

NetworkPolicy controls Pod-to-Pod traffic.

Without policy:

```text
Pod A → Pod B
Pod A → Pod C
Pod A → Database
```

With policy:

```text
Pod A → Pod B       ALLOWED
Pod A → Database    ALLOWED
Pod A → Pod C       DENIED
```

---

# NetworkPolicy Lab 1

Create a namespace.

---

# NetworkPolicy Lab 2

Create an allow policy.

---

# NetworkPolicy Lab 3

Create a deny policy.

---

# NetworkPolicy Lab 4

Test Pod-to-Pod connectivity.

---

# NetworkPolicy Lab 5

Troubleshoot selectors and labels.

---

# 28. Kubernetes Networking

Teach networking in this order:

```text
Container networking
      ↓
Pod IP
      ↓
Pod-to-Pod
      ↓
Service
      ↓
ClusterIP
      ↓
NodePort
      ↓
LoadBalancer
      ↓
Ingress
      ↓
DNS
      ↓
NetworkPolicy
```

---

# Important Port Concepts

Example:

```yaml
ports:
  - port: 80
    targetPort: 8080
```

Meaning:

```text
Service :80
     ↓
Pod :8080
```

`containerPort`:

```yaml
containerPort: 8080
```

describes the application container port.

It does not itself create external access.

---

# 29. Helm

Do not teach Helm before students understand Kubernetes YAML.

Learning order:

```text
Kubernetes Objects
       ↓
YAML
       ↓
Repeated YAML
       ↓
Problem
       ↓
Helm
```

Helm concepts:

```text
Chart
Values
Templates
Release
Repository
```

---

# Helm Lab 1

Install Helm.

```bash
helm version
```

---

# Helm Lab 2

Create a chart:

```bash
helm create myapp
```

---

# Helm Lab 3

Install:

```bash
helm install myapp ./myapp
```

---

# Helm Lab 4

Change values:

```bash
helm upgrade myapp ./myapp
```

---

# Helm Lab 5

Rollback:

```bash
helm history myapp
helm rollback myapp <revision>
```

---

# 30. GitOps

GitOps means Git becomes the desired-state source for deployments.

Basic flow:

```text
Developer
   ↓
Git
   ↓
CI
   ↓
Container Image
   ↓
GitOps Repository
   ↓
Argo CD
   ↓
Kubernetes
```

---

# GitOps Lab 1

Create Kubernetes repository.

---

# GitOps Lab 2

Store Helm configuration in Git.

---

# GitOps Lab 3

Install Argo CD.

---

# GitOps Lab 4

Create Argo CD Application.

---

# GitOps Lab 5

Change Git configuration and observe synchronization.

---

# 31. Monitoring

Production Kubernetes needs monitoring.

Typical architecture:

```text
Kubernetes
    |
    +-- Metrics
    |
    ↓
Prometheus
    |
    ↓
Grafana
```

Monitor:

```text
CPU
Memory
Pod count
Node health
API Server
Application metrics
```

---

# Monitoring Lab 1

Install Prometheus.

# Monitoring Lab 2

Install Grafana.

# Monitoring Lab 3

Connect Prometheus to Grafana.

# Monitoring Lab 4

Create dashboard.

# Monitoring Lab 5

Create alert.

---

# 32. Logging

Application logs:

```text
Pod
 ↓
Container stdout/stderr
 ↓
Logging Agent
 ↓
Log Storage
 ↓
Visualization
```

Enterprise examples:

```text
Loki
Grafana
Alloy
Fluent Bit
CloudWatch
```

---

# Logging Lab 1

Inspect Pod logs:

```bash
kubectl logs <pod>
```

---

# Logging Lab 2

Follow logs:

```bash
kubectl logs -f <pod>
```

---

# Logging Lab 3

Multi-container Pod logs:

```bash
kubectl logs <pod> -c <container>
```

---

# Logging Lab 4

Deploy a logging agent.

---

# Logging Lab 5

Centralize and search application logs.

---

# 33. Enterprise Kubernetes Architecture

After students finish the individual objects, show the complete architecture.

```text
                         Internet
                            |
                            ↓
                           ALB
                            |
                            ↓
                         Ingress
                            |
          +-----------------+----------------+
          |                 |                |
          ↓                 ↓                ↓
      User Service     Product Service    Order Service
          |                 |                |
          ↓                 ↓                ↓
        Pods              Pods             Pods
          |                 |                |
          +-----------------+----------------+
                            |
                     Kubernetes Network
                            |
              +-------------+-------------+
              |                           |
              ↓                           ↓
           Database                    Cache
              |                           |
             RDS                         Redis
```

---

# CI/CD Architecture

```text
Developer
    |
    ↓
Git
    |
    ↓
Jenkins
    |
    +-- Maven
    |
    +-- Tests
    |
    +-- SonarQube
    |
    +-- Docker
    |
    ↓
Container Registry
    |
    ↓
Helm
    |
    ↓
GitOps Repository
    |
    ↓
Argo CD
    |
    ↓
EKS
```

---

# Monitoring Architecture

```text
EKS
 |
 +-- Prometheus
 |
 +-- Grafana
 |
 +-- Loki
 |
 +-- Alloy
 |
 +-- Alerts
```

---

# 34. Troubleshooting Framework

This is one of the most important things to teach.

Never tell students:

> "Run random kubectl commands."

Teach a troubleshooting flow.

---

## Application Not Working

Start:

```bash
kubectl get pods
```

---

## Step 1 — Pod Status

```text
Running?
Pending?
CrashLoopBackOff?
ImagePullBackOff?
ErrImagePull?
Completed?
```

---

## Step 2 — Describe

```bash
kubectl describe pod <pod>
```

Look at:

```text
Events
Image
Container
Mounts
Probes
Scheduling
```

---

## Step 3 — Logs

```bash
kubectl logs <pod>
```

For previous crashed container:

```bash
kubectl logs <pod> --previous
```

---

## Step 4 — Service

```bash
kubectl get svc
kubectl describe svc <service>
```

---

## Step 5 — Endpoints

```bash
kubectl get endpoints <service>
```

Modern:

```bash
kubectl get endpointslice
```

If endpoints are empty:

```text
Service selector
        ≠
Pod labels
```

---

## Step 6 — Port

Check:

```text
Service port
Target port
Container port
Application listening port
```

---

## Step 7 — Application

Inside Pod:

```bash
kubectl exec -it <pod> -- sh
```

Test:

```bash
curl localhost:8080
```

---

# 35. Trainer Method

For every Kubernetes topic, use this structure.

```text
1. What?
2. Why?
3. Real-Time Problem
4. Kubernetes Solution
5. Architecture
6. YAML
7. Explain YAML line-by-line
8. Commands
9. Lab 1
10. Lab 2
11. Lab 3
12. Lab 4
13. Lab 5
14. Break It
15. Troubleshoot
16. Enterprise Usage
17. Interview Questions
```

---

# 36. Final Enterprise Project

## Project

Build an enterprise e-commerce platform on Kubernetes.

Example:

```text
ShopSphere
```

Services:

```text
User
Product
Cart
Order
Payment
Notification
```

---

# Application Architecture

```text
                         Internet
                            |
                            ↓
                           ALB
                            |
                            ↓
                         Ingress
                            |
       +--------------------+--------------------+
       |                    |                    |
       ↓                    ↓                    ↓
 User Service         Product Service       Order Service
       |                    |                    |
       ↓                    ↓                    ↓
     Pods                 Pods                 Pods
       |                    |                    |
       ↓                    ↓                    ↓
   PostgreSQL          PostgreSQL           PostgreSQL
```

---

# CI/CD

```text
Developer
   |
   ↓
Git
   |
   ↓
Jenkins
   |
   +-- Maven
   +-- Unit Tests
   +-- SonarQube
   +-- Docker Build
   +-- Trivy
   |
   ↓
ECR
   |
   ↓
Helm
   |
   ↓
GitOps
   |
   ↓
Argo CD
   |
   ↓
EKS
```

---

# Infrastructure

```text
AWS
 |
 +-- VPC
 |
 +-- Public Subnets
 |
 +-- Private Subnets
 |
 +-- EKS
 |
 +-- ALB
 |
 +-- RDS
 |
 +-- ECR
 |
 +-- IAM
 |
 +-- CloudWatch
```

---

# Kubernetes Objects Used

```text
Deployment
ReplicaSet
Pod
Service
Namespace
ConfigMap
Secret
Ingress
StatefulSet
PVC
StorageClass
HPA
Probes
RBAC
NetworkPolicy
```

---

# Enterprise Deployment Flow

```text
Feature Branch
      |
      ↓
Pull Request
      |
      ↓
Code Review
      |
      ↓
CI
      |
      +-- Build
      +-- Test
      +-- SonarQube
      +-- Docker
      +-- Security Scan
      |
      ↓
Container Registry
      |
      ↓
GitOps Repository
      |
      ↓
Argo CD
      |
      ↓
EKS
      |
      ↓
Production
```

---

# 37. Kubernetes Interview Preparation

## Beginner Questions

### 1. What is Kubernetes?

Container orchestration platform.

### 2. What is a Pod?

Smallest deployable unit.

### 3. What is a Deployment?

Manages application Pods and supports controlled rollout/rollback behavior.

### 4. What is a ReplicaSet?

Maintains the desired number of Pod replicas.

### 5. What is a Service?

Provides stable networking access to Pods.

### 6. Why can't users directly depend on Pod IPs?

Pod IPs can change when Pods are recreated.

### 7. What is ConfigMap?

Stores non-sensitive configuration.

### 8. What is Secret?

Stores sensitive configuration data.

### 9. What is DaemonSet?

Runs a Pod on each eligible node according to its scheduling rules.

### 10. What is StatefulSet?

Manages stateful workloads with stable identity and storage patterns.

---

# Intermediate Questions

### 1. Deployment vs ReplicaSet?

Deployment provides higher-level lifecycle management and manages ReplicaSets.

### 2. ClusterIP vs NodePort?

ClusterIP provides internal Service access; NodePort exposes a Service through a node port.

### 3. Readiness vs Liveness?

Readiness determines whether traffic should be sent; liveness determines whether the container should be considered alive and potentially restarted.

### 4. ConfigMap vs Secret?

ConfigMap is for non-sensitive configuration; Secret is intended for sensitive configuration.

### 5. Job vs CronJob?

Job runs a task to completion; CronJob creates Jobs according to a schedule.

---

# Advanced Questions

### 1. How does Kubernetes perform rolling updates?

Deployment creates/manages ReplicaSets and gradually transitions workloads according to the Deployment strategy.

### 2. How does Service find Pods?

Through label selectors.

```text
Service Selector
       ↓
Pod Labels
       ↓
Endpoints / EndpointSlices
```

### 3. What happens when a Pod crashes?

The result depends on what manages the Pod. A Deployment/ReplicaSet will work to restore the desired number of replicas.

### 4. What happens when a node fails?

Kubernetes detects node health changes and workload controllers/schedulers can place replacement Pods on eligible nodes, subject to workload configuration and cluster capacity.

### 5. How does HPA work?

HPA evaluates metrics and adjusts the desired replica count within configured boundaries.

---

# Trainer Quick Reference

## Most Important Commands

```bash
kubectl get pods

kubectl get pods -o wide

kubectl get all

kubectl describe pod <pod>

kubectl logs <pod>

kubectl logs -f <pod>

kubectl exec -it <pod> -- /bin/bash

kubectl get deployment

kubectl get replicaset

kubectl get service

kubectl describe service <service>

kubectl get endpoints

kubectl get endpointslice

kubectl get ingress

kubectl get configmap

kubectl get secrets

kubectl get namespaces

kubectl get events

kubectl rollout status deployment/<name>

kubectl rollout history deployment/<name>

kubectl rollout undo deployment/<name>

kubectl scale deployment <name> --replicas=5

kubectl apply -f <file>.yaml

kubectl delete -f <file>.yaml
```

---

# Trainer Golden Rule

Never teach:

```text
YAML
 ↓
Memorize
 ↓
Next Object
```

Teach:

```text
Business Problem
       ↓
Technical Problem
       ↓
Why Kubernetes?
       ↓
Correct Object
       ↓
Architecture
       ↓
YAML
       ↓
Hands-On
       ↓
Failure
       ↓
Troubleshooting
       ↓
Enterprise Usage
       ↓
Interview
```

---

# Kubernetes Mental Model

Students should eventually understand:

```text
Container
   ↓
Pod
   ↓
ReplicaSet
   ↓
Deployment
   ↓
Service
   ↓
Ingress
   ↓
Application
```

For configuration:

```text
ConfigMap
Secret
```

For workloads:

```text
Deployment
DaemonSet
StatefulSet
Job
CronJob
```

For storage:

```text
PVC
 ↓
PV
 ↓
StorageClass
 ↓
Cloud Storage
```

For scaling:

```text
HPA
 ↓
More/Fewer Pods
```

For security:

```text
RBAC
NetworkPolicy
Secrets
```

For deployment automation:

```text
Helm
 ↓
GitOps
 ↓
Argo CD
```

For observability:

```text
Metrics
 ↓
Prometheus
 ↓
Grafana

Logs
 ↓
Loki
 ↓
Grafana
```

---

# Final Student Goal

At the end of this training, the student should not simply say:

> "I know Kubernetes YAML."

The student should be able to say:

> "I understand why Kubernetes is required, how a Kubernetes cluster works, how workloads are deployed, how Pods are managed, how applications are exposed, how configuration and secrets are handled, how storage works, how applications scale, how security is implemented, how Kubernetes is monitored, and how applications are deployed through CI/CD and GitOps."

That is the actual goal of **Kubernetes Zero to Hero**.

---

# Complete Learning Path

```text
                    KUBERNETES
                         |
             +-----------+-----------+
             |                       |
          BEGINNER                ADVANCED
             |                       |
           Pod                    Ingress
             |                    Storage
        ReplicaSet                Probes
             |                    HPA
        Deployment                RBAC
             |                    NetworkPolicy
          Service                     |
             |                        |
        Namespace                     |
             |                        |
     ConfigMap / Secret               |
             |                        |
       DaemonSet / StatefulSet        |
             |                        |
        Job / CronJob                 |
             |                        |
             +-----------+------------+
                         |
                       Helm
                         |
                       GitOps
                         |
                      Argo CD
                         |
                        EKS
                         |
                    Enterprise
                      Project
```

---

# Final Trainer Checklist

Before moving to the next topic, make sure students can answer:

```text
[ ] What is this object?
[ ] Why do we need it?
[ ] What problem does it solve?
[ ] What happens without it?
[ ] What is its architecture?
[ ] Can I create it?
[ ] Can I verify it?
[ ] Can I modify it?
[ ] Can I delete it?
[ ] Can I troubleshoot it?
[ ] Can I explain it to another junior?
[ ] Can I explain where it is used in production?
```

If the student can answer all of these:

```text
              UNDERSTAND
                  ↓
               PRACTICE
                  ↓
                 BREAK
                  ↓
             TROUBLESHOOT
                  ↓
                EXPLAIN
                  ↓
             ENTERPRISE
```

then move to the next Kubernetes concept.

---

# Final Trainer Statement

> **"Don't teach Kubernetes as a collection of YAML files. Teach Kubernetes as a solution to real production problems."**

```text
Problem
  ↓
Why?
  ↓
Kubernetes Object
  ↓
How?
  ↓
Hands-On
  ↓
Failure
  ↓
Troubleshooting
  ↓
Production
```

This is the teaching approach used throughout this README.


## 2.2 Why DevOps Engineers Need Linux

Most DevOps infrastructure uses Linux extensively:

```text
Developer
   ↓
Git
   ↓
Jenkins
   ↓
Docker
   ↓
Kubernetes
   ↓
AWS EC2 / EKS
   ↓
Linux Infrastructure
```

A DevOps engineer should be comfortable with:

* Files
* Permissions
* Processes
* Networking
* Services
* Logs
* Storage
* Users
* SSH
* Shell scripting
* Troubleshooting

---

# 3. Linux Architecture

```text
+----------------------------------+
|          Applications            |
+----------------------------------+
|       Shell / Utilities          |
+----------------------------------+
|          System Libraries        |
+----------------------------------+
|          Linux Kernel            |
+----------------------------------+
|             Hardware             |
+----------------------------------+
```

## 3.1 Kernel

The kernel communicates with hardware.

It manages:

* CPU
* Memory
* Processes
* Storage
* Networking
* Devices

---

## 3.2 Shell

The shell allows us to interact with Linux.

Example:

```bash
bash
```

Common shells:

```text
bash
zsh
sh
fish
```

---

# 4. Linux Installation and Lab Setup

For training, use an Ubuntu-based environment.

Recommended environments:

```text
Laptop
  ↓
WSL / Virtual Machine
  ↓
Ubuntu
```

or:

```text
Local Machine
      ↓
AWS EC2
      ↓
Ubuntu / Amazon Linux
```

## Basic verification

```bash
cat /etc/os-release
uname -a
hostname
whoami
pwd
```

---

# 5. Linux Terminal Fundamentals

Before learning commands, students must understand:

```text
Command
Option
Argument
Path
Output
Exit Status
```

Example:

```bash
ls -lah /var/log
```

Breakdown:

```text
ls       → command
-l       → option
-a       → option
-h       → option
/var/log → argument
```

---

# 6. Linux File System

Linux uses a hierarchical filesystem.

```text
/
├── bin
├── boot
├── dev
├── etc
├── home
├── lib
├── media
├── mnt
├── opt
├── proc
├── root
├── run
├── sbin
├── srv
├── sys
├── tmp
├── usr
└── var
```

## Important directories

| Directory  | Purpose                        |
| ---------- | ------------------------------ |
| `/`        | Root of filesystem             |
| `/home`    | Normal users' home directories |
| `/root`    | Root user's home               |
| `/etc`     | Configuration                  |
| `/var`     | Variable data and logs         |
| `/var/log` | Logs                           |
| `/tmp`     | Temporary files                |
| `/opt`     | Optional/application software  |
| `/usr`     | User-space programs/libraries  |
| `/bin`     | Essential commands             |
| `/sbin`    | System administration commands |
| `/dev`     | Device files                   |
| `/proc`    | Process/kernel information     |
| `/sys`     | Kernel/device information      |
| `/boot`    | Boot-related files             |

---

# 7. Essential File and Directory Commands

> **Rule:** Every important command below has **5 labs**.

---

# 7.1 `pwd`

## What is `pwd`?

`pwd` means:

```text
Print Working Directory
```

It tells us where we currently are.

### Syntax

```bash
pwd
```
---

## Lab 1 — Check Current Directory

```bash
pwd
```

### Objective

Understand the current working directory.

---

## Lab 2 — Navigate and Verify

```bash
cd /tmp
pwd
```

---

## Lab 3 — Home Directory

```bash
cd ~
pwd
```

---

## Lab 4 — Parent Directory

```bash
cd ..
pwd
```

---

## Lab 5 — Production Directory Verification

```bash
cd /var/log
pwd
ls
```

### Interview Questions

1. What does `pwd` do?
2. Difference between absolute and relative paths?
3. What does `~` represent?

---

# 7.2 `ls`

## What is `ls`?

Lists files and directories.

### Basic syntax

```bash
ls
```

### Important options

```bash
ls -l
ls -a
ls -h
ls -lh
ls -la
ls -ltr
```

---

## Understanding `ls -l`

Example:

```text
-rw-r--r-- 1 ubuntu ubuntu 2456 Sep 24 10:30 app.conf
```

Breakdown:

```text
-              → File type
rw-r--r--      → Permissions
1              → Link count
ubuntu         → Owner
ubuntu         → Group
2456           → Size
Sep 24 10:30   → Modification time
app.conf       → Filename
```

---

## Lab 1 — Basic Listing

```bash
ls
```

---

## Lab 2 — Detailed Listing

```bash
ls -l
```

---

## Lab 3 — Hidden Files

```bash
ls -la
```

---

## Lab 4 — Human-Readable Sizes

```bash
ls -lh
```

---

## Lab 5 — Production Log Investigation

```bash
cd /var/log
ls -ltr
```

### Why `-ltr`?

```text
-l → detailed
-t → time sorted
-r → reverse
```

This is useful for identifying recently modified files.

---

# 7.3 `cd`

## Purpose

Change directory.

```bash
cd /var/log
```

---

## Lab 1

```bash
cd /tmp
pwd
```

## Lab 2

```bash
cd ..
pwd
```

## Lab 3

```bash
cd ~
pwd
```

## Lab 4

```bash
cd -
pwd
```

## Lab 5

Navigate:

```text
/opt
/opt/app
/opt/app/config
/opt/app/logs
```

using only `cd`.

---

# 7.4 `mkdir`

## Purpose

Create directories.

```bash
mkdir devops
```

### Important option

```bash
mkdir -p
```

`-p` creates parent directories when required.

---

## Lab 1

```bash
mkdir project
ls
```

## Lab 2

```bash
mkdir app logs config
ls
```

## Lab 3

```bash
mkdir -p project/application/config
```

## Lab 4 — Application Structure

```bash
mkdir -p shopsphere/{app,config,logs,backup}
```

Verify:

```bash
ls -R shopsphere
```

## Lab 5 — Production Directory

Create:

```text
/opt/company/app/
├── config
├── logs
├── releases
└── backup
```

Command:

```bash
sudo mkdir -p /opt/company/app/{config,logs,releases,backup}
```

---

# 7.5 `touch`

## Purpose

Create an empty file or update timestamps.

```bash
touch app.log
```

---

## Lab 1

```bash
touch file1.txt
```

## Lab 2

```bash
touch app.log error.log access.log
```

## Lab 3

```bash
mkdir logs
touch logs/application.log
```

## Lab 4

Create configuration files:

```bash
mkdir config
touch config/app.conf config/db.conf config/cache.conf
```

## Lab 5

Create a production-style structure:

```bash
mkdir -p application/{config,logs}
touch application/config/application.conf
touch application/logs/application.log
```

---

# 7.6 `cp`

## Purpose

Copy files/directories.

```bash
cp source destination
```

Important options:

```bash
-r
-p
-i
```

---

## Lab 1 — Copy File

```bash
touch app.conf
cp app.conf app.conf.backup
```

---

## Lab 2 — Copy Multiple Files

```bash
touch a.txt b.txt c.txt
mkdir backup
cp a.txt b.txt c.txt backup/
```

---

## Lab 3 — Copy Directory

```bash
mkdir -p application/config
touch application/config/app.conf

cp -r application application-backup
```

---

## Lab 4 — Preserve Attributes

```bash
cp -p app.conf app.conf.backup
```

---

## Lab 5 — Production Configuration Backup

Before modifying:

```bash
sudo cp /etc/nginx/nginx.conf \
/etc/nginx/nginx.conf.backup
```

### Team Lead Rule

> Never modify an important production configuration without knowing
> how you will recover it.

---

# 7.7 `mv`

## Purpose

Move or rename files/directories.

---

## Lab 1 — Rename

```bash
mv old.txt new.txt
```

## Lab 2 — Move File

```bash
mv app.log logs/
```

## Lab 3 — Move Directory

```bash
mv application /opt/
```

## Lab 4 — Rename Configuration

```bash
mv app.conf app.conf.old
```

## Lab 5 — Release Deployment

```text
releases/
├── app-1.0.0
├── app-1.1.0
└── current
```

Practice switching:

```bash
mv current current-old
mv app-1.1.0 current
```

Discuss why this pattern can support controlled deployments and why atomic deployment mechanisms are preferable in production.

---

# 7.8 `rm`

## Purpose

Remove files/directories.

```bash
rm file.txt
```

Important:

```bash
rm -r directory
rm -i file
```

### WARNING

```bash
rm -rf
```

is dangerous.

### Trainer Rule

> Never run `rm -rf` blindly in production.

---

## Lab 1

```bash
touch test.txt
rm test.txt
```

## Lab 2

```bash
touch a b c
rm a b c
```

## Lab 3

```bash
mkdir testdir
touch testdir/file
rm -r testdir
```

## Lab 4

```bash
touch important.txt
rm -i important.txt
```

## Lab 5 — Safe Cleanup

Find files first:

```bash
find /tmp -type f -name "*.log"
```

Then decide what can safely be removed.

---

# 7.9 `rmdir`

Removes empty directories.

```bash
rmdir directory
```

## 5 Labs

```bash
mkdir test
rmdir test
```

```bash
mkdir empty1 empty2
rmdir empty1 empty2
```

Create a file and observe:

```bash
mkdir test
touch test/file
rmdir test
```

Why does it fail?

Because the directory isn't empty.

---

# 7.10 `tree`

Displays directory structure.

```bash
tree
```

Example:

```text
project
├── app
├── config
│   └── application.conf
├── logs
│   └── application.log
└── backup
```

### 5 Labs

Practice:

```bash
tree project
tree -L 2 project
tree -a project
tree -d project
tree /etc 2>/dev/null | head
```

---

# 8. File Viewing Commands

---

# 8.1 `cat`

Displays file contents.

```bash
cat file.txt
```

## Lab 1

```bash
echo "Hello Linux" > file.txt
cat file.txt
```

## Lab 2

```bash
cat /etc/hostname
```

## Lab 3

```bash
cat file1 file2
```

## Lab 4

```bash
cat -n file.txt
```

## Lab 5

Create an application configuration and inspect it:

```bash
cat application.conf
```

### Trainer Note

For very large files, don't blindly use `cat`.

Use:

```bash
less
```

---

# 8.2 `less`

Useful for reading large files.

```bash
less application.log
```

Useful keys:

```text
Space → Next page
b     → Previous page
/word → Search
n     → Next match
q     → Quit
```

### 5 Labs

```bash
less /var/log/syslog
```

Search:

```text
/error
```

Next:

```text
n
```

Practice with:

* application logs
* access logs
* system logs
* configuration files
* large text files

---

# 8.3 `head`

Displays beginning of a file.

```bash
head file.txt
```

Options:

```bash
head -n 5 file.txt
```

### 5 Labs

```bash
head /var/log/syslog
head -n 5 /var/log/syslog
head -n 20 application.log
head -n 1 file.txt
head -n 50 access.log
```

---

# 8.4 `tail`

Displays the end of a file.

```bash
tail application.log
```

Important:

```bash
tail -f application.log
```

`-f` follows a changing file.

### Production Scenario

Application is running:

```text
User
 ↓
Load Balancer
 ↓
Application
 ↓
application.log
```

Trainer:

> "The user reports HTTP 500. Show me what the application is logging right now."

```bash
tail -f application.log
```

### 5 Labs

```bash
tail file.txt
tail -n 20 file.txt
tail -f application.log
tail -F application.log
tail -n 100 access.log
```

---

# 9. Searching Files and Data

---

# 9.1 `find`

One of the most important DevOps Linux commands.

Syntax:

```bash
find <path> <conditions>
```

---

## Lab 1 — Find by Name

```bash
find /tmp -name "*.log"
```

## Lab 2 — Find Files

```bash
find . -type f
```

## Lab 3 — Find Directories

```bash
find . -type d
```

## Lab 4 — Find Large Files

```bash
find /var -type f -size +100M 2>/dev/null
```

## Lab 5 — Production Log Search

```bash
find /var/log -type f -name "*.log" -mtime -1
```

Discuss:

```text
What files?
Where?
How old?
Why?
Can they be deleted?
```

---

# 9.2 `grep`

Search text.

```bash
grep "ERROR" application.log
```

Important options:

```bash
-i
-n
-r
-v
-c
```

---

## Lab 1

```bash
grep "ERROR" application.log
```

## Lab 2

```bash
grep -i "error" application.log
```

## Lab 3

```bash
grep -n "ERROR" application.log
```

## Lab 4

```bash
grep -r "database" /opt/app/
```

## Lab 5 — Incident Investigation

```bash
grep -i "error\|exception\|failed" application.log
```

Then:

```bash
grep -i "timeout" application.log
```

---

# 9.3 `wc`

Count lines, words and bytes.

```bash
wc file.txt
```

Examples:

```bash
wc -l application.log
wc -w file.txt
wc -c file.txt
```

### 5 Labs

Count:

* log lines
* configuration lines
* users
* errors
* HTTP requests

Example:

```bash
grep -i "ERROR" application.log | wc -l
```

---

# 9.4 `sort`

Sort text.

```bash
sort file.txt
```

Labs:

```bash
sort names.txt
sort -r names.txt
sort -n numbers.txt
sort -k2 data.txt
sort access.log
```

---

# 9.5 `uniq`

Remove/count adjacent duplicate lines.

```bash
sort names.txt | uniq
```

Count:

```bash
sort names.txt | uniq -c
```

Labs:

```bash
sort names.txt | uniq
sort names.txt | uniq -c
sort access.log | uniq -c
sort errors.log | uniq -c
sort users.txt | uniq -c
```

---

# 10. Redirection and Pipes

This is a **must-know DevOps concept**.

---

# 10.1 Standard Streams

```text
stdin  → 0
stdout → 1
stderr → 2
```

---

# 10.2 `>`

Overwrite output.

```bash
echo "hello" > file.txt
```

---

# 10.3 `>>`

Append output.

```bash
echo "new line" >> file.txt
```

---

# 10.4 `2>`

Redirect errors.

```bash
command 2> error.log
```

---

# 10.5 `|`

Pipe output from one command into another.

```bash
ps aux | grep nginx
```

---

## 5 Practical Labs

### Lab 1

```bash
ls > files.txt
cat files.txt
```

### Lab 2

```bash
echo "deployment successful" >> deployment.log
```

### Lab 3

```bash
find /root -name "*.log" 2>errors.log
```

### Lab 4

```bash
ps aux | grep java
```

### Lab 5 — Production Log Analysis

```bash
grep -i "ERROR" application.log | \
sort | \
uniq -c | \
sort -nr
```

Trainer asks:

> "What happened to the data after each pipe?"

Students must explain every stage.

---
