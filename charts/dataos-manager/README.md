# DataOS® Manager Chart

You will need to create a values.yaml file to configure the dataos-manager application.

---

## Fill out dataos-manager-values.yaml


## Install helm chart

```sh
helm repo add dataos https://tmdc-io.github.io/dataos-helm
helm repo update
kubectl create ns dataos-manager
helm install -n dataos-manager dataos-manager dataos/dataos-manager -f dataos-manager-values.yaml
```

## Make sure the dataos-manager is running

```sh
> kubectl -n dataos-manager rollout status statefulset.apps/dataos-manager
stateful set "dataos-manager" successfully rolled out
```

