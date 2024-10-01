## Kubernetes Orchestration

- CLUSTER = node + master
- MINIKUBE / DOCKER DESKTOP = managing the virtual machines (cluster)
- KUBECTL = command line tool to interact with k8s cluster

### Features

- HIGH AVAILABILITY / no downtime
- SCALABILITY / high performance
- DISASTER RECOVERY / backup & restore
- LOAD BALANCING / distributing traffic
- HEALTH CHECKS / checking state of container

### Components / Object Types

- POD / a group of one or more containers
- SERVICE / allows for network communication between pods
- DEPLOYMENTS / manage a set of identical pods
- INGRESS / route traffic into cluster from outside(world)
- CONFIGMAP & SECRETS / stores environment & secret variables
- VOLUMES / stores persistent data (PVC)

<!-- ingress => service => pod -->

### Service Types

- ClusterIp / Exposes a service that can only be accessed from inside
- NodePort / Exposes a service through a static port from outside
- LoadBalancer / Exposes a service through the cloud provider's load balancer

### 4 Master Processes - master (we always work with master)

- API SERVER / acts as the gateway for the cluster and handles requests from both inside and outside the cluster.
- SCHEDULER / decides on which node new pod should be scheduled
- CONTROLLER MANAGER / detects cluster state changes and take action
- ETCD / stores the cluster's state and configuration data

### 3 Node Processes - node (master give commands to node)

- CONTAINER RUNTIME / responsible for running containers i.e docker
- KUBELET / makes sure that containers are running in a pod
- KUBE PROXY / forwards the requests (network proxy)

### Commands

**01 - SHOW STATUS (COMPONENTS)**

```bash
kubectl get nodes
kubectl get pods
kubectl get services
kubectl get deployments
kubectl get replicasets
kubectl get namespaces
kubectl get secrets
kubectl get all
```

**02 - SINGLE CONFIGURATION**

```bash
kubectl apply -f <config.yaml>
kubectl delete -f <config.yaml>
```

**03 - ALL CONFIGURATION**

```bash
kubectl apply -f .
kubectl delete all --all
```

**04 - PODS**

```bash
kubectl delete pod <pod-name>
kubectl logs <pod-name>
kubectl exec -it <pod-name> -- bin/bash
kubectl describe pod <pod-name>
```

**05 - DEPLOYMENTS**

```bash
kubectl create deployment <deploy-name> --image=<image>
kubectl edit deployment <deploy-name>
kubectl delete deployment <deploy-name>
```

**06 - SECRETS**

```bash
kubectl create secret generic <secret-name> --from-literal <key>=<value>
kubectl get secrets <secret-name> -o yaml
echo <encoded-value> | base64 -d
```
