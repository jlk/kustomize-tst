# Really basic kustomize deployment

This repo contains a [kustomize](https://kustomize.io/) deployment that I copied a good chunk of from the Internet - can't 
remember where I got it now. :(

In a nutshell, it creates a kubernetes deployment, service, and configmap that results in 3 little demo pods.

Besides the base profile, there's 2 "overlays" - a "staging" version, and a "production" version.

## Prerequisites
Kustomize needs to be installed - [this page](https://kubectl.docs.kubernetes.io/installation/kustomize/) has 
instructions for various source or binary versions.

## Use
Basically for any of these, cd into either `base`, `overlays/staging`, or `overlays/production`, and then run...

```
kustomize build .|kubectl apply -f -
```

`kustomize build` generates kubectl yaml, and then that's applied by kubectl.

You can check if this is running with `kubectl`:
```
$ kubectl get pod
NAME                                      READY   STATUS    RESTARTS   AGE
staging-the-deployment-6cd65cfc7f-8v2s4   1/1     Running   0          66m
staging-the-deployment-6cd65cfc7f-k2jnn   1/1     Running   0          66m
staging-the-deployment-6cd65cfc7f-zpkf9   1/1     Running   0          66m
```

