# Koperator Installer

This repository contains Helm Charts to automate the installation of Apache Kafka and Zookeeper, using [Koperator](https://github.com/banzaicloud/koperator).

## How to use

Install [Helm](https://helm.sh) if you haven't already, ArgoCD and the ArgoCD CLI.

```bash
$ kubectl port-forward svc/argocd-server -n argocd 8080:443
```

```bash
$ argocd login localhost:8080
```

```bash
$ argocd app create zookeeper --repo https://github.com/schultyy/koperator-install.git --path zookeeper --dest-namespace zookeeper --dest-server https://kubernetes.default.svc --sync-option Server-Side-Apply=true
```

```bash
$ argocd app sync zookeeper
```

```bash
$ argocd app create koperator --repo https://github.com/schultyy/koperator-install.git --path koperator --dest-namespace kafka --dest-server https://kubernetes.default.svc --sync-option Server-Side-Apply=true --sync-option validate=false
```

```bash
$ argocd app sync koperator
```
