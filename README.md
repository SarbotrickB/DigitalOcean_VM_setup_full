# DigitalOcean_VM_setup_full
Setting up a Kubernetes cluster with a Docker registry on a single DigitalOcean VM, using Ansible to automate the process. This approach will install Kubernetes on the VM, set up Docker as the container runtime, deploy a Docker registry, and then add a sample application from the developer's code to the registry.

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

## registry.yml
 A Docker registry within the Kubernetes cluster and expose it as a service.

## app-deployment.yml
A Kubernetes manifest for the application deployment using the image in the registry.

## Run the Playbook
Update the developer_app_path variable in the playbook to point to the directory containing the developer's Dockerfile and application code.
Run the playbook:
```
ansible-playbook -i inventory.ini playbook.yml
```

## Summary of Workflow
This setup allows the Kubernetes cluster on a single VM to host a Docker registry, push images, and deploy applications. 

Please let me know if you need further customization.
