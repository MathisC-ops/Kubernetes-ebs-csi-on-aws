# Kubernetes-ebs-csi-on-aws

This project provides the necessary resources to create and manage an Amazon EBS volume with a pod in your Kubernetes cluster. You can find some kube manifest example and the IAM policy for make in place this project.

## Project Structure

- **kubernetes-manifest** : Folder containing all kube manifest for the kubernetes resources.
- **resources** : All externe, copied or alternative files for the projet.
- **iam_policy** : The policy that grants the required permissions to manage the EC2 and EBS.

## Variables

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

## Requirements

- You must install the EBS driver plugin before (AWS Add-ons | HELM)
- Have Permissions to manage AWS CLI, IAM policy, EC2 resources, Kubernetes resources

## Command Sheet

Some command to manage EBS and kubernetes resources.

- **Kubernetes** :
```shell
kubectl describe pod $POD_NAME           #Check the description of the pod to see the pv, pvc mount
kubectl exec -it ebs-test-pod -- df -h   #Check the mountpoint inside the pod
```
- **AWS** :
```shell
aws ec2 describe-volumes --profile MY_PROFILE --region $MY_REGION
```


