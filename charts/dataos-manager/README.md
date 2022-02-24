# DataOS® Manager Chart

You will need to create a values.yaml file to configure the dataos-manager application.

---

## Install the dataos-manager Helm Chart

### Prepare the Inputs

**Fill out dataos-manager-values.yaml**

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| licenseKey | string | `""` | DataOS Software License Key |
| primeApiKey | string | `""` | DataOS Prime API Key |
| primeCloudUserName | string | `""` | DataOS Prime Cloud Username |
| primeCloudPassword | string | `""` | DataOS Prime Cloud Password |
| instanceName | string | `""` | Fully Qualified Instance name `(ex. smiley-mouse.dataos.io)` |
| primeSyncIntervalUp | string | `"10m"` | Interval to Heartbeat Prime |
| primeSyncIntervalExecute | string | `"5m"` | Interval to Retrieve Execute Requests |
| gitopsProviderType | string | `"s3"` | GitOps Provider Type s3 or azurefile |
| gitopsS3Endpoint | string | `""` | GitOps S3 Endpoint blank for AWS, use storage.googleapis.com for GCP |
| gitopsS3Region | string | `""` | GitOps S3 Region |
| gitopsS3Bucket | string | `""` | GitOps S3 Bucket |
| gitopsS3AccessKey | string | `""` | GitOps S3 Access Key |
| gitopsS3SecretKey | string | `""` | GitOps S3 Secret Key |
| gitopsS3RootDir | string | `""` | GitOps S3 Root Directory in Bucket |
| gitopsAzureFileFileUrlTemplate | string | `"https://%s.file.core.windows.net/%s/%s"` | GitOps Azure File Url Template |
| gitopsAzureFileDirectoryUrlTemplate | string | `"https://%s.file.core.windows.net/%s"` | GitOps Azure File Url Template |
| gitopsAzureFileStorageAccountName | string | `""` | GitOps Azure File Storage Account Name |
| gitopsAzureFileShareName | string | `""` | GitOps Azure File Storage File Share Name in Storage Account |
| gitopsAzureFileAccessKey | string | `""` | GitOps Azure File Access Key to File Share |
| redisUrl | string | `""` | GitOps Redis Cache Url |
| redisDbId | string | `"8"` | GitOps Redis Cache DB ID |
| redisUseTls | string | `"false"` | GitOps Redis Cache Use TLS |

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