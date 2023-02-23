# Demo-kustomize

## Summary

Short demo for demonstrate kustomize based deployment with pros and cons.


## Install kustomize

The following script detects your OS and downloads the appropriate kustomize binary to your current working directory.
(This script doesn’t work for ARM architecture.)
```
curl -s "https://raw.githubusercontent.com/kubernetes-sigs/kustomize/master/hack/install_kustomize.sh"  | bash
```

## Deployment

Create namespaces:
```
kubectl create namespace qa
kubectl create namespace prod
```

Deploy demo application into qa:
```
kustomize build overlays/qa | kubectl apply -n qa -f -
kubectl get all -n qa
```

then into prod:
```
kustomize build overlays/prod | kubectl apply -n prod -f -
kubectl get all -n prod
```