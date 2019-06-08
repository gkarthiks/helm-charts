# ip-geo-locator

[ip-geo-locator](https://github.com/gkarthiks/ip-geo-locator) is a simple utility server written in go which queries the location of the IP addresses.

## TL;DR;

```bash
$ helm repo add gkarthiks https://gkarthiks.github.io/helm-charts
$ helm install --name ip-locator gkarthiks/ip-geo-locator
```

## Introduction

This deploys a stateless deployment of the [ip-geo-locator](https://github.com/gkarthiks/ip-geo-locator) on a [Kubernetes](http://kubernetes.io) cluster using the [Helm](https://helm.sh) package manager.

## Prerequisites

- Kubernetes 1.8+ with Beta APIs enabled

## Installing the Chart

To install the chart with the release name `ip-locator`:

```bash
$ helm repo add gkarthiks https://gkarthiks.github.io/helm-charts
$ helm install --name ip-locator gkarthiks/ip-geo-locator
```

The command deploys `ip-locator` on the Kubernetes cluster in the default configuration.

## Uninstalling the Chart

To uninstall/delete the `ip-locator` deployment:

```bash
$ helm delete ip-locator
```

The command removes all the Kubernetes components associated with the chart and deletes the release.

## Configuration

The following table lists the configurable parameters and their default values.

| Parameter              | Description                                         | Default                                 |
| ---------------------- | --------------------------------------------------- | --------------------------------------- |
| `replicaCount`         | desired number of ip-locator pods                   | `1`                                     |
| `image.repository`     | ip-locator image repository                         | `gkarthics/ip-geo-locator`              |
| `image.tag`            | ip-locator image tag                                | `v0.1.0`                                |
| `image.pullPolicy`     | image pull policy                                   | `IfNotPresent`                          |
| `service.type`         | desired service type                                | `ClusterIP`                             |
| `service.port`         | service external port                               | `8080`                                  |
| `ingress.enabled`      | enable ingress controller resource                  | `false`                                 |
| `ingress.annotations`  | annotations for the host's ingress records          | `false`                                 |
| `ingress.path`         | path for the ingress route                          | `/`                                     |
| `ingress.hosts`        | list of host address for ingress creation           |                                         |
| `ingress.tls`          | utilize TLS backend in ingress                      |                                         |
| `resources`            | cpu/memory resource requests/limits                 | {}                                      |
| `nodeSelector`         | node labels for pod assignment                      | {}                                      |
| `tolerations`          | tolerations for pod assignment                      | {}                                      |
| `affinity`             | affinity settings for proxy pod assignments         | {}                                      |
| `readinessProbe`       | readiness probe, as of now there is no endpoint to check. | `false`                           |
| `livenessProbe`        | liveness probe, as of now there is no endpoint to check. | `false`                            |


For more information please refer to the [ip-geo-locator](https://github.com/gkarthiks/ip-geo-locator) documentation.

PS: The request is served over the `/ip/` endpoints.

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`. For example,

```bash
$ helm install --name ip-locator \
  --set "image.tag=latest" \
    gkarthiks/ip-geo-locator
```

Alternatively, a YAML file that specifies the values for the parameters can be provided while installing the chart. For example,

```bash
$ helm install --name ip-locator -f values.yaml gkarthiks/ip-geo-locator
```
