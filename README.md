# Fluent Bit log shipping from Kuberentes (AKS etc.) to Azure Data Explorer

This repo contains updated Kubernetes manifests that allow Fluent Bit to parse containerd/CRI formatted logs and ship them to Event Hub, from where they can be [ingested into Azure Data Explorer](https://github.com/Azure/azure-kusto-labs/tree/master/k8s-container-log-analytics), based on https://github.com/microsoft/fluentbit-containerd-cri-o-json-log.

The files `fluent-bit-ds.yaml` and `fluent-bit-configmap.yaml` can be used as drop-in replacement for the outdated files provided at https://github.com/Azure/azure-kusto-labs/tree/master/k8s-container-log-analytics/fluent-bit/k8s-container-logs/conf. Other than that, follow the steps described in this lab to set up your log shipping solution from AKS (or any other Kubernetes cluster) to ADX.

Make sure to set

- `YOUR_AZURE_EVENT_HUB_NAMESPACE`
- `YOUR_AZURE_EVENT_HUB`
- `YOUR_AZURE_EVENT_HUB_NAMESPACE_PRIMARY_CONNECTION_STRING`

in `fluent-bit-configmap.yaml` before deploying to your cluster.

`fluent-bit-configmap-debug.yaml` can be used to play around with and understand the Fluent Bit config--it just dumps all logs to stdout.
