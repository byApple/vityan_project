# Vityan project

## Overview
Vityan project is a demonstration platform, aimed to demonstrate Danechka's experience. It contains three kostil-type python apps, deployed into kuber.

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
**Configure ~/.docker/config.json to have access to private repo**

Should be something like this:
```yaml
{
        "auths": {
                "https://index.docker.io/v1/": {
                        "auth": "dc<...>d8"
                }
        }
}
```
**Create secret**
```bash
kubectl create secret generic regcred --from-file=.dockerconfigjson=/home/user/.docker/config.json     --type=kubernetes.io/dockerconfigjson
```

**Deploy Vityan project**
```bash
kubectl apply -f vityan.yaml
```

# Test
open https://dyablo-inc.ru/test
