# prometheus-node-exporter

![Version: 4.21.8](https://img.shields.io/badge/Version-4.21.8-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 1.6.0](https://img.shields.io/badge/AppVersion-1.6.0-informational?style=flat-square)

A Helm chart for prometheus node-exporter

## Requirements

| Repository | Name | Version |
|------------|------|---------|
| file://charts/calico-exporter | CalicoExporter | 0.3.* |
| file://charts/prometheus-process-exporter | ProcessExporter | 0.5.* |

## Install the Chart

Ensure Helm is initialized in your Kubernetes cluster.
For more details on initializing Helm, [read the Helm docs](https://helm.sh/docs/)

To install the chart with the release name `prometheus-node-exporter` into the namespace `kube-monitoring-sytem`:

```bash
helm install prometheus-node-exporter ./pkg/prometheus-node-exporter-4.21.8.tgz --namespace kube-monitoring-system
```

To enable `calico-exporter` and `process-exporter`, you can set the following values:

```bash
helm install prometheus-node-exporter ./prometheus-node-exporter-4.21.8.tgz --namespace kube-monitoring-system --set CalicoExporter.enabled=true --set ProcessExporter.enabled=true
```

## Verify installation

To verify the installation, check the pods in the `kube-monitoring-system` namespace:

```bash
helm list --namespace kube-monitoring-system
kubectl get po -n kube-monitoring-system
```

## Uninstall the Chart

To uninstall the `prometheus-node-exporter` release:

```bash
helm uninstall prometheus-node-exporter --namespace kube-monitoring-system
```

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| CalicoExporter.affinity | object | `{}` |  |
| CalicoExporter.bgpService.annotations."prometheus.io/scrape" | string | `"true"` |  |
| CalicoExporter.bgpService.innerPort | int | `19093` |  |
| CalicoExporter.bgpService.nodePort | string | `nil` |  |
| CalicoExporter.bgpService.port | int | `19094` |  |
| CalicoExporter.bgpService.targetPort | int | `19094` |  |
| CalicoExporter.bgpService.type | string | `"ClusterIP"` |  |
| CalicoExporter.calicoService.annotations."prometheus.io/scrape" | string | `"true"` |  |
| CalicoExporter.calicoService.innerPort | int | `9094` |  |
| CalicoExporter.calicoService.nodePort | string | `nil` |  |
| CalicoExporter.calicoService.port | int | `9094` |  |
| CalicoExporter.calicoService.targetPort | int | `9094` |  |
| CalicoExporter.calicoService.type | string | `"ClusterIP"` |  |
| CalicoExporter.enabled | bool | `false` |  |
| CalicoExporter.fullnameOverride | string | `"calico-exporter"` |  |
| CalicoExporter.hostNetwork | bool | `true` |  |
| CalicoExporter.image.pullPolicy | string | `"IfNotPresent"` |  |
| CalicoExporter.image.repository | string | `"kubesphere/calico-exporter"` |  |
| CalicoExporter.image.tag | string | `"v0.3.0"` |  |
| CalicoExporter.ippoolService.annotations."prometheus.io/scrape" | string | `"true"` |  |
| CalicoExporter.ippoolService.innerPort | int | `19095` |  |
| CalicoExporter.ippoolService.nodePort | string | `nil` |  |
| CalicoExporter.ippoolService.port | int | `19096` |  |
| CalicoExporter.ippoolService.targetPort | int | `19096` |  |
| CalicoExporter.ippoolService.type | string | `"ClusterIP"` |  |
| CalicoExporter.kubeRbacProxy.image.repository | string | `"brancz/kube-rbac-proxy"` |  |
| CalicoExporter.kubeRbacProxy.image.tag | string | `"v0.14.0"` |  |
| CalicoExporter.kubeRbacProxy.resources | object | `{}` |  |
| CalicoExporter.nodeSelector | object | `{}` |  |
| CalicoExporter.podAnnotations | object | `{}` |  |
| CalicoExporter.podLabels."app.kubernetes.io/name" | string | `"prometheus-node-exporter"` |  |
| CalicoExporter.resources.limits.cpu | int | `1` |  |
| CalicoExporter.resources.limits.memory | string | `"500Mi"` |  |
| CalicoExporter.resources.requests.cpu | string | `"102m"` |  |
| CalicoExporter.resources.requests.memory | string | `"180Mi"` |  |
| CalicoExporter.securityContext.runAsNonRoot | bool | `true` |  |
| CalicoExporter.securityContext.runAsUser | int | `65534` |  |
| CalicoExporter.serviceAccount.automountServiceAccountToken | bool | `true` |  |
| CalicoExporter.serviceAccount.imagePullSecrets | list | `[]` |  |
| CalicoExporter.serviceAccount.name | string | `"prometheus-node-exporter"` |  |
| CalicoExporter.serviceMonitor.enabled | bool | `true` |  |
| CalicoExporter.serviceMonitor.interval | string | `"30s"` |  |
| CalicoExporter.serviceMonitor.labels."app.kubernetes.io/vendor" | string | `"kubesphere"` |  |
| CalicoExporter.serviceMonitor.scrapeTimeout | string | `"30s"` |  |
| CalicoExporter.tolerations[0].effect | string | `"NoSchedule"` |  |
| CalicoExporter.tolerations[0].operator | string | `"Exists"` |  |
| CalicoExporter.updateStrategy.rollingUpdate.maxUnavailable | int | `1` |  |
| CalicoExporter.updateStrategy.type | string | `"RollingUpdate"` |  |
| ProcessExporter.affinity | object | `{}` |  |
| ProcessExporter.enabled | bool | `false` |  |
| ProcessExporter.endpoints | list | `[]` |  |
| ProcessExporter.extraArgs | object | `{}` |  |
| ProcessExporter.extraHostVolumeMounts | object | `{}` |  |
| ProcessExporter.fullnameOverride | string | `"process-exporter"` |  |
| ProcessExporter.groups[0].cmdline[0] | string | `".+"` |  |
| ProcessExporter.groups[0].name | string | `"{{.Comm}}"` |  |
| ProcessExporter.hostNetwork | bool | `false` |  |
| ProcessExporter.image.pullPolicy | string | `"IfNotPresent"` |  |
| ProcessExporter.image.repository | string | `"ncabatoff/process-exporter"` |  |
| ProcessExporter.image.tag | string | `"0.5.0"` |  |
| ProcessExporter.kubeRbacProxy.image | string | `"kubesphere/kube-rbac-proxy"` |  |
| ProcessExporter.kubeRbacProxy.resources | object | `{}` |  |
| ProcessExporter.kubeRbacProxy.tag | string | `"v0.11.0"` |  |
| ProcessExporter.nodeSelector | object | `{}` |  |
| ProcessExporter.podAnnotations | object | `{}` |  |
| ProcessExporter.podLabels."app.kubernetes.io/name" | string | `"prometheus-node-exporter"` |  |
| ProcessExporter.rbac.create | bool | `true` |  |
| ProcessExporter.rbac.pspEnabled | bool | `false` |  |
| ProcessExporter.resources | object | `{}` |  |
| ProcessExporter.securityContext.runAsNonRoot | bool | `true` |  |
| ProcessExporter.securityContext.runAsUser | int | `65534` |  |
| ProcessExporter.service.annotations."prometheus.io/scrape" | string | `"true"` |  |
| ProcessExporter.service.innerPort | int | `19202` |  |
| ProcessExporter.service.nodePort | string | `nil` |  |
| ProcessExporter.service.port | int | `19201` |  |
| ProcessExporter.service.targetPort | int | `19201` |  |
| ProcessExporter.service.type | string | `"ClusterIP"` |  |
| ProcessExporter.serviceAccount.automountServiceAccountToken | bool | `true` |  |
| ProcessExporter.serviceAccount.create | bool | `false` |  |
| ProcessExporter.serviceAccount.imagePullSecrets | list | `[]` |  |
| ProcessExporter.serviceAccount.name | string | `"prometheus-node-exporter"` |  |
| ProcessExporter.serviceMonitor.enabled | bool | `true` |  |
| ProcessExporter.serviceMonitor.interval | string | `"30s"` |  |
| ProcessExporter.serviceMonitor.labels."app.kubernetes.io/vendor" | string | `"kubesphere"` |  |
| ProcessExporter.templates."config.yml" | string | `"process_names:\n{{ .Values.groups | toYaml }}\n"` |  |
| ProcessExporter.tolerations[0].effect | string | `"NoSchedule"` |  |
| ProcessExporter.tolerations[0].operator | string | `"Exists"` |  |
| ProcessExporter.updateStrategy.rollingUpdate.maxUnavailable | int | `1` |  |
| ProcessExporter.updateStrategy.type | string | `"RollingUpdate"` |  |
| affinity | object | `{}` |  |
| configmaps | list | `[]` |  |
| containerSecurityContext.readOnlyRootFilesystem | bool | `true` |  |
| daemonsetAnnotations | object | `{}` |  |
| dnsConfig | object | `{}` |  |
| endpoints | list | `[]` |  |
| env | object | `{}` |  |
| extraArgs | list | `[]` |  |
| extraHostVolumeMounts | list | `[]` |  |
| extraInitContainers | list | `[]` |  |
| extraManifests | list | `[]` |  |
| fullnameOverride | string | `""` |  |
| global.imagePullSecrets | list | `[]` |  |
| global.imageRegistry | string | `""` |  |
| hostNetwork | bool | `true` |  |
| hostPID | bool | `true` |  |
| hostRootFsMount.enabled | bool | `true` |  |
| hostRootFsMount.mountPropagation | string | `"HostToContainer"` |  |
| image.digest | string | `""` |  |
| image.pullPolicy | string | `"IfNotPresent"` |  |
| image.registry | string | `"quay.io"` |  |
| image.repository | string | `"prometheus/node-exporter"` |  |
| image.tag | string | `""` |  |
| imagePullSecrets | list | `[]` |  |
| kubeRBACProxy.containerSecurityContext | object | `{}` |  |
| kubeRBACProxy.enabled | bool | `false` |  |
| kubeRBACProxy.extraArgs | list | `[]` |  |
| kubeRBACProxy.image.pullPolicy | string | `"IfNotPresent"` |  |
| kubeRBACProxy.image.registry | string | `"quay.io"` |  |
| kubeRBACProxy.image.repository | string | `"brancz/kube-rbac-proxy"` |  |
| kubeRBACProxy.image.sha | string | `""` |  |
| kubeRBACProxy.image.tag | string | `"v0.14.0"` |  |
| kubeRBACProxy.proxyEndpointsPort | int | `0` |  |
| kubeRBACProxy.resources | object | `{}` |  |
| livenessProbe.failureThreshold | int | `3` |  |
| livenessProbe.httpGet.httpHeaders | list | `[]` |  |
| livenessProbe.httpGet.scheme | string | `"http"` |  |
| livenessProbe.initialDelaySeconds | int | `0` |  |
| livenessProbe.periodSeconds | int | `10` |  |
| livenessProbe.successThreshold | int | `1` |  |
| livenessProbe.timeoutSeconds | int | `1` |  |
| nameOverride | string | `""` |  |
| namespaceOverride | string | `""` |  |
| networkPolicy.enabled | bool | `false` |  |
| nginx.image.pullPolicy | string | `"IfNotPresent"` |  |
| nginx.image.registry | string | `""` |  |
| nginx.image.repository | string | `"nginxinc/nginx-unprivileged"` |  |
| nginx.image.tag | string | `"1.24"` |  |
| nginx.port | int | `18102` |  |
| nginx.resources | object | `{}` |  |
| nginx.securityContext | string | `nil` |  |
| nodeSelector."kubernetes.io/os" | string | `"linux"` |  |
| podAnnotations."cluster-autoscaler.kubernetes.io/safe-to-evict" | string | `"true"` |  |
| podLabels | object | `{}` |  |
| prometheus.monitor.additionalLabels | object | `{}` |  |
| prometheus.monitor.apiVersion | string | `""` |  |
| prometheus.monitor.attachMetadata.node | bool | `false` |  |
| prometheus.monitor.basicAuth | object | `{}` |  |
| prometheus.monitor.bearerTokenFile | string | `nil` |  |
| prometheus.monitor.enabled | bool | `false` |  |
| prometheus.monitor.interval | string | `""` |  |
| prometheus.monitor.jobLabel | string | `""` |  |
| prometheus.monitor.labelLimit | int | `0` |  |
| prometheus.monitor.labelNameLengthLimit | int | `0` |  |
| prometheus.monitor.labelValueLengthLimit | int | `0` |  |
| prometheus.monitor.metricRelabelings | list | `[]` |  |
| prometheus.monitor.namespace | string | `""` |  |
| prometheus.monitor.podTargetLabels | list | `[]` |  |
| prometheus.monitor.proxyUrl | string | `""` |  |
| prometheus.monitor.relabelings | list | `[]` |  |
| prometheus.monitor.sampleLimit | int | `0` |  |
| prometheus.monitor.scheme | string | `"http"` |  |
| prometheus.monitor.scrapeTimeout | string | `"10s"` |  |
| prometheus.monitor.selectorOverride | object | `{}` |  |
| prometheus.monitor.targetLimit | int | `0` |  |
| prometheus.monitor.tlsConfig | object | `{}` |  |
| prometheus.podMonitor.additionalLabels | object | `{}` |  |
| prometheus.podMonitor.apiVersion | string | `""` |  |
| prometheus.podMonitor.attachMetadata.node | bool | `false` |  |
| prometheus.podMonitor.authorization | object | `{}` |  |
| prometheus.podMonitor.basicAuth | object | `{}` |  |
| prometheus.podMonitor.bearerTokenSecret | object | `{}` |  |
| prometheus.podMonitor.enableHttp2 | string | `""` |  |
| prometheus.podMonitor.enabled | bool | `false` |  |
| prometheus.podMonitor.filterRunning | string | `""` |  |
| prometheus.podMonitor.followRedirects | string | `""` |  |
| prometheus.podMonitor.honorLabels | bool | `true` |  |
| prometheus.podMonitor.honorTimestamps | bool | `true` |  |
| prometheus.podMonitor.interval | string | `""` |  |
| prometheus.podMonitor.jobLabel | string | `""` |  |
| prometheus.podMonitor.labelLimit | int | `0` |  |
| prometheus.podMonitor.labelNameLengthLimit | int | `0` |  |
| prometheus.podMonitor.labelValueLengthLimit | int | `0` |  |
| prometheus.podMonitor.metricRelabelings | list | `[]` |  |
| prometheus.podMonitor.namespace | string | `""` |  |
| prometheus.podMonitor.oauth2 | object | `{}` |  |
| prometheus.podMonitor.params | object | `{}` |  |
| prometheus.podMonitor.path | string | `"/metrics"` |  |
| prometheus.podMonitor.podTargetLabels | list | `[]` |  |
| prometheus.podMonitor.proxyUrl | string | `""` |  |
| prometheus.podMonitor.relabelings | list | `[]` |  |
| prometheus.podMonitor.sampleLimit | int | `0` |  |
| prometheus.podMonitor.scheme | string | `"http"` |  |
| prometheus.podMonitor.scrapeTimeout | string | `""` |  |
| prometheus.podMonitor.selectorOverride | object | `{}` |  |
| prometheus.podMonitor.targetLimit | int | `0` |  |
| prometheus.podMonitor.tlsConfig | object | `{}` |  |
| rbac.create | bool | `true` |  |
| rbac.pspAnnotations | object | `{}` |  |
| rbac.pspEnabled | bool | `true` |  |
| readinessProbe.failureThreshold | int | `3` |  |
| readinessProbe.httpGet.httpHeaders | list | `[]` |  |
| readinessProbe.httpGet.scheme | string | `"http"` |  |
| readinessProbe.initialDelaySeconds | int | `0` |  |
| readinessProbe.periodSeconds | int | `10` |  |
| readinessProbe.successThreshold | int | `1` |  |
| readinessProbe.timeoutSeconds | int | `1` |  |
| releaseLabel | bool | `false` |  |
| resources | object | `{}` |  |
| secrets | list | `[]` |  |
| securityContext.fsGroup | int | `65534` |  |
| securityContext.runAsGroup | int | `65534` |  |
| securityContext.runAsNonRoot | bool | `true` |  |
| securityContext.runAsUser | int | `65534` |  |
| service.annotations."prometheus.io/scrape" | string | `"true"` |  |
| service.listenOnAllInterfaces | bool | `true` |  |
| service.nodePort | string | `nil` |  |
| service.port | int | `19100` |  |
| service.portName | string | `"metrics"` |  |
| service.targetPort | int | `19100` |  |
| service.type | string | `"ClusterIP"` |  |
| serviceAccount.annotations | object | `{}` |  |
| serviceAccount.automountServiceAccountToken | bool | `false` |  |
| serviceAccount.create | bool | `true` |  |
| serviceAccount.imagePullSecrets | list | `[]` |  |
| serviceAccount.name | string | `"prometheus-node-exporter"` |  |
| sidecarHostVolumeMounts | list | `[]` |  |
| sidecarVolumeMount | list | `[]` |  |
| sidecars | list | `[]` |  |
| tolerations[0].effect | string | `"NoSchedule"` |  |
| tolerations[0].operator | string | `"Exists"` |  |
| updateStrategy.rollingUpdate.maxUnavailable | int | `1` |  |
| updateStrategy.type | string | `"RollingUpdate"` |  |
| verticalPodAutoscaler.controlledResources | list | `[]` |  |
| verticalPodAutoscaler.enabled | bool | `false` |  |
| verticalPodAutoscaler.maxAllowed | object | `{}` |  |
| verticalPodAutoscaler.minAllowed | object | `{}` |  |
