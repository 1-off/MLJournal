
# Installing Kubeflow with Microk8s on Ubuntu

## Prerequisites
- Ubuntu 18.04 or later
- Microk8s installed and running
- Access to a terminal

## Step 1: Install Microk8s

To install Microk8s, run the following command in your terminal:
```
sudo snap install microk8s --classic
```

## Step 2: Enable Required Microk8s Addons

Run the following command to enable the required addons for Kubeflow:
```
microk8s.enable dns storage metrics-server
```

## Step 3: Install Kubeflow

To install Kubeflow, run the following command:
```
microk8s.kubeflow install
```

## Step 4: Verify Installation

To verify the installation, check the status of the Kubeflow pods by running the following command:
```
microk8s.kubectl get pods --namespace kubeflow
```

## Step 5: Accessing Kubeflow

To access the Kubeflow UI, run the following command to get the URL:

```
microk8s.kubectl cluster-info | grep 'Kubernetes master' | awk '/http/ {print $NF}'
```

And then open the URL in a browser, you should now see the Kubeflow UI.

Note:
    This guide is for a single node setup of Kubeflow on Ubuntu using Microk8s.
    If you want to access the UI from your host machine, you will need to forward the port using the command:
```
microk8s.kubectl port-forward -n kubeflow svc/istio-ingressgateway 8080:80
```
 Before you begin, make sure that you have Microk8s installed and running on your system.
    To make sure that all the required Microk8s addons are running, you can use the command microk8s.status.
    Make sure to run all the command as a non-root user with sudo access.
