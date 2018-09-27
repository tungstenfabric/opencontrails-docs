You can access this page also through the following shortcut: https://tinyurl.com/yb5b5fza

**Always open URLs in a new tab or window**

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

URL #5: https://github.com/Juniper/contrail-ansible-deployer/wiki/Deployment-Example%3A-Contrail-and-Kubernetes-and-Openstack

# 2. Using TF

# 2.1. Playing with the TF + Kubernetes integration

For the record there is a complete guide here but do **NOT** follow it here.

URL #6: https://s3.eu-west-2.amazonaws.com/contrail-k8s-workshop/contrail-50-kubernetes-aws-cloudformation-openlab.docx

You are going to do some basic experiments in a shared test. Here are the resulting VMs after applying that procedure on URL #2 plus some VM renaming and after adding root password access:

K8s Master + Controller: ssh root@18.130.5.116 / tungsten123
K8s Compute #1: ssh root@3.8.16.209 / tungsten123
K8s Compute #2: ssh root@3.8.16.108 / tungsten123

All the following commands are to be executed on the controller and let's start with a very existential question. What is your nickname? OK whatever your nickname is (and make sure it's not Joe or Phil but something more unique) it becomes <your_name> from now on.

Use your super-advanced linux skills to create a file called <your_name>.yml and add the following content, making sure you replace <your_name> appropriately:

```apiVersion: v1
kind: Namespace
metadata:
 name: "<your_name>"
 annotations: {
       "opencontrail.org/isolation" : "true",
 }´´´

The instructor is also going

# 3. Building TF
# 4. Debugging TF

