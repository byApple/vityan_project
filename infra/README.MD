# Vityan project

## Overview
Vityan project is a demonstration platform, aimed to perform Danechka's experiene. It contains three kostil-type python apps, deployed into kuber.

# Get started
## Installation guide
**Install ingress-nginx controller into insress-nginx namespace**
```bash
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.5.1/deploy/static/provider/cloud/deploy.yaml
```
**Install Cert manager**
```bash
kubectl apply -f https://github.com/jetstack/cert-manager/releases/download/v1.1.0/cert-manager.yaml
```
**Create cluster issuer for letsencrypt**
```bash
kubectl apply -f letsencrypt.yaml
```
**Deploy Vityan project**
```bash
kubectl apply -f vityan.yaml
```

# Test
open https://dyablo-inc.ru/test
