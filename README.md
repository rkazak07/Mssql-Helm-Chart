## Mssql Helm Chart Deploy

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

The following table lists the configurable parameters of the mssql chart and their default values.

| Parameter                                      | Description                                                                                                                                           | Default                           |
|------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------|
| `image.repository`                     | `mssql` image repository                                                                                                                            | `mcr.microsoft.com/mssql/server`                |
| `image.tag`                            | `mssql` image tag                                                                                                                                   | `2019-latest`                         |
| `image.pullPolicy`                     | Image pull policy                                                                                                                                     | `IfNotPresent`                    |
| `replicaCount`                             | The number of mssql instances in the cluster. The chart will automatic create assign master to one of replicaCount                                      | `1`                               |
| `resources`                            | CPU/Memory resource requests/limits                                                                                                                   | Memory: `4096i`, CPU: `100m`     |
| `ACCEPT_EULA.value`                            | ACCEPT_EULA variable to any value to confirm your acceptance of the End-User Licensing Agreement.                                                                                                                   |  `y`     |
| `MSSQL_PID.value`                         | MSSQL_PID Set the SQL Server edition or product key                                                                                                                       | `Developer`                              |
| `MSSQL_AGENT_ENABLED.values`                         | mssql agent                                                                                                                        | `true`                              |
| `hostname`                         | mssql server  hostname                                                                                                                         | `mssql`                              |
| `sa_password`                         | mssql server  sa user password                                                                                                                        | ` " " `                              |
| `nodeSelector`                         | mssql server pod assignment                                                                                                                         | `{}`                              |
| `affinity`                             | mssql server affinity                                                                                                                               | `{}`                              |
| `tolerations`                          | mssql server tolerations                                                                                                                            | `[]`                              |
| `nodeSelector`                         | mssql server node selector                                                                                                                          | `{}`                              |
| `podSecurityContext`                   | Set security context for defining privilege and accessing control settings entire Pod                                                                 | `{}`                              |
| `securityContext`                      | Set security context for defining privilege and accessing control settings for couchbase container                                                      | `privileged: false`               |
| `service.type`                         | Kubernetes Service type                                                                                                                               | `ClusterIP`                       |
| `service.port`                         | couchbase Service port                                                                                                                                  | `9000`                            |
| `podAnnotations`                       | Kubernetes Pod annotations                                                                                                                            | `{}`                              |
| `pvc.storageClass`             | Storage class of backing PVC (uses storage class annotation)                                                                                          | `nil`                             |
| `pvc.mssqlDataMode`               | Use volume as ReadOnly or ReadWrite                                                                                                                   | `ReadWriteOnce`                   |
| `pvc.DataSize`                     | Size of data volume                                                                                                                                   | `50Gi`                            |
| `ingress.enabled`                      | If true, mssql Ingress will be created                                                                                                          |
| `ingress.port`                         | mssql Ingress port                                                                                                                                  | `false`                           |
| `ingress.annotations`                  | mssql Ingress annotations                                                                                                                           | `{}`                              |
| `ingress.hosts`                        | mssql Ingress host names                                                                                                                            | `[]`                              |
| `ingress.paths`                        | mssql path parameters                                                                                                                           | `[]`                              |
| `ingress.tls`                          | mssql Ingress TLS configuration (YAML)                                                                                                              | `[]`                              |                                                                     
| `serviceAccount.create`                        | If true, create the msql service account                                                                                                           | `true`                            |
| `autoscaling.enabled`                        | If true, autoscaling enabled                                                                                                          | `false`                            |
| `autoscaling.minreplicas`                        | minimum replica count                                                                                                     | `1`                            |
| `autoscaling.maxReplicas`                        | maximum replica count                                                                                                          | `100`                            |
| `autoscaling.targetCPUUtilizationPercentage`                        | Target cpu utilization  percentage                                                                                                      | `100`                            |
| `serviceAccount.name`                          | Name of the server service account to use or create                                                                                                   | `{{ fullname }}`          |
| `serviceAccount.annotations`                   | Service Account annotations                                                                                                                           | `{}`                              |
| `imagePullSecrets`                             | Configuration for imagePullSecrets so that you can use a private registry for your images                                                        | `[]`                              |



