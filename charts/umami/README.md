# umami

Umami is a simple, fast, privacy-focused alternative to Google Analytics.

## TL;DR;

```console
helm repo add christianknell https://christianknell.github.io/helm-charts
helm repo update
helm install my-release christianknell/umami
```

## Introduction

Umami is a simple, fast, privacy-focused alternative to Google Analytics.

This chart bootstraps [Umami](https://github.com/umami-software/umami) on a [Kubernetes](http://kubernetes.io) cluster using the [Helm](https://helm.sh) package manager.

## Prerequisites

- Kubernetes 1.19+

## Installing the Chart

To install the chart with the release name `my-release`:

```console
helm repo add christianknell https://christianknell.github.io/helm-charts
helm repo update
helm install my-release christianknell/umami
```

These commands deploy Umami on the Kubernetes cluster in the default configuration. The [Values](#values) section lists the values that can be configured during installation.

> **Tip**: List all releases using `helm list`

## Uninstalling the Chart

To uninstall the `my-release` deployment:

```console
helm uninstall my-release
```

The command removes all the Kubernetes components associated with the chart and deletes the release.

## Values

| Key                                           | Type   | Default                                                     | Description                                                                                                                                                                                          |
| --------------------------------------------- | ------ | ----------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| affinity                                      | object | `{}`                                                        | Affinity settings for pod assignment                                                                                                                                                                 |
| autoscaling.enabled                           | bool   | `false`                                                     | Enable Horizontal POD autoscaling                                                                                                                                                                    |
| autoscaling.maxReplicas                       | int    | `100`                                                       | Maximum number of replicas                                                                                                                                                                           |
| autoscaling.minReplicas                       | int    | `1`                                                         | Minimum number of replicas                                                                                                                                                                           |
| autoscaling.targetCPUUtilizationPercentage    | int    | `80`                                                        | Target CPU utilization percentage                                                                                                                                                                    |
| autoscaling.targetMemoryUtilizationPercentage | int    | `80`                                                        | Target Memory utilization percentage                                                                                                                                                                 |
| externalDatabase.auth.database                | string | `"mychart"`                                                 | Name of the database to use                                                                                                                                                                          |
| externalDatabase.auth.password                | string | `"mychart"`                                                 | Password to use                                                                                                                                                                                      |
| externalDatabase.auth.username                | string | `"mychart"`                                                 | Name of the user to use                                                                                                                                                                              |
| externalDatabase.hostname                     | string | `""`                                                        | Hostname of the database                                                                                                                                                                             |
| externalDatabase.port                         | int    | `5432`                                                      | Port used to connect to database                                                                                                                                                                     |
| externalDatabase.type                         | string | `"postgresql"`                                              | Type of database                                                                                                                                                                                     |
| extraEnv                                      | list   | `[]`                                                        | additional environment variables to be added to the pods. See https://umami.is/docs/environment-variables for a complete list of available variables. Most variables can be set under umami as well. |
| fullnameOverride                              | string | `""`                                                        | String to fully override `"umami.fullname"`                                                                                                                                                          |
| image.pullPolicy                              | string | `"Always"`                                                  | image pull policy                                                                                                                                                                                    |
| image.registry                                | string | `"ghcr.io"`                                                 | image registry                                                                                                                                                                                       |
| image.repository                              | string | `"umami-software/umami"`                                    | image repository                                                                                                                                                                                     |
| image.tag                                     | string | `"postgresql-v1.39.5"`                                      | Overrides the image tag                                                                                                                                                                              |
| imagePullSecrets                              | list   | `[]`                                                        | If defined, uses a Secret to pull an image from a private Docker registry or repository.                                                                                                             |
| ingress.annotations                           | object | `{}`                                                        | Additional annotations for the Ingress resource                                                                                                                                                      |
| ingress.className                             | string | `""`                                                        | IngressClass that will be be used to implement the Ingress                                                                                                                                           |
| ingress.enabled                               | bool   | `false`                                                     | Enable ingress record generation                                                                                                                                                                     |
| ingress.hosts                                 | list   | see [values.yaml](./values.yaml)                            | An array with hosts and paths                                                                                                                                                                        |
| ingress.tls                                   | list   | `[]`                                                        | An array with the tls configuration                                                                                                                                                                  |
| mysql.auth.database                           | string | `"mychart"`                                                 | Name for a custom database to create                                                                                                                                                                 |
| mysql.auth.password                           | string | `"mychart"`                                                 | Password for the custom user to create                                                                                                                                                               |
| mysql.auth.username                           | string | `"mychart"`                                                 | Name for a custom user to create                                                                                                                                                                     |
| mysql.enabled                                 | bool   | `false`                                                     | enable MySQL™ subchart from Bitnami                                                                                                                                                                  |
| nameOverride                                  | string | `""`                                                        | Provide a name in place of `umami`                                                                                                                                                                   |
| nodeSelector                                  | object | `{}`                                                        | Node labels for pod assignment                                                                                                                                                                       |
| podAnnotations                                | object | `{}`                                                        | Annotations to be added to pods                                                                                                                                                                      |
| podSecurityContext                            | object | `{}`                                                        | pod-level security context                                                                                                                                                                           |
| postgresql.auth.database                      | string | `"mychart"`                                                 | Name for a custom database to create                                                                                                                                                                 |
| postgresql.auth.password                      | string | `"mychart"`                                                 | Password for the custom user to create                                                                                                                                                               |
| postgresql.auth.username                      | string | `"mychart"`                                                 | Name for a custom user to create                                                                                                                                                                     |
| postgresql.enabled                            | bool   | `true`                                                      | enable PostgreSQL™ subchart from Bitnami                                                                                                                                                             |
| replicaCount                                  | int    | `1`                                                         | Number of replicas                                                                                                                                                                                   |
| resources                                     | object | `{}`                                                        | Resource limits and requests for the controller pods.                                                                                                                                                |
| securityContext                               | object | `{"runAsGroup":65533,"runAsNonRoot":true,"runAsUser":1001}` | container-level security context                                                                                                                                                                     |
| service.port                                  | int    | `3000`                                                      | Kubernetes port where service is exposed                                                                                                                                                             |
| service.type                                  | string | `"ClusterIP"`                                               | Kubernetes service type                                                                                                                                                                              |
| serviceAccount.annotations                    | object | `{}`                                                        | Annotations to add to the service account                                                                                                                                                            |
| serviceAccount.create                         | bool   | `true`                                                      | Specifies whether a service account should be created                                                                                                                                                |
| serviceAccount.name                           | string | `""`                                                        | The name of the service account to use. If not set and create is true, a name is generated using the fullname template                                                                               |
| tolerations                                   | list   | `[]`                                                        | Toleration labels for pod assignment                                                                                                                                                                 |
| umami.clientIpHeader                          | string | `""`                                                        | HTTP header to check for the client's IP address. This is useful when you're behind a proxy that uses non-standard headers.                                                                          |
| umami.collectApiEndpoint                      | string | `""`                                                        | Allows you to send metrics to a location different than the default /api/collect. This is to help you avoid some ad-blockers.                                                                        |
| umami.disableLogin                            | string | `"1"`                                                       | Disables the login page for the application                                                                                                                                                          |
| umami.disableTelemetry                        | string | `"1"`                                                       | Umami collects completely anonymous telemetry data in order help improve the application. You can choose to disable this if you don't want to participate.                                           |
| umami.disableUpdates                          | string | `"1"`                                                       | Disables the check for new versions of Umami                                                                                                                                                         |
| umami.forceSSL                                | string | `"1"`                                                       | This will redirect all requests from http to https in the Umami application. Note, this does not apply to the tracking script.                                                                       |
| umami.hash.existingSecret                     | string | `""`                                                        | Name of an existing secret containing the hash salt under the key hash-salt                                                                                                                          |
| umami.hash.salt                               | string | `""`                                                        | A random string used to generate unique values.                                                                                                                                                      |
| umami.hostname                                | string | `""`                                                        | hostname under which Umami will be reached                                                                                                                                                           |
| umami.ignoredIpAddresses                      | string | `""`                                                        | You can provide a comma-delimited list of IP address to exclude from data collection.                                                                                                                |
| umami.removeTrailingSlash                     | string | `"1"`                                                       | Removes the trailing slash from all incoming urls.                                                                                                                                                   |
| umami.trackerScriptName                       | string | `"umami"`                                                   | Allows you to assign a custom name to the tracker script different from the default umami. This is to help you avoid some ad-blockers.                                                               |

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`.

Alternatively, a YAML file that specifies the values for the parameters can be provided while installing the chart. For example,

```console
helm install my-release -f values.yaml christianknell/umami
```

---

Autogenerated from chart metadata using [helm-docs v1.11.0](https://github.com/norwoodj/helm-docs/releases/v1.11.0)
