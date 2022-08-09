
# RDFox Helm Chart for Kubernetes

This helm chart will deploy a statefulset of RDFox instances.

## Prerequisites

You will need a `RDFOX.lic` license file.

## Installation

Install the helm chart repository:

```bash
helm repo add rdfox https://sintef.github.io/rdfox-helm-chart
```

Create a secret from the license:
```bash
kubectl create secret generic rdfox-license --from-file=RDFox.lic
```

Install the chart:
```bash
helm install rdfox rdfox/rdfox
```

## Configuration

| Property | Description | Default |
| -------- | ----------- | ------- |
| `replicaCount` | The number of replicas | `1` |
| `storageClass` | The storage class | `""` (default storage class) |
| `storageSize` | The storage size | `4Gi` |
| `maxMemory` | The maximum memory use in MB | `null` (all the RAM of the node) |
| `numThreads` | The maximum number of threads | `null` (the number of cores of the node) |
| `credentials.role` | The role (username) to use | `"rdfox"` |
| `credentials.password` | The password | `"rdfox"` (override if necessary) |
| `licenseSecretName` | The name of the license secret | `rdfox-license` |
| `image.repository` | The image | `oxfordsemantic/rdfox` |
| `image.tag` | The image tag | `5.6` |
| `initImage.repository` | The image | `oxfordsemantic/rdfox-init` |
| `initImage.tag` | The image tag | `5.6` |
| `ingress` | Ingress settings | *see values.yaml* |
| `resources` | Resources settings | *see values.yaml* |
| `nodeSelector` | Note selector settings | *see values.yaml* |
| `tolerations` | Tolerations settings | *see values.yaml* |
| `affinity` | Affinity settings | *see values.yaml* |