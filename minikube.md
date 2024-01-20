
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




## Install bash completion for the suggestion in kubernetes

```

apt-get install bash-completion

echo $SHELL


kubectl completion bash

kubectl completion bash > kubecom.sh

cat kubecom.sh 

cp kubecom.sh /home/user/.kube/

source $HOME/.kube/kubecom.sh



# Open profile and pasted the commands
sudo vim .profile
 
source $HOME/.kube/kubecom.sh
```



### Create pod.

```
kubectl run firstpod --image=coolgourav147/nginx-custom
```

### check the list of pod.

```
kubectl get pod

kubectl get pods

kubectl get po

kubectl get rc

# Note: By the help of get commands you can see the list of pods,namespace,etc.
```



### Now, Let’s check the details of the pods list.
```
kubectl get po -o wide
```


### Now, check the pod's details in yaml format.
```
kubectl get po -o yaml 
```

### Now, check the pod’s details in json format.
```
kubectl get po -o json
```


### Explain the pods details.

```

kubectl explain pods
# KIND:       Pod
# VERSION:    v1
```

### Describe the pod details. 
```
kubectl describe pod firstpod
```

### Watch the pod's details.
```
kubectl get pod -w
```

### Delete the container. 

```
sudo docker container ls

sudo docker container rm -f a77ad096e319

```

### Delete the pods.

```
kubectl delete pod firstpod
```

### Assign the label in pods.
```
kubectl label pod firstpod env=testing
```

### Now, Check the label in pods.

```
kubectl describe pod firstpod 

#Name:             firstpod
Namespace:        default
Priority:         0
Service Account:  default
Node:             minikube/192.168.39.100
Start Time:       Fri, 19 Jan 2024 04:59:55 +0530
Labels:           env=testing
                  run=firstpod
Annotations:      <none>
Status:           Running
IP:               10.244.0.15
IPs:
  IP:  10.244.0.15

```

### Set the label prod of pods.

```
kubectl label --overwrite pod firstpod env=prod

# Name:             firstpod
Namespace:        default
Priority:         0
Service Account:  default
Node:             minikube/192.168.39.100
Start Time:       Fri, 19 Jan 2024 04:59:55 +0530
Labels:           env=prod
                  run=firstpod
Annotations:      <none>
Status:           Running
IP:               10.244.0.15

```


### Delete the labels of pods.

```
kubectl label pod --all status=rahul
```

### Check the status of labels.

```
kubectl describe pod firstpod 
```

### Now, Check the labels of all pods.

```
kubectl get pods --show-labels
```

### Delete the all pods

```
kubectl delete pods --all
```



## Create First YAML for Kubernetes Resource, kubectl create, kubectl apply.


```
# Create the yaml file.

# Vim frirstpod.yaml

apiVersion: v1
kind: Pod


metadata:
  name: myfristpod
  labels: 
    env: prod


spec:
  containers:
    - name: rahul
      image: coolgourav147/nginx-custom
```


```
# Now, Create the pod
 kubectl create -f first-pod.yaml

# Now, check the pod list.
kubectl get pods

NAME         READY   STATUS    RESTARTS   AGE
myfristpod   1/1     Running   0          55s
```










