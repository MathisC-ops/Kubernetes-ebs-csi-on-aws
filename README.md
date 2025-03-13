# Kubernetes-ebs-csi-on-aws

This project provides the necessary resources to create and manage an Amazon EBS volume with a pod in your kubernetes cluster. You can find some kube manifest example and the iam policy for make in place this project.

## Project Structure

- **Kubernetes-manifest** : Folder with all kube manifest for the kubernetes resources.
- **Resources** : All externe, ccopy or alternative file for the projet.
- **IAM_policy** : The policy that grants the required permissions to manage the EC2 and the external EBS place on it.

## Changes Variables

- **In pod.yaml** :
```shell
claimName: $PVC_NAME
```

- **In pvc.yaml** :
```shell
name: $PVC_NAME
storageClassName: $STORAGECLASS_NAME
```

- **In StorageClass.yaml** :
```shell
storageClassName: $STORAGECLASS_NAME
```

## Requierement

- You need to have install the EBS driver plugin before (AWS Add-ons | HELM)
- Have Permissions to manage AWS CLI, IAM policy, EC2 ressources, Kubernetes resources

## Command Sheet

Some command to manage EBS and kubernetes resources.

- **Kubernetes** :
```shell
kubectl describe pod $POD_NAME           #Check the description of the pod for see the pv, pvc mount
kubectl exec -it ebs-test-pod -- df -h   #Check the mountpoint in the pod directly
```
- **AWS** :
```shell
aws ec2 describe-volumes --profile MY_PROFILE --region $MY_REGION
```


