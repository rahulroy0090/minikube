
## How to setup minikube on ubuntu 22.04

### Step 1: Install Dependencies

```
sudo apt update
sudo apt install -y curl wget apt-transport-https
```

### Step 2: Install Minikube

```
wget https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo cp minikube-linux-amd64 /usr/local/bin/minikube
sudo chmod +x /usr/local/bin/minikube
minikube version
```

###   Step 3: Install kubectl


```
curl -LO https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl
chmod +x kubectl
sudo mv kubectl /usr/local/bin/
kubectl version -o yaml
```

### Step 4: Start Minikube 

```
minikube start
minikube status
```

### Step 5: Verify Kubernetes Cluster


```
kubectl get pods
kubectl cluster-info
kubectl get nodes
```


### Step 6: Check Minikube Addons

```
minikube addons list
```

### Step 7: Access Kubernetes Dashboard

```
minikube dashboard
```





## Install docker on ubuntu 22.04

### Set up Docker's apt repository.

```
# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl gnupg
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg

# Add the repository to Apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```

### Install the Docker packages.

```
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```


### Verify that the Docker Engine installation is successful by running the hello-world image.


```
sudo docker run hello-world
```

### Run the following command to uninstall all conflicting packages:

```
for pkg in docker.io docker-doc docker-compose docker-compose-v2 podman-docker containerd runc; do sudo apt-get remove $pkg; done
```


