## To deploy Kubernetes manually;

The Values.yaml File contains Deployment and Service. We revise it according to our own system. We give the information of our repo to Containers in Deployment.


### Environment variable	Description
ACCEPT_EULA	Set the ACCEPT_EULA variable to any value to confirm your acceptance of the End-User Licensing Agreement. Required setting for the SQL Server image.

### MSSQL_PID	Set the SQL Server edition or product key. Possible values include:

* Evaluation
* Developer
* Express
* Web
* Standard
* Enterprise


## Quick Installation

```bash
$ kubectl create ns mssql
```

```bash
$ helm  install my-release . --set ACCEPT_EULA.value=Y --set MSSQL_PID.value=Developer -n mssql
```
## Delete Chart

```bash
$ helm delete -n mssql my-release
```

## Configuration

The following table lists the configurable parameters of the Couchbase chart and their default values.

| Parameter                                      | Description                                                                                                                                           | Default                           |
|------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------|
| `image.repository`                     | `mssql` image repository                                                                                                                            | `mcr.microsoft.com/mssql/server`                |
| `image.tag`                            | `mssql` image tag                                                                                                                                   | `2019-latest`                         |
| `image.pullPolicy`                     | Image pull policy                                                                                                                                     | `IfNotPresent`                    |
| `replicaCount`                             | The number of mssql instances in the cluster. The chart will automatic create assign master to one of replicaCount                                      | `1`                               |
| `resources`                            | CPU/Memory resource requests/limits                                                                                                                   | Memory: `4096i`, CPU: `100m`     |
| `nodeSelector`                         | couchbase server pod assignment                                                                                                                         | `{}`                              |
| `affinity`                             | couchbase server affinity                                                                                                                               | `{}`                              |
| `tolerations`                          | couchbase server tolerations                                                                                                                            | `[]`                              |
| `nodeSelector`                         | couchbase server node selector                                                                                                                          | `{}`                              |
| `podSecurityContext`                   | Set security context for defining privilege and accessing control settings entire Pod                                                                 | `{}`                              |
| `securityContext`                      | Set security context for defining privilege and accessing control settings for couchbase container                                                      | `privileged: false`               |
| `service.type`                         | Kubernetes Service type                                                                                                                               | `ClusterIP`                       |
| `service.port`                         | couchbase Service port                                                                                                                                  | `9000`                            |
| `podAnnotations`                       | Kubernetes Pod annotations                                                                                                                            | `{}`                              |
| `pvc.storageClass`             | Storage class of backing PVC (uses storage class annotation)                                                                                          | `nil`                             |
| `pvc.mssqlDataMode`               | Use volume as ReadOnly or ReadWrite                                                                                                                   | `ReadWriteOnce`                   |
| `pvc.DataSize`                     | Size of data volume                                                                                                                                   | `50Gi`                            |
| `ingress.enabled`                      | If true, Couchbase Ingress will be created                                                                                                          |
| `ingress.port`                         | couchbase Ingress port                                                                                                                                  | `false`                           |
| `ingress.annotations`                  | couchbase Ingress annotations                                                                                                                           | `{}`                              |
| `ingress.hosts`                        | couchbase Ingress host names                                                                                                                            | `[]`                              |
| `ingress.tls`                          | couchbase Ingress TLS configuration (YAML)                                                                                                              | `[]`                              |                                                                     
| `serviceAccount.create`                        | If true, create the Couchbase service account                                                                                                           | `true`                            |
| `serviceAccount.name`                          | Name of the server service account to use or create                                                                                                   | `{{ fullname }}`          |
| `serviceAccount.annotations`                   | Service Account annotations                                                                                                                           | `{}`                              |
| `imagePullSecrets`                             | Configuration for [imagePullSecrets][3] so that you can use a private registry for your images                                                        | `[]`                              |



