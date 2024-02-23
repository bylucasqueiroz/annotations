1. [Kubectl](#kubectl)
	1. [Configs](#configs)
	2. [Pods](#pods)
	3. [Storage Class](#StorageClass)
	4. [Namespaces](#namespaces)
	5. [Logs](#logs)
	6. [Deployment](#deployment)
	7. [Service Account](#ServiceAccount)
	8. [Persistent Volume](#PersistentVolume)
	9. [Persistent Volume Claim](#PersistentVolumeClaim)
	10. [Force Delete](#ForceDelete)
	11. [Nodes](#nodes)
	12. [DaemonSet](#DaemonSet)
	13. [HPA](#hpa)
	14. [Events](#events)
2. [AWS Configuration](#configuration)
## Kubectl
### Configs
___
#### Get contexts

```bash
kubectl config get-contexts
```
#### Change context

```bash
kubectl config use-context (CONTEXT_NAME)
```
#### Get current context

```bash
kubectl config current-context
```

### Pods
___
#### Get Pods

```bash
kubectl -n (NAMESPACE) get pods
```
#### Get Pods and Details

```bash
kubectl -n (NAMESPACE) get pods -o wide
```
#### Describe Pods

```bash
kubectl -n (NAMESPACE) describe pods (POD_NAME)
```
#### Describe Pod

```bash
kubectl -n (NAMESPACE) describe pod (POD_NAME)
```
#### Delete Pod

``` bash
kubectl -n (NAMESPACE) delete pod (POD_NAME)
```
#### Restart the pods managed by the specified deployment

``` bash
kubectl -n (NAMESPACE) rollout restart deploy (DEPLOY_NAME)
```

### StorageClass
___
#### Get storage class no Kubernetes

```bash
kubectl get storageclass
```

### Namespaces
___
#### Get all namespaces

```bash
kubectl get ns -A
```

### Logs
___
#### Get logs from Pods

```bash
kubectl -n (NAMESPACE) logs -f (POD_NAME)
```
#### Get detailed logs from Pods

``` bash
kubectl --v=8 logs -n (NAMESPACE) (POD_NAME) --all-containers=true
```
#### Pod Container Access

``` bash
kubectl -n (NAMESPACE) exec -it (POD_NAME) -- sh
```
#### List containers inside the Pod

``` bash
ctr -n kis.io containers list
```

### Deployment
___
#### Return the image name of the first container defined in the specified deployment

``` bash
kubectl -n (NAMESPACE) get deployment (DEPLOYMENT_NAME) -o=jsonpath=' ($-spef.template spec-containers :11. image}'
```
#### Deployment Rollout

``` bash
kubectl -n (NAMESPACE) rollout restart deploy (DEPLOYMENT_NAME)
```
#### Deployment zero replicas

``` bash
kubectl -n (NAMESPACE) scale deployments/(DEPLOYMENT_NAME) --replicas=0
```
### ServiceAccount
___
#### Get Service Account

``` bash
kubectl -n (NAMESPACE) get serviceaccount
```
#### Describe Service Account

``` bash
kubectl -n (NAMESPACE) describe serviceaccount (SERVICE_ACCOUNT_NAME)
```

### PersistentVolume
___
#### Get Persistent Volume

``` bash
kubectl -n (NAMESPACE) get pv
```
#### Describe Persistent Volume

```bash
kubectl -n (NAMESPACE) describe pv (PV_NAME)
```
### Edit Persistent Volume

``` bash
kubectl -n (NAMESPACE) edit pv (PVC_NAME)
```
### Get all Persistent Volume

```bash
kubectl -n (NAMESPACE) get pv -A
```
#### Get all Persistent Volume

```bash
kubectl -n (NAMESPACE) edit pv -A
```
#### Delete Persistent Volume

``` bash
kubectl -n (NAMESPACE) delete pv (PV_NAME)
```

### PersistentVolumeClaim
___
#### Get Persistent Volume Claim

``` bash
kubectl -n (NAMESPACE) get pvc
```
#### Describe Persistent Volume Claim

``` bash
kubectl -n (NAMESPACE) describe pvc (PVC_NAME)
```
#### Edit Persistent Volume Claim

``` bash
kubectl -n (NAMESPACE) edit pvc (PVC_NAME)
```
#### Get all Persistent Volume Claim

```bash
kubectl -n (NAMESPACE) get pvc -A
```
#### Get all Persistent Volume Claim

```bash
kubectl -n (NAMESPACE) edit pvc -A
```
### Delete Persistent Volume Claim

``` bash
kubectl -n (NAMESPACE) delete pvc (PVC_NAME)
```

OBS: Attention to delete a Persistent Volume Claim: [Delete with Protection](https://kubernetes.io/docs/concepts/storage/persistent-volumes)
### ForceDelete
___
``` bash
--grace-period=0 --force
```

### Nodes
___
#### Get Nodes

``` bash
kubectl get nodes
```
#### Describe Node 

```
kubectl describe node (NODE_NAME)
```
#### Get node ordered by usage

``` bash
kubectl top nodes
```

### DaemonSet
___
#### Get Daemon

```bash
kubectl -n (NAMESPACE) get ds
```
#### Edit Daemon

```bash
kubectl -n (NAMESPACE) edit ds (DS_NAME)
```

### HPA
___
#### Get HPA

``` bash
kubectl get hpa -n (NAMESPACE)
```
### Events
___
#### Get Events

``` bash
kubectl get events
```
### Set Sleep to Container

Update a deployment, and insert the follow line: `comand: ["sleep"]`

## Initial AWS Configuration
### Configuration
___
#### Connect using SSO

``` bash
aws configure sso --profile (PROFILE)
```
#### Configure STS

``` bash
aws sts get-caller-identity --profile (PROFILE)
```
#### List AWS Clusters

``` bash
aws eks list-clusters --profile (PROFILE)
```
#### Update kubecofing

```bash
aws eks --region sa-east-1 update-kubeconfig --name (CLUSTER_NAME) --profile (PROFILE)
```