# cron-schedules

[cron-schedules](https://github.com/gkarthiks/cronjob-schedule-table) is a simple utility web server in go which queries the list of avaialble CronJobs in the current namespace and displays along with the schedule corresponding to it.

## TL;DR;

```bash
$ helm repo add gkarthiks https://gkarthiks.github.io/helm-charts
$ helm install --name cron-schedules gkarthiks/cron-schedules
```

## Introduction

This deploys a stateless deployment of the [cron-schedules](https://github.com/gkarthiks/cronjob-schedule-table) on a [Kubernetes](http://kubernetes.io) cluster using the [Helm](https://helm.sh) package manager.

## Prerequisites

- Kubernetes 1.8+ with Beta APIs enabled

## Installing the Chart

To install the chart with the release name `cron-schedules`:

```bash
$ helm repo add gkarthiks https://gkarthiks.github.io/helm-charts
$ helm install --name cron-schedules gkarthiks/cron-schedules
```

The command deploys `cron-schedules` on the Kubernetes cluster in the default configuration.

## Uninstalling the Chart

To uninstall/delete the `cron-schedules` deployment:

```bash
$ helm delete cron-schedules
```

The command removes all the Kubernetes components associated with the chart and deletes the release.

## Configuration

The following table lists the configurable parameters and their default values.

| Parameter              | Description                                         | Default                                 |
| ---------------------- | --------------------------------------------------- | --------------------------------------- |
| `replicaCount`         | desired number of cron-schedules pods               | `1`                                     |
| `image.repository`     | cron-schedules image repository                     | `gkarthics/cronjob-schedule-table`      |
| `image.tag`            | cron-schedules image tag                            | `v0.1.0`                                |
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
| clusterScope.enabled   | To list the cronjobs on the cluster scope           | `true`                                  |
