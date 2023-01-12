# Vityan project

## Overview
Vityan project is a demonstration platform, aimed to demonstrate Danechka's experience. It contains three kostil-type python apps, deployed into kuber.

# Get started
## Installation guide
**Install ingress-nginx controller into insress-nginx namespace**
```bash
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.5.1/deploy/static/provider/cloud/deploy.yaml
```
:point_up: at this moment you should manually link IP of new balancer to your DNS name. Later can be automated.

**Install Cert manager**
```bash
kubectl apply -f https://github.com/jetstack/cert-manager/releases/download/v1.1.0/cert-manager.yaml
```

**Create cluster issuer for letsencrypt**
```bash
kubectl apply -f letsencrypt.yaml
```
:point_up: sometimes fails with connection error. Just wait and try again. Later can be fixed.

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
open https://dyablo-inc.ru/service1
open https://dyablo-inc.ru/service2

# Coming soon
:chart_with_upwards_trend: Cluster monitoring (base level)
:incoming_envelope: Helm chart installation (maybe)
:toilet: More bugs (definitely)

