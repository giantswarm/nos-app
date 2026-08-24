# nos

Nebuly Open Source (NOS) is a Kubernetes-native solution for managing and optimizing GPU workloads.

**Homepage:** <https://github.com/giantswarm/nos-app>

## Source Code

* <https://github.com/nebuly-ai/nos>

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| image.name | string | `"giantswarm/nos-app"` |  |
| image.tag | string | `""` |  |
| registry.domain | string | `"gsoci.azurecr.io"` |  |
| nvidiaGpuResourceMemoryGB | int | `32` | Defines how many GB of memory each nvidia.com/gpu resource has. |
| allowDefaultNamespace | bool | `true` | If true allows to deploy `nos` chart in the `default` namespace |
| shareTelemetry | bool | `true` | If true, shares with Nebuly telemetry data collected only during the Chart installation |
| operator.enabled | bool | `true` | Enable or disable the `nos operator` |
| operator.replicaCount | int | `1` | Number of replicas of the controller manager Pod. |
| operator.logLevel | int | `0` | The level of log of the controller manager. Zero corresponds to `info`, while values greater or equal than 1 corresponds to higher debug levels. **Must be >= 0**. |
| operator.nameOverride | string | `""` |  |
| operator.fullnameOverride | string | `""` |  |
| operator.image.repository | string | `"ghcr.io/nebuly-ai/nos-operator"` | Sets the operator Docker repository |
| operator.image.tag | string | `""` | Overrides the operator Docker image tag whose default is the chart appVersion. |
| operator.image.pullPolicy | string | `"IfNotPresent"` | Sets the operator Docker image pull policy. |
| operator.kubeRbacProxy | object | - | Configuration of the [Kube RBAC Proxy](https://github.com/brancz/kube-rbac-proxy), which runs as sidecar of the operator Pods. |
| operator.leaderElection.enabled | bool | `true` | Enables/Disables the leader election of the operator controller manager. |
| operator.podSecurityContext | object | `{"runAsNonRoot":true}` | Sets the security context of the operator Pod. |
| operator.securityContext | object | `{"allowPrivilegeEscalation":false,"capabilities":{"drop":["ALL"]},"privileged":false,"readOnlyRootFilesystem":true,"runAsGroup":65534,"runAsNonRoot":true,"runAsUser":65534,"seccompProfile":{"type":"RuntimeDefault"}}` | Sets the security context of the operator container. |
| operator.resources | object | `{"limits":{"cpu":"500m","memory":"128Mi"},"requests":{"cpu":"10m","memory":"64Mi"}}` | Sets the resource limits and requests of the operator controller manager container. |
| operator.podAnnotations | object | `{}` | Sets the annotations of the operator Pod. |
| operator.tolerations | list | `[]` | Sets the tolerations of the operator Pod. |
| operator.affinity | object | `{}` | Sets the affinity config of the operator Pod. |
| operator.nodeSelector | object | `{}` | Sets the nodeSelector config of the operator Pod. |
| operator.webhookCertIssuerName | string | `"selfsigned-giantswarm"` |  |
| operator.webhookCertIssuerInstall | bool | `false` | Set to true in non GS clusters |
| scheduler.enabled | bool | `true` | Enable or disable the `nos scheduler` |
| scheduler.logLevel | int | `0` | The level of log of the scheduler. Zero corresponds to `info`, while values greater or equal than 1 corresponds to higher debug levels. **Must be >= 0**. |
| scheduler.config | object | `{}` | Overrides the Kube Scheduler configuration |
| scheduler.replicaCount | int | `1` | Number of replicas of the scheduler. |
| scheduler.nameOverride | string | `""` |  |
| scheduler.fullnameOverride | string | `""` |  |
| scheduler.image.repository | string | `"ghcr.io/nebuly-ai/nos-scheduler"` | Sets Docker image. |
| scheduler.image.pullPolicy | string | `"IfNotPresent"` | Sets Docker image pull policy. |
| scheduler.image.tag | string | `""` | Overrides the image tag whose default is the chart appVersion. |
| scheduler.leaderElection.enabled | bool | `true` | Enables/Disables the leader election when deployed with multiple replicas. |
| scheduler.resources | object | `{"limits":{"cpu":"500m","memory":"128Mi"},"requests":{"cpu":"10m","memory":"64Mi"}}` | Sets the resource limits and requests of the scheduler container. |
| scheduler.podAnnotations | object | `{}` | Sets the annotations of the scheduler Pod. |
| scheduler.tolerations | list | `[]` | Sets the tolerations of the scheduler deployment. |
| scheduler.affinity | object | `{}` | Sets the affinity config of the scheduler deployment. |
| scheduler.nodeSelector | object | `{}` | Sets the nodeSelector config of the scheduler deployment. |
| scheduler.securityContext | object | `{"allowPrivilegeEscalation":false,"capabilities":{"drop":["ALL"]},"privileged":false,"readOnlyRootFilesystem":true,"runAsGroup":65534,"runAsNonRoot":true,"runAsUser":65534,"seccompProfile":{"type":"RuntimeDefault"}}` | Sets the security context of the scheduler container |
| scheduler.podSecurityContext | object | `{"runAsNonRoot":true}` | Sets the security context of the scheduler Pod |
| gpuPartitioner.enabled | bool | `true` | Enable or disable the `nos gpu partitioner` |
| gpuPartitioner.logLevel | int | `0` | The level of log of the GPU Partitioner. Zero corresponds to `info`, while values greater or equal than 1 corresponds to higher debug levels. **Must be >= 0**. |
| gpuPartitioner.replicaCount | int | `1` | Number of replicas of the gpu-manager Pod. |
| gpuPartitioner.nameOverride | string | `""` |  |
| gpuPartitioner.fullnameOverride | string | `""` |  |
| gpuPartitioner.devicePlugin.config.name | string | `"nos-device-plugin-configs"` | Name of the ConfigMap containing the NVIDIA Device Plugin configuration files. It must be equal to the value "devicePlugin.config.name" of the Helm chart used for deploying the NVIDIA GPU Operator. |
| gpuPartitioner.devicePlugin.config.namespace | string | `"nebuly-nvidia"` | Namespace of the ConfigMap containing the NVIDIA Device Plugin configuration files. It must be equal to the namespace where the Nebuly NVIDIA Device Plugin has been deployed to. |
| gpuPartitioner.devicePlugin.configUpdateDelaySeconds | int | `5` | Duration of the delay between when the new partitioning config is computed and when it is sent to the NVIDIA device plugin. Since the config is provided to the plugin as a mounted ConfigMap, this delay is required to ensure that the updated ConfigMap is propagated to the mounted volume. |
| gpuPartitioner.scheduler.config.name | string | `"nos-scheduler-config"` | Name of the ConfigMap containing the k8s scheduler configuration file. If not specified or the ConfigMap does not exist, the GPU partitioner will use the default k8s scheduler profile. |
| gpuPartitioner.image.repository | string | `"ghcr.io/nebuly-ai/nos-gpu-partitioner"` | Sets the GPU Partitioner Docker image. |
| gpuPartitioner.image.pullPolicy | string | `"IfNotPresent"` | Sets the GPU Partitioner Docker image pull policy. |
| gpuPartitioner.image.tag | string | `""` | Overrides the GPU Partitioner image tag whose default is the chart appVersion. |
| gpuPartitioner.migAgent | object | - | Configuration of the MIG Agent component of the GPU Partitioner. |
| gpuPartitioner.migAgent.reportConfigIntervalSeconds | int | `10` | Interval at which the mig-agent will report to k8s the MIG partitioning status of the GPUs of the Node |
| gpuPartitioner.migAgent.logLevel | int | `0` | The level of log of the MIG Agent. Zero corresponds to `info`, while values greater or equal than 1 corresponds to higher debug levels. **Must be >= 0**. |
| gpuPartitioner.migAgent.image.repository | string | `"ghcr.io/nebuly-ai/nos-mig-agent"` | Sets the MIG Agent Docker image. |
| gpuPartitioner.migAgent.image.pullPolicy | string | `"IfNotPresent"` | Sets the MIG Agent Docker image pull policy. |
| gpuPartitioner.migAgent.image.tag | string | `""` | Overrides the MIG Agent image tag whose default is the chart appVersion. |
| gpuPartitioner.migAgent.resources | object | `{"limits":{"cpu":"100m","memory":"128Mi"}}` | Sets the resource requests and limits of the MIG Agent container. |
| gpuPartitioner.migAgent.tolerations | list | `[{"effect":"NoSchedule","key":"kubernetes.azure.com/scalesetpriority","operator":"Equal","value":"spot"}]` | Sets the tolerations of the MIG Agent Pod. |
| gpuPartitioner.gpuAgent | object | - | Configuration of the GPU Agent component of the GPU Partitioner. |
| gpuPartitioner.gpuAgent.reportConfigIntervalSeconds | int | `10` | Interval at which the mig-agent will report to k8s status of the GPUs of the Node |
| gpuPartitioner.gpuAgent.logLevel | int | `0` | The level of log of the GPU Agent. Zero corresponds to `info`, while values greater or equal than 1 corresponds to higher debug levels. **Must be >= 0**. |
| gpuPartitioner.gpuAgent.runtimeClassName | string | `nil` | The container runtime class name to use for the GPU Agent container. |
| gpuPartitioner.gpuAgent.image.repository | string | `"ghcr.io/nebuly-ai/nos-gpu-agent"` | Sets the GPU Agent Docker image. |
| gpuPartitioner.gpuAgent.image.pullPolicy | string | `"IfNotPresent"` | Sets the GPU Agent Docker image pull policy. |
| gpuPartitioner.gpuAgent.image.tag | string | `""` | Overrides the GPU Agent image tag whose default is the chart appVersion. |
| gpuPartitioner.gpuAgent.resources | object | `{"limits":{"cpu":"100m","memory":"128Mi"}}` | Sets the resource requests and limits of the GPU Agent container. |
| gpuPartitioner.gpuAgent.tolerations | list | `[{"effect":"NoSchedule","key":"kubernetes.azure.com/scalesetpriority","operator":"Equal","value":"spot"}]` | Sets the tolerations of the GPU Agent Pod. |
| gpuPartitioner.kubeRbacProxy | object | - | Configuration of the [Kube RBAC Proxy](https://github.com/brancz/kube-rbac-proxy), which runs as sidecar of all the GPU Partitioner components Pods. |
| gpuPartitioner.batchWindowTimeoutSeconds | int | `60` | Timeout of the window used by the GPU partitioner for batching pending Pods.  Higher values make the GPU partitioner will potentially take into account more pending Pods when deciding the GPU partitioning plan, but the partitioning will be performed less frequently |
| gpuPartitioner.batchWindowIdleSeconds | int | `10` | Idle seconds before the GPU partitioner processes the current batch if no new pending Pods are created, and the timeout has not been reached.  Higher values make the GPU partitioner will potentially take into account more pending Pods when deciding the GPU partitioning plan, but the partitioning will be performed less frequently |
| gpuPartitioner.leaderElection.enabled | bool | `true` | Enables/Disables the leader election of the GPU Partitioner controller manager. |
| gpuPartitioner.podSecurityContext | object | `{"runAsNonRoot":true,"runAsUser":1000}` | Sets the security context of the GPU partitioner Pod. |
| gpuPartitioner.resources | object | `{"limits":{"cpu":"500m","memory":"128Mi"},"requests":{"cpu":"10m","memory":"64Mi"}}` | Sets the resource limits and requests of the GPU partitioner container. |
| gpuPartitioner.podAnnotations | object | `{}` | Sets the annotations of the GPU Partitioner Pod. |
| gpuPartitioner.tolerations | list | `[]` | Sets the tolerations of the GPU Partitioner Pod. |
| gpuPartitioner.affinity | object | `{}` | Sets the affinity config of the GPU Partitioner Pod. |
| gpuPartitioner.nodeSelector | object | `{}` | Sets the nodeSelector config of the GPU Partitioner Pod. |
| gpuPartitioner.knownMigGeometries | list | - | List that associates GPU models to the respective allowed MIG configurations |
