# Uptime Kuma Helm Chart

This Helm chart deploys Uptime Kuma, a self-hosted monitoring tool that allows you to monitor the uptime and performance of your websites, services, and infrastructure. It provides a user-friendly dashboard to visualize the status of your monitored targets and sends notifications when downtime or performance issues are detected.

## Features

- Monitor websites, APIs, servers, and other network services
- Customizable monitoring intervals and timeouts
- Receive notifications via various channels (e.g., email, Slack, SMS)
- Detailed uptime reports and statistics
- User-friendly web interface for managing monitored targets
- Lightweight and easy to deploy using Helm

## Prerequisites

- Kubernetes cluster
- Helm v3+

## Installation

To install the Uptime Kuma Helm chart, follow these steps:

1. Clone the Uptime Kuma Helm chart repository and navigate to the cloned repo:

   ```bash
   git clone https://github.com/sharjeelaziz/uptimekuma.git
   cd uptimekuma
   ```

1. Update the `values.yaml` file with your desired configuration. You can modify various settings such as the number of replicas, image repository and tag, ingress settings, and persistence options (storageClassName). Save the changes.

1. Deploy the Uptime Kuma Helm chart using the following command:

   ```bash
   helm upgrade uptimekuma charts/uptimekuma/ --wait --install --namespace uptimekuma --create-namespace
   ```

    This command upgrades or installs the `uptimekuma` release using the Helm chart located in the `charts/uptimekuma/` directory. It waits for the deployment to complete, creates the `uptimekuma` namespace if it doesn't exist, and installs the chart in that namespace.

## Configuration

The Uptime Kuma Helm chart provides various configuration options that can be customized by modifying the `values.yaml` file. Some commonly used configuration options include:

- `image.repository`: Docker image repository for Uptime Kuma
- `image.tag`: Docker image tag for Uptime Kuma
- `ingress.enabled`: Enable or disable Ingress for external access and update according to your environment.
- `storageClassName`: Set according to your environment

For a complete list of configuration options and their descriptions, please refer to the `values.yaml` file.

## Uninstallation

To uninstall the Uptime Kuma Helm chart, use the following command:

```bash
helm uninstall uptimekuma -n uptimekuma
```

This command removes the `uptimekuma` release from the `uptimekuma` namespace.

This deployment is running on a baremetal [k8s cluster](https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/create-cluster-kubeadm/) with [OpenEBS](https://openebs.io/) for persistence, [MetalLB](https://metallb.universe.tf/) for LoadBalancer, [cert-manager](https://cert-manager.io/) for TLS certs, [external-dns](https://github.com/kubernetes-sigs/external-dns) for automatic creation of DNS records configured for [CloudFlare](https://www.cloudflare.com/), and [ingress-nginx](https://kubernetes.github.io/ingress-nginx/deploy/) for ingress.
