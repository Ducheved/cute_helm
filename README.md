# Cute Helm

Cute Helm is a Helm chart for testing ArgoCD in an environment where Traefik and MetalLB are installed.

**Note:** This file is intended for learning purposes and is not recommended for use in other contexts.

## Overview

This Helm chart deploys the following:

- A Deployment running the `ducheved/cmconstructor` Docker image.
- An Ingress resource configured to route traffic to the deployed application.
- A Role and RoleBinding for RBAC.
- A Service to expose the application within the cluster.

## Configuration

The following table lists the configurable parameters of the Cute Helm chart and their default values.

| Parameter                | Description                                     | Default                        |
|--------------------------|-------------------------------------------------|--------------------------------|
| `fullnameOverride`      | Overrides the full name of the resources        | `""`                           |
| `replicaCount`          | Sets the number of replicas                     | `1`                            |
| `host`                  | Sets the hostname for the ingress resource      | `"meow.lemon"`                 |
| `namespace`             | Sets the namespace where the resources are deployed | `default`                  |
| `image.repository`      | Sets the Docker image repository                | `ducheved/cmconstructor`       |
| `image.pullPolicy`      | Sets the Docker image pull policy               | `IfNotPresent`                 |
| `image.tag`             | Sets the Docker image tag                       | `"under"`                      |
| `service.type`          | Sets the Kubernetes Service type                | `LoadBalancer`                 |
| `service.port`          | Sets the Service port                           | `39531`                        |
| `service.targetPort`    | Sets the target port of the application         | `3000`                         |
| `ingressRoute.enabled`  | Enables the ingress route                       | `true`                         |
| `ingressRoute.tls.certResolver` | Sets the cert resolver for the ingress route | `default`                   |
| `ingressRoute.entryPoints` | Sets the entry points for the ingress route  | `["websecure"]`                |
| `ingressRoute.routes.match` | Sets the match rule for the ingress route   | `Host(`meow.lemon`)`           |
| `ingressRoute.routes.priority` | Sets the priority for the ingress route  | `10`                           |
| `ingressRoute.routes.services.port` | Sets the Service port for the ingress route | `80`                      |
| `ingressRoute.routes.services.scheme` | Sets the scheme for the ingress route | `h2c`                       |
| `resources`             | Sets the CPU/Memory resource requests/limits    | `{}`                           |