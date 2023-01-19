# DataOS® Manager Chart

You will need to create a values.yaml file to configure the dataos-manager application.

---

## Install the dataos-manager Helm Chart

### Prepare the Inputs

**Fill out dataos-manager-values.yaml**

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| primeAccountId | string | `""` | DataOS Account ID |
| primeApiKey | string | `""` | DataOS Prime API Key |
| instanceName | string | `""` | Fully Qualified Instance name `(ex. smiley-mouse.dataos.io)` |
| primeSyncIntervalUp | string | `"10m"` | Interval to Heartbeat Prime |
| primeSyncIntervalExecute | string | `"5m"` | Interval to Retrieve Execute Requests |

```sh
helm repo add dataos https://tmdc-io.github.io/dataos-helm
helm repo update
kubectl create ns dataos-manager
kubectl label ns dataos-manager dataos.io/partOf=dataos
helm install -n dataos-manager dataos-manager dataos/dataos-manager -f dataos-manager-values.yaml
```

## Make sure the dataos-manager is running

```sh
> kubectl -n dataos-manager rollout status statefulset/dataos-manager

statefulset rolling update complete 1 pods at revision dataos-manager-REV...

```

---

## TODO

- Get helm-doc implemented on the Charts
