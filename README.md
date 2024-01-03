# Minio Cluster 

## Purpose
It's a simple and fast way to deploy your own Minio cluster with any number of nodes to get your own S3-compatible storage. When using Minio as a cluster, it increases the reliability of your Minio installation and allows you to combine several servers into a single storage system. Atop this cluster sits a Caddy server, serving as a proxy for balancing, health checks, and TLS termination.

## Installation
The installation uses Docker and Docker Compose to run the cluster, and Ansible roles are provided for installing these as dependencies (currently supports Debian like OS only).
Clone the repository, navigate to the ansible directory, and update the `vars/main.yml` file with your specific values.

Let’s take a closer look at the variables:
- `minio_path`: The directory on each server where all configurations and data will be stored. This includes the './data' directory as a mounted volume.
- `minio_image`: The Docker image of Minio. You can choose a different release from the Docker Hub.
- `minio_user`: The admin user for Minio.
- `minio_password`: The admin user's password for Minio.
- `minio_proxy_path`: The directory on the node with the Caddy proxy server.
- `minio_proxy_domain`: The domain for Minio's admin web UI and as the parent domain for the API (`api.${'minio_proxy_domain'}`).

Make sure you configure your `api.${'minio_proxy_domain'}` and `${'minio_proxy_domain'}` with IP address of Minio proxy server.
