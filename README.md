# DigitalOcean_VM_setup_full
Setting up a single VM that will act as a simple cluster and host a Docker registry for deploying the developer's code.

## playbook.yml
### Docker and Kubernetes Installation: 
Installs Docker and Kubernetes on the VM.
### Kubernetes Cluster Initialization: 
Sets up a single-node Kubernetes cluster with kubeadm.
### Flannel Network Plugin: 
Adds network support using Flannel for pod communication.
### Docker Registry Deployment: 
Deploys a Docker registry inside the Kubernetes cluster.
### Application Build and Push: 
Builds the developer's application and pushes it to the registry.
### Application Deployment: 
Deploys the application using the image stored in the registry.

## inventory.ini
Define the VM as the Ansible host.

## Run the Playbook
```
ansible-playbook -i inventory.ini playbook.yml
```
## Deploy Code into the Registry
### Build and Tag Image: 
```
docker build -t <vm_ip>:5000/<image_name>:<tag> .
```
### Push the Image: 
```
docker push <vm_ip>:5000/<image_name>:<tag>
```

## Summary:
Inventory and Ansible Playbook: Specifies VM setup.
Docker and Docker Swarm: Installs Docker and configures it as a single-node Swarm.
Registry Setup: Runs the Docker registry as a service in the Swarm.
Push Code: Allows developers to push code (Docker images) to the registry.
This setup will create a simplified, single-node cluster with a Docker registry ready to deploy and store the developer's containerized applications. 

Let me know if you'd like to add any additional configurations!
