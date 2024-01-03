# Minio Cluster 

## Configuration
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

Update `inventory/hosts.ini` with IP addresses of nodes. Also update `ansible_host` with values from ssh config if you use it. Do the same for proxy node where Caddy server will be installed. It would by entry point for all traffic and TLS termination for Admin panel and API domains.

## Installation

Run Ansible playbook:
```bash
ansible-playbook playbook.yml -i inventory/hosts.ini
```
