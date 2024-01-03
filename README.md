# Minio Cluster 

## Purpose
It's a simple and fast way to deploy your own Minio cluster with any number of nodes to get your own S3-compatible storage. When using Minio as a cluster, it increases the reliability of your Minio installation and allows you to combine several servers into a single storage system. Atop this cluster sits a Caddy server, serving as a proxy for balancing, health checks, and TLS termination.

## Ansible
Ansible playbook to initial configuration of servers in cluster, install all dependencies (Docker and Docker Compose) and install and configure Minio cluster and proxy server with Caddy for it. 

**[Ansible](./ansible)**
