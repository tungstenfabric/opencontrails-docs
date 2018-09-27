https://tinyurl.com/yb5b5fza

**NOTE**: Always open URLs in a new tab or window

# 1. Deploying Tungsten Fabric

### 1.1. Where is Tungsten Fabric

URL #1: https://hub.docker.com/u/opencontrailnightly/

### 1.2. TF + Kubernetes in AWS

One easy (but not free) way to get started is by running a cluster on AWS with Kubernetes and Tungsten fabric.

There are many ways to get started and a decent one that works right now is:

URL #2: https://tungstenfabric.github.io/website/Tungsten-Fabric-15-minute-deployment-with-k8s-on-AWS.html

It is difficult to reverse engineer and to maintain and well... it may break in the future but don't worry, there are other similar approaches such as (although it says Contrail it's actually Tungsten Fabric):

URL #3: https://github.com/Juniper/contrail-ansible-deployer/wiki/Deployment-Example:-Click-On-Deployment-of-Contrail-and-Kubernetes-in-AWS

All these procedures rely on an instances.yaml file that defines the cluster. For example the latter procedure uses the following instances.yaml file.

URL #4: https://s3.eu-west-2.amazonaws.com/contrail-k8s-workshop/aws-k8s-config.yaml

### 1.3. TF + Kubernetes + Openstack On Prem

This procedure works perfectly fine and you can easily adapt it to any environment. In this case the very same TF cluster is integrated with both a Kubernetes cluster and an Openstack cluster.

URL #4: https://github.com/Juniper/contrail-ansible-deployer/wiki/Deployment-Example%3A-Contrail-and-Kubernetes-and-Openstack



# 2. Using TF
# 3. Building TF
# 4. Debugging TF

