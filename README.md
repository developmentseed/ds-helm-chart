# DS-helm-charts


The ds-helm-chart repository serves as a comprehensive collection of Helm charts tailored for seamless deployments on Kubernetes clusters (https://github.com/developmentseed/ds-k8s-gpu), this repository includes configurations. for a variety of services, such as Jupyter Notebooks and the Segment Anything Model(#TODO). By utilizing specific tags (nodegroup_type) within the values file, users can effortlessly allocate different GPU resources for their machine learning experiments.

This project addresses the current challenge of easily accessing GPU instances and setting up a Jupyter Notebook. The aim is to create Helm charts that facilitate the easy configuration of services, allowing access to various GPUs directly from a Jupyter Notebook or for deploying other applications.


An important point to consider is that the [cluster](https://github.com/developmentseed/ds-k8s-gpu) operates with an autoscaler. This means you don't have to worry about the cost of GPUs, as the system will automatically adjust resources. However, please note that once you've completed your work, you should remove your Helm installation to prevent unnecessary GPU resource demand.


Before installing ds-helm-chart, it's essential to properly configure your Kubernetes cluster. Once that is done, you can proceed with the installation of the Helm chart package.

Note: If you did not create the cluster yourself, you will need to request access from the cluster administrator to associate your AWS account with the cluster.

## Prerequisites

- 1. Have an AWS account set up and ready to use.
- 2. Have the eksctl(optional), kubectl, and helm command-line tools installed.

# Installing Helm Charts

Before executing the installation of the Helm charts, you have the option to modify the values.yaml file. This will allow you to specify which Docker image you wish to run on the cluster and whether you require a persistent disk. *More details on this topic will be provided soon.*

```sh
# Get cluster credentials
aws eks update-kubeconfig --region ${AWS_REGION} --name ${CLUSTER_NAME}
kubectl cluster-info

git clone https://github.com/developmentseed/ds-helm-chart.git
cd ds-helm-chart/
helm upgrade --install <relese_name> .
# e.g: helm upgrade --install staging .
```

```sh
kubectl get nodes -L nodegroup_type
```


