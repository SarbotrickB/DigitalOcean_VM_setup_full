# DigitalOcean_VM_setup_full
Setting up a single VM that will act as a simple cluster and host a Docker registry for deploying the developer's code.

## playbook.yml
###  Docker Installation: 
Ensures Docker is installed and running.
### Swarm Initialization: 
Initializes Docker Swarm on a single VM, effectively setting up a single-node cluster.
### Registry Setup: 
Sets up the registry as a Docker service, exposing it on port 5000.
### Verification: 
Checks that the registry is accessible on http://localhost:5000.

## inventory.ini
Define the VM as the Ansible host.

## Run the Playbook
```
ansible-playbook -i inventory.ini playbook.yml
```
## Deploy Code into the Registry
### Build and Tag Image: 
```
docker build -t <your_vm_ip>:5000/<image_name>:<tag> .
```
### Push the Image: 
```
docker push <your_vm_ip>:5000/<image_name>:<tag>
```

## Summary:
Inventory and Ansible Playbook: Specifies VM setup.
Docker and Docker Swarm: Installs Docker and configures it as a single-node Swarm.
Registry Setup: Runs the Docker registry as a service in the Swarm.
Push Code: Allows developers to push code (Docker images) to the registry.
This setup will create a simplified, single-node cluster with a Docker registry ready to deploy and store the developer's containerized applications. 

Let me know if you'd like to add any additional configurations!
