# Elasticsearch

[Elasticsearch](https://www.elastic.co/products/elasticsearch) is a highly scalable open-source full-text search and analytics engine. It allows you to store, search, and analyze big volumes of data quickly and in near real time.

## TL;DR

```console
$ helm install bitnami/elasticsearch
```

## Introduction

This chart bootstraps a [Elasticsearch](https://github.com/bitnami/bitnami-docker-elasticsearch) deployment on a [Kubernetes](http://kubernetes.io) cluster using the [Helm](https://helm.sh) package manager.

## Prerequisites

- Kubernetes 1.6+ with Beta APIs enabled
- PV provisioner support in the underlying infrastructure

## Installing the Chart

To install the chart with the release name `my-release`:

```console
$ helm install --name my-release bitnami/elasticsearch
```

The command deploys Elasticsearch on the Kubernetes cluster in the default configuration. The [configuration](#configuration) section lists the parameters that can be configured during installation.

> **Tip**: List all releases using `helm list`

## Uninstalling the Chart

To uninstall/delete the `my-release` release:

```console
$ helm delete my-release
```

The command removes all the Kubernetes components associated with the chart and deletes the release. Remove also the chart using `--purge` option:

```console
$ helm delete --purge my-release
```

## Configuration

The following table lists the configurable parameters of the Elasticsearch chart and their default values.

|            Parameter                              |                      Description                                                                                          |                               Default                               |
|---------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------|
| `image.registry`                                  | Elasticsearch image registry                                                                                              | `docker.io`                                                         |
| `image.repository`                                | Elasticsearch image repository                                                                                            | `bitnami/elasticsearch`                                             |
| `image.tag`                                       | Elasticsearch image tag                                                                                                   | `{VERSION}`                                                         |
| `image.pullPolicy`                                | Image pull policy                                                                                                         | `Always`                                                            |
| `image.pullSecrets`                               | Specify image pull secrets                                                                                                | `nil`                                                               |
| `name`                                            | Elasticsearch cluster name                                                                                                | `elastic`                                                           |
| `config`                                          | Elasticsearch node custom configuration                                                                                   | ``                                                                  |
| `master.name`                                     | Master-eligible node pod name                                                                                             | `master`                                                            |
| `master.replicas`                                 | Desired number of Elasticsearch master-eligible nodes                                                                     | `2`                                                                 |
| `master.heapSize`                                 | Master-eligible node heap size                                                                                            | `128m`                                                              |
| `master.antiAffinity`                             | Master-eligible node pod anti-affinity policy                                                                             | `soft`                                                              |
| `master.resources`                                | CPU/Memory resource requests/limits for master-eligible nodes pods                                                        | `requests: { cpu: "25m", memory: "256Mi" }`                         |
| `master.livenessProbe.enabled`                    | Enable/disable the liveness probe (master-eligible nodes pod)                                                             | `true`                                                              |
| `master.livenessProbe.initialDelaySeconds`        | Delay before liveness probe is initiated (master-eligible nodes pod)                                                      | `90`                                                                |
| `master.livenessProbe.periodSeconds`              | How often to perform the probe (master-eligible nodes pod)                                                                | `10`                                                                |
| `master.livenessProbe.timeoutSeconds`             | When the probe times out (master-eligible nodes pod)                                                                      | `5`                                                                 |
| `master.livenessProbe.successThreshold`           | Minimum consecutive successes for the probe to be considered successful after having failed (master-eligible nodes pod)   | `1`                                                                 |
| `master.livenessProbe.failureThreshold`           | Minimum consecutive failures for the probe to be considered failed after having succeeded                                 | `5`                                                                 |
| `master.readinessProbe.enabled`                   | Enable/disable the readiness probe (master-eligible nodes pod)                                                            | `true`                                                              |
| `master.readinessProbe.initialDelaySeconds`       | Delay before readiness probe is initiated (master-eligible nodes pod)                                                     | `90`                                                                |
| `master.readinessProbe.periodSeconds`             | How often to perform the probe (master-eligible nodes pod)                                                                | `10`                                                                |
| `master.readinessProbe.timeoutSeconds`            | When the probe times out (master-eligible nodes pod)                                                                      | `5`                                                                 |
| `master.readinessProbe.successThreshold`          | Minimum consecutive successes for the probe to be considered successful after having failed (master-eligible nodes pod)   | `1`                                                                 |
| `master.readinessProbe.failureThreshold`          | Minimum consecutive failures for the probe to be considered failed after having succeeded                                 | `5`                                                                 |
| `securityContext.enabled`            | Enable security context                                                                      | `true`                            |
| `securityContext.fsGroup`            | Group ID for the container                                                                   | `1001`                            |
| `securityContext.runAsUser`          | User ID for the container                                                                    | `1001`        
| `discovery.name`                                  | Discover node pod name                                                                                                    | `discovery`                                                         |
| `coordinating.name`                               | Coordinating-only node pod name                                                                                           | `coordinating-only`                                                      |
| `coordinating.replicas`                           | Desired number of Elasticsearch coordinating-only nodes                                                                   | `2`                                                                 |
| `coordinating.heapSize`                           | Coordinating-only node heap size                                                                                          | `128m`                                                              |
| `coordinating.antiAffinity`                       | Coordinating-only node pod anti-affinity policy                                                                           | `soft`                                                              |
| `coordinating.service.type`                       | Coordinating-only node kubernetes service type                                                                            | `ClusterIP`                                                         |
| `coordinating.service.port`                       | Elasticsearch REST API port                                                                                               | `9200`                                                              |
| `coordinating.resources`                          | CPU/Memory resource requests/limits for coordinating-only nodes pods                                                      | `requests: { cpu: "25m", memory: "256Mi" }`                         |
| `coordinating.livenessProbe.enabled`              | Enable/disable the liveness probe (coordinating-only nodes pod)                                                           | `true`                                                              |
| `coordinating.livenessProbe.initialDelaySeconds`  | Delay before liveness probe is initiated (coordinating-only nodes pod)                                                    | `90`                                                                |
| `coordinating.livenessProbe.periodSeconds`        | How often to perform the probe (coordinating-only nodes pod)                                                              | `10`                                                                |
| `coordinating.livenessProbe.timeoutSeconds`       | When the probe times out (coordinating-only nodes pod)                                                                    | `5`                                                                 |
| `coordinating.livenessProbe.successThreshold`     | Minimum consecutive successes for the probe to be considered successful after having failed (coordinating-only nodes pod) | `1`                                                                 |
| `coordinating.livenessProbe.failureThreshold`     | Minimum consecutive failures for the probe to be considered failed after having succeeded                                 | `5`                                                                 |
| `coordinating.readinessProbe.enabled`             | Enable/disable the readiness probe (coordinating-only nodes pod)                                                          | `true`                                                              |
| `coordinating.readinessProbe.initialDelaySeconds` | Delay before readiness probe is initiated (coordinating-only nodes pod)                                                   | `90`                                                                |
| `coordinating.readinessProbe.periodSeconds`       | How often to perform the probe (coordinating-only nodes pod)                                                              | `10`                                                                |
| `coordinating.readinessProbe.timeoutSeconds`      | When the probe times out (coordinating-only nodes pod)                                                                    | `5`                                                                 |
| `coordinating.readinessProbe.successThreshold`    | Minimum consecutive successes for the probe to be considered successful after having failed (coordinating-only nodes pod) | `1`                                                                 |
| `coordinating.readinessProbe.failureThreshold`    | Minimum consecutive failures for the probe to be considered failed after having succeeded                                 | `5`                                                                 |
| `data.name`                                       | Data node pod name                                                                                                        | `data`                                                              |
| `data.replicas`                                   | Desired number of Elasticsearch data nodes    nodes                                                                       | `3`                                                                 |
| `data.heapSize`                                   | Data node heap size                                                                                                       | `1024m`                                                             |
| `data.antiAffinity`                               | Data pod anti-affinity policy                                                                                             | `soft`                                                              |
| `data.resources`                                  | CPU/Memory resource requests/limits for data nodes                                                                        | `requests: { cpu: "25m", memory: "1152Mi" }`                        |
| `data.persistence.enabled`                        | Enable persistence using a `PersistentVolumeClaim`                                                                        | `true`                                                              |
| `data.persistence.annotations`                    | Persistent Volume Claim annotations                                                                                       | `{}`                                                                |
| `data.persistence.storageClass`                   | Persistent Volume Storage Class                                                                                           | ``                                                                  |
| `data.persistence.accessModes`                    | Persistent Volume Access Modes                                                                                            | `[ReadWriteOnce]`                                                   |
| `data.persistence.size`                           | Persistent Volume Size                                                                                                    | `8Gi`                                                               |
| `data.livenessProbe.enabled`                      | Enable/disable the liveness probe (data nodes pod)                                                                        | `true`                                                              |
| `data.livenessProbe.initialDelaySeconds`          | Delay before liveness probe is initiated (data nodes pod)                                                                 | `90`                                                                |
| `data.livenessProbe.periodSeconds`                | How often to perform the probe (data nodes pod)                                                                           | `10`                                                                |
| `data.livenessProbe.timeoutSeconds`               | When the probe times out (data nodes pod)                                                                                 | `5`                                                                 |
| `data.livenessProbe.successThreshold`             | Minimum consecutive successes for the probe to be considered successful after having failed (data nodes pod)              | `1`                                                                 |
| `data.livenessProbe.failureThreshold`             | Minimum consecutive failures for the probe to be considered failed after having succeeded                                 | `5`                                                                 |
| `data.readinessProbe.enabled`                     | Enable/disable the readiness probe (data nodes pod)                                                                       | `true`                                                              |
| `data.readinessProbe.initialDelaySeconds`         | Delay before readiness probe is initiated (data nodes pod)                                                                | `90`                                                                |
| `data.readinessProbe.periodSeconds`               | How often to perform the probe (data nodes pod)                                                                           | `10`                                                                |
| `data.readinessProbe.timeoutSeconds`              | When the probe times out (data nodes pod)                                                                                 | `5`                                                                 |
| `data.readinessProbe.successThreshold`            | Minimum consecutive successes for the probe to be considered successful after having failed (data nodes pod)              | `1`                                                                 |
| `data.readinessProbe.failureThreshold`            | Minimum consecutive failures for the probe to be considered failed after having succeeded                                 | `5`                                                                 |
| `ingest.enabled`                                  | Enable ingest nodes                                                                                                       | `false`                                                             |
| `ingest.name`                                     | Ingest node pod name                                                                                                      | `ingest`                                                            |
| `ingest.replicas`                                 | Desired number of Elasticsearch ingest nodes                                                                              | `2`                                                                 |
| `ingest.heapSize`                                 | Ingest node heap size                                                                                                     | `128m`                                                              |
| `ingest.antiAffinity`                             | Ingest node pod anti-affinity policy                                                                                      | `soft`                                                              |
| `ingest.resources`                                | CPU/Memory resource requests/limits for ingest nodes pods                                                                 | `requests: { cpu: "25m", memory: "256Mi" }`                         |
| `ingest.livenessProbe.enabled`                    | Enable/disable the liveness probe (ingest nodes pod)                                                                      | `true`                                                              |
| `ingest.livenessProbe.initialDelaySeconds`        | Delay before liveness probe is initiated (ingest nodes pod)                                                               | `90`                                                                |
| `ingest.livenessProbe.periodSeconds`              | How often to perform the probe (ingest nodes pod)                                                                         | `10`                                                                |
| `ingest.livenessProbe.timeoutSeconds`             | When the probe times out (ingest nodes pod)                                                                               | `5`                                                                 |
| `ingest.livenessProbe.successThreshold`           | Minimum consecutive successes for the probe to be considered successful after having failed (ingest nodes pod)            | `1`                                                                 |
| `ingest.livenessProbe.failureThreshold`           | Minimum consecutive failures for the probe to be considered failed after having succeeded                                 | `5`                                                                 |
| `ingest.readinessProbe.enabled`                   | Enable/disable the readiness probe (ingest nodes pod)                                                                     | `true`                                                              |
| `ingest.readinessProbe.initialDelaySeconds`       | Delay before readiness probe is initiated (ingest nodes pod)                                                              | `90`                                                                |
| `ingest.readinessProbe.periodSeconds`             | How often to perform the probe (ingest nodes pod)                                                                         | `10`                                                                |
| `ingest.readinessProbe.timeoutSeconds`            | When the probe times out (ingest nodes pod)                                                                               | `5`                                                                 |
| `ingest.readinessProbe.successThreshold`          | Minimum consecutive successes for the probe to be considered successful after having failed (ingest nodes pod)            | `1`                                                                 |
| `ingest.readinessProbe.failureThreshold`          | Minimum consecutive failures for the probe to be considered failed after having succeeded                                 | `5`                                                                 |
| `metrics.enabled`                                 | Enable prometheus exporter                                                                                                | `false`                                                             |
| `metrics.name`                                    | Metrics pod name                                                                                                          | `metrics`                                                           |
| `metrics.image.registry`                          | Metrics exporter image registry                                                                                           | `docker.io`                                                         |
| `metrics.image.repository`                        | Metrics exporter image repository                                                                                         | `bitnami/elasticsearch-exporter`                                    |
| `metrics.image.tag`                               | Metrics exporter image tag                                                                                                | `latest`                                                            |
| `metrics.image.pullPolicy`                        | Metrics exporter image pull policy                                                                                        | `Always`                                                            |
| `metrics.service.type`                            | Metrics exporter endpoint service type                                                                                    | `ClusterIP`                                                         |
| `metrics.resources`                               | Metrics exporter resource requests/limit                                                                                  | `requests: { cpu: "25m" }`                                          |
| `sysctlImage.registry`                          | Kernel settings modifier image registry                                                                                           | `docker.io`                                                         |
| `sysctlImage.repository`                        | Kernel settings modifier image repository                                                                                         | `busybox`                                    |
| `sysctlImage.tag`                               |  Kernel settings modifier image tag                                                                                                | `latest`                                                            |
| `sysctlImage.pullPolicy`                        | Kernel settings modifier image pull policy                                                                                        | `Always`
Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`. For example,

```console
$ helm install --name my-release \
  --set name=my-elastic,client.service.port=8080 \
  bitnami/elasticsearch
```

The above command sets the Elasticsearch cluster name to `my-elastic` and REST port number to `8080`.

Alternatively, a YAML file that specifies the values for the parameters can be provided while installing the chart. For example,

```console
$ helm install --name my-release -f values.yaml bitnami/elasticsearch
```

> **Tip**: You can use the default [values.yaml](values.yaml). [values-production.yaml](values-production.yaml) has defaults optimized for use in production environments.

## Persistence

The [Bitnami Elasticsearch](https://github.com/bitnami/bitnami-docker-elasticsearch) image stores the Elasticsearch data at the `/bitnami/elasticsearch/data` path of the container.

By default, the chart mounts a [Persistent Volume](http://kubernetes.io/docs/user-guide/persistent-volumes/) at this location. The volume is created using dynamic volume provisioning. See the [Configuration](#configuration) section to configure the PVC.
