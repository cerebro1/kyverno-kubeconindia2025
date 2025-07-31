# kyverno-kubeconindia2025
Kyverno Maintainer Track Demo for KubeCon India 2025

---

# 🔗 Chainsaw E2E Testing tool 

This repo contains policy test cases written using [Chainsaw](https://kyverno.github.io/chainsaw/0.2.3/quick-start/) — a powerful tool for writing E2E tests using YAML!

## 📦 Prerequisites

* Kubernetes cluster (v1.24+ recommended)
* [`kubectl`](https://kubernetes.io/docs/tasks/tools/) installed
* [`chainsaw`](https://kyverno.github.io/chainsaw/0.2.3/quick-start/install/) installed

> Install `chainsaw` via `go`:

```bash
go install github.com/kyverno/chainsaw@latest
```

Or via `brew` (if using macOS):

add tap
```bash
brew tap kyverno/chainsaw https://github.com/kyverno/chainsaw
```
install chainsaw

```bash
brew install kyverno/chainsaw/chainsaw
```

## 📁 Repo Structure
Sure — here's the section formatted for direct inclusion in your `README.md`:

```markdown
## 📁 Directory Structure

```

.
├── comparison-1/
│   ├── .chainsaw-test/                  # has Test resource (e.g., Pod manifest)
│   │   └── chainsaw-test.yaml           # Chainsaw test case for verifying policy behavior
│   ├── cpol.yaml                        # Kyverno ClusterPolicy
│   └── require-pod-requests-limits.yaml # Kyverno ValidatingPolicy (NewPolicy Types)
├── comparison-2/
│   └── ...
├── extras/
│   └── ...
├── README.md


```


Each folder contains:

* One Chainsaw YAML test files
* Kyverno policies and test resources

## 🚀 Running Tests

From the root of this repo, run:

```bash
chainsaw test .
```

To run a specific test:

```bash
chainsaw test ./comparison-1
```


## 🧪 Writing Tests

A Chainsaw test includes:

* Setup resources (e.g., policies)
* Action steps (e.g., create pod, patch policy)
* Assertions (e.g., resource exists, has label)

Example snippet:

```yaml
steps:
  - apply:
      file: policy.yaml
  - assert:
      file: expected-result.yaml
```

See the full Chainsaw docs: [kyverno.io/docs/chainsaw](https://kyverno.io/docs/chainsaw)

## 🧼 Cleanup

Tests cleanup the resources whether fail or pass after completion



