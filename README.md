# helm-cert-manager-example

cert-manager is a native Kubernetes certificate management controller. It can help with issuing certificates from a variety of sources, such as Let’s Encrypt, HashiCorp Vault, Venafi, a simple signing key pair, or self signed.

You can modify it and use cert-manager. There is example about installing it with Helm in the article.

## Prerequisites

- [Kubernetes(K8S)](https://kubernetes.io/)
    Kubernetes (K8s) is an open-source system for automating deployment, scaling, and management of containerized applications.

- [Helm](https://helm.sh/)
    Helm is the best way to find, share, and use software built for Kubernetes.

## How to Install

```shell
# git clone example and cert-manager.
$ git clone --recursive https://github.com/CloudoLife/helm-cert-manager-example

$ cd helm-cert-manager-example
```

### Custom Values.yaml

Edit [values.yaml](./values.yaml) in helm-cert-manager-example directory, and replace content within < and >.
```shell
# cat values.yaml


# cert-manager/values.yaml at master · jetstack/cert-manager
# https://github.com/jetstack/cert-manager/blob/master/deploy/charts/cert-manager/values.yaml

installCRDs: true
```

### Install by Helm

Helm install cert-manager within cert-manager namespace. Please create cert-manager namespace first if not exist.

```shell
# Add the Jetstack Helm repository:
$ helm repo add jetstack https://charts.jetstack.io

# Update your local Helm chart repository cache:
$ helm repo update

# To install the cert-manager Helm chart:
$ helm install cert-manager jetstack/cert-manager --namespace cert-manager -f values.yaml
```

See Helm release about cert-manager.

```shell
$ helm list -n cert-manager
NAME                       	NAMESPACE   	REVISION	UPDATED                               	STATUS  	CHART                            	APP VERSION
cert-manager	cert-manager	1       	2020-09-25 12:57:30.168666 +0800 +0800	deployed	webhook-alidns-0.1.0             	1.0
```

See pods about cert-manager.

```shell
$ kubectl get pods -n cert-manager
...
```

## References
[1] [CloudoLife/helm-cert-manager-example: Examples about Helm install cert-manager. https://github.com/CloudoLife/helm-cert-manager-example - https://github.com/CloudoLife/helm-cert-manager-example](https://github.com/CloudoLife/helm-cert-manager-example)

[2] [cert-manager - https://cert-manager.io/](https://cert-manager.io/)

[3] [Helm - https://helm.sh/](https://helm.sh/)

[4] [Kubernetes - https://kubernetes.io/](https://kubernetes.io/)