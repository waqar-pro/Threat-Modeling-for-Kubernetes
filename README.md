# Kubernetes Threat Modeling & Security Hardening 🛡️

Hands-on lab implementing security hardening on a multi-tier application in Kubernetes.

---

## Application Architecture

3-tier e-commerce application:


---

## What I Implemented

### Task 1: Environment Setup
- Deployed 3-tier e-commerce app on Minikube
- Frontend (3 replicas), Backend (2 replicas), Database (1 replica)

### Task 2: Threat Modeling
- Mapped 5 trust boundaries across the architecture
- Traced all data flows from internet to database
- Documented attack surface in threat model

### Task 3: Attack Vectors Identified
- Containers running as root (no security context)
- Flat network — frontend could directly access database
- Hardcoded credentials in environment variables
- No resource limits — vulnerable to DoS

### Task 4: Security Hardening
- **Pod Security Standards** — non-root, read-only filesystem, dropped ALL capabilities
- **Network Policies** — micro-segmentation between tiers
- **Kubernetes Secrets** — removed hardcoded credentials
- **Resource Quotas & Limit Ranges** — DoS protection

### Task 5: Validation
| Test | Expected | Result |
|------|----------|--------|
| Frontend → Database | BLOCKED | ✅ |
| Backend → Database | ALLOWED | ✅ |
| Pod Security Compliance | PASSED | ✅ |

---

## Key Takeaway
> Default Kubernetes is NOT secure.
> Every layer must be explicitly hardened.

---

## Tools Used
- Kubernetes (Minikube)
- kubectl
- Network Policies
- Pod Security Standards
- Resource Quotas

---

## Author
**[WAQAR HUSSIAN]**
[LinkedIn](https://www.linkedin.com/posts/waqar-hussain-c_kubernetes-devsecops-threatmodeling-ugcPost-7452895966271094784-Ky36?utm_source=share&utm_medium=member_desktop&rcm=ACoAAFjiFo0BxoXETYoDBg8RIbY-uEiLJGB5Il0)
