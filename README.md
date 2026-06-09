# Fleet

## Cluster Setup

Dev cluster setup:

```bash
minikube start -p dev
minikube addons enable ingress -p dev
```

Staging cluster setup:

```bash

```

## FluxCD Bootstrap

Dev cluster bootstrap:

```bash
export GITHUB_TOKEN=<...>
export GITHUB_USER=<...>  # used as an author of commit message
exprot GITHUB_EMAIL=<...> # used as an author for commit message

flux bootstrap github \
  --token-auth \
  --context=dev \
  --components-extra=source-watcher \
  --owner=${GITHUB_USER} \
  --repository=fleet \
  --branch=master \
  --path=clusters/dev \
  --personal \
  --author-name=${GITHUB_USER} \
  --author-email=${GITHUB_EMAIL} \
  --commit-message-appendix='[ci skip]'
  
git pull
```


