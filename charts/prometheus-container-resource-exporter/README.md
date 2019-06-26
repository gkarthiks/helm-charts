# prometheus-container-resource-exporter

[prometheus-container-resource-exporter](https://github.com/gkarthiks/container-resource-exporter) is a Prometheus format exporter for Container's resource metrics.

## TL;DR;

```bash
$ helm repo add gkarthiks https://gkarthiks.github.io/helm-charts
$ helm install --name container-resource-exporter gkarthiks/prometheus-container-resource-exporter
```

## Introduction

This chart bootstraps a [Container Resource Exporter (CRE)](https://github.com/gkarthiks/container-resource-exporter) deployment on a [Kubernetes](http://kubernetes.io) cluster using the [Helm](https://helm.sh) package manager.

## Prerequisites

- Kubernetes 1.8+ with Beta APIs enabled

## Installing the Chart

To install the chart with the release name `my-release`:

```bash
$ helm install --name container-resource-exporter gkarthiks/prometheus-container-resource-exporter
```

The command deploys prometheus-container-resource-exporter on the Kubernetes cluster in the default configuration.

## Uninstalling the Chart

To uninstall/delete the `my-release` deployment:

```bash
$ helm delete my-release
```

The command removes all the Kubernetes components associated with the chart and deletes the release.

## Configuration

The following table lists the configurable parameters and their default values.

| Parameter              | Description                                         | Default                                 |
| ---------------------- | --------------------------------------------------- | --------------------------------------- |
| `runScope.local`       | Running the CRE in namespaced scope                 | `true`                                  |
| `runScope.cluster`     | Running the CRE in cluster scope                    | `false`                                 |
| `replicaCount`         | desired number of prometheus-couchdb-exporter pods  | `1`                                     |
| `image.repository`     | prometheus-couchdb-exporter image repository        | `gesellix/couchdb-prometheus-exporter`  |
| `image.tag`            | prometheus-couchdb-exporter image tag               | `22`                                    |
| `image.pullPolicy`     | image pull policy                                   | `IfNotPresent`                          |
| `serviceAccount.create`| Creates the service account for CRE pod             | `true`                                  |
| `serviceAccount.name`  | Name of the service account to be created           | `true`                                  |
| `service.type`         | desired service type                                | `ClusterIP`                             |
| `service.port`         | service external port                               | `9984`                                  |
| `ingress.enabled`      | enable ingress controller resource                  | `false`                                 |
| `ingress.annotations`  | annotations for the host's ingress records          | `false`                                 |
| `ingress.path`         | path for the ingress route                          | `/`                                     |
| `ingress.hosts`        | list of host address for ingress creation           |                                         |
| `ingress.tls`          | utilize TLS backend in ingress                      |                                         |
| `resources`            | cpu/memory resource requests/limits                 | {}                                      |
| `nodeSelector`         | node labels for pod assignment                      | {}                                      |
| `tolerations`          | tolerations for pod assignment                      | {}                                      |
| `affinity`             | affinity settings for proxy pod assignments         | {}                                      |
| `podAnnotations`	     | annotations to add to each pod					   | {}                                      |
| `couchdb.uri`          | address of the couchdb                              | `http://couchdb.default.svc:5984`       |
| `couchdb.databases`    | comma separated databases to monitor                | `_all_dbs`                              |


For more information please refer to the [CRE](https://github.com/gkarthiks/container-resource-exporter) documentation.

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`. For example,

Alternatively, a YAML file that specifies the values for the parameters can be provided while installing the chart. For example,

```bash
$ helm install --name my-release -f values.yaml gkarthiks/prometheus-container-resource-exporter
```
