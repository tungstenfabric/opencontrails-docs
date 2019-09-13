# Welcome to the Tungsten Fabric Carbide Evaluation Guide (CEG)

## What is this Guide for?

This guide is designed for application developer or a compute infrastructure platform engineer considering their options for Kubernetes networking, with specific focus on [Tungsten Fabric Carbide](https://tungsten.io/start/).

[Kubernetes Cluster Networking](https://kubernetes.io/docs/concepts/cluster-administration/networking/) functions are central to applications running on top of Kubernetes. These functions include:

*   [Network communications between Pods](https://kubernetes.io/docs/concepts/services-networking/connect-applications-service/) through Services;
*   Network communications [between the outside world and externally-facing Services](https://kubernetes.io/docs/concepts/services-networking/ingress/); and
*   [Network policies](https://kubernetes.io/docs/concepts/services-networking/network-policies/) that provide fine-grained control over what network communication flows are allowed.

To do the above, Kubernetes cluster must have a Container Network Interface ("CNI") plugin installed. Kubernetes documentation web site lists [a number of options](https://kubernetes.io/docs/concepts/cluster-administration/networking/#how-to-implement-the-kubernetes-networking-model), Tungsten Fabric being the one we cover in this document.

We will use a sample 3-tier application to go through the three main function areas listed above, and explain what Tungsten Fabric does in each of the cases. Where Tungsten Fabric provides extra functionality beyond Kubernetes baseline, we will also say so.

To follow along with our use cases, you should deploy your own copy of a [Quick Start of Tungsten Fabric ("TF") Carbide with Kubernetes ("K8s") on AWS](https://tungstenfabric.github.io/website/Tungsten-Fabric-15-minute-deployment-with-k8s-on-AWS.html).

## Prerequisites

This guide assumes that you are comfortable with how to:

*   Deploy a CloudFormation template into your AWS account;
*   Connect to an EC2 instance in AWS with an SSH client and SSH private key;
*   Deploy applications to Kubernetes using `kubectl` CLI tool;
*   Use Linux CLI/terminal tools, like `less` and `nano`.

## Introduction to our sample app

To demonstrate how Tungsten Fabric can help us get an application running, accessible from the Internet, and then secured, we will use the mock application called "[yelb](https://github.com/mreferre/yelb)". It was written and is maintained by one of the Developer Advocates at AWS. The reason for choosing this application is that it is simple, [well-documented](https://github.com/mreferre/yelb#yelb-architecture), and is [ready to run on Kubernetes](https://github.com/mreferre/yelb/tree/master/deployments/platformdeployment/Kubernetes).

Please see the "[Yelb Architecture](https://github.com/mreferre/yelb#yelb-architecture)" link for more detail, but at the high level it looks like this:

![alt_text](images/image1.png "image_tooltip")

(Original image URL: [https://github.com/mreferre/yelb/raw/master/yelb-architecture.png](https://github.com/mreferre/yelb/raw/master/yelb-architecture.png))

The application is made of four Deployments:`yelb-ui`, `yelb-appserver`, `yelb-db` and `yelb-cache`. Each Deployment is fronted by a respective Kubernetes Service. The `yelb-ui` Service can also be fronted by Kubernetes Ingress, providing you with L7 HTTP routing.

## Getting ready

For our exercises, we will need to have the following in place:

*   Access to our Kubernetes cluster with Tungsten Fabric through Kubernetes' `kubectl` CLI tool; and
*   A copy of yelb

### Access our Kubernetes cluster

If you followed the steps in [Tungsten Fabric Carbide Quick Start on AWS guide](https://tungstenfabric.github.io/website/Tungsten-Fabric-15-minute-deployment-with-k8s-on-AWS.html), you should be able to log in into your QuickStart sandbox control node as described in the `Accessing the Cluster` section of the guide. To find out the public DNS host name of your sandbox control node, look in the Outputs tab of the AWS CloudFormation UI for the template you used to deploy Kubernetes with Tungsten Fabric Carbide:

![alt_text](images/image10.png "image_tooltip")

Once on the sandbox control node, run:
```bash
sudo -s
kubectl get nodes
```

which should display output similar to:
```text
NAME                                         STATUS     ROLES     AGE       VERSION
ip-172-25-1-105.us-west-1.compute.internal   NotReady   master    1m        v1.9.2
ip-172-25-1-146.us-west-1.compute.internal   Ready      <none>    1m        v1.9.2
ip-172-25-1-202.us-west-1.compute.internal   Ready      <none>    1m        v1.9.2
```

### Get a copy of yelb application

After you've successfully connected to the sandbox control node and verified that your `kubectl` works correctly, use the following commands to get a copy of `yelb` and change your working directory to the one with its Kubernetes manifests (while running as root):
```bash
# Install git
yum -y install git

# Clone the Yelb repo and checkout the branch we used for this guide
git clone https://github.com/mreferre/yelb
cd yelb
git checkout 9cba442 # to make sure our examples keep working as yelb evolves

# Change to the manifests directory
cd deployments/platformdeployment/Kubernetes/yaml/
```

### What's next

At this point, you have a functional sandbox Kubernetes cluster with 2 compute nodes and an application that you can use to play around. The rest of this document will walk you through examples of how to deal with a few common scenarios around networking and network security that you can encounter when developing and operating an application that runs on Kubernetes.

Each use case is stand-alone, and does not require you to complete any other use cases in this document.

Feel free to jump to any one as you see fit:

1. [Basic app connectivity through Kubernetes' Services](use_case_1)
2. [Advanced external app connectivity through Kubernetes' Ingress](use_case_2)
3. [Coarse application isolation through Kubernetes Namespaces](use_case_3)
4. [Application micro-segmentation through Kubernetes Network Policies](use_case_4)

<!-- Backup of the rest

5. Application traffic flow visibility
6. Application security with Network Intrusion Detection
7. Application connectivity across multiple Kubernetes clusters




## Use case 5: Application traffic flow visibility

[This is a bonus - idea is to show how to do remote "tcpdump"; this may not work in our QuickStart as TF needs a special Analyzer VM image that needs to be deployed to handle traffic that's been mirrored. I opened [https://jira.tungsten.io/browse/TFP-87](https://jira.tungsten.io/browse/TFP-87) to add this into the QuickStart.

**Further notes**:

*   It is possible to configure an arbitrary Pod as a destination for the mirrored traffic, without the need for the Analyzer VM. This is done in Configure -> Network -> Policies. Create a new policy or edit an existing one and add "Mirror" option with "Analyzer IP". Specify IP and MAC of the Pod that will receive traffic, and set "Juniper Header" to "Enabled" and "Next Hop Mode" to "Dynamic".
*   Mirrored will be forwarded to the selected Pod. I tested with a Pod that's connected to the same Pod network as our sample app's Pods.
*   One small snag: `tcpdump` doesn't have a dissector for Juniper Header, and it's not practical to just cut it off with something like `editcap -C <xxx>` since the `xxx` here is of variable size. One solution would be to have a Pod with `tshark` in it, but I couldn't find any official wireshark/tshark images. I'm guessing we're back to the Analyzer VM option.

More info on "Juniper Header": https://kb.juniper.net/InfoCenter/index?page=content&id=KB33131

]

 Common situations where traffic visibility is helpful are:

*   When you're designing your policy and not entirely sure what should be able to talk to what;
*   When your application is misbehaving

## Advanced use case 6: Application security with Network Intrusion Detection

[This would be an advanced use case: walk through how to create an in-line NIPS based on OSS Snort ([http://sublimerobots.com/2016/02/snort-ips-inline-mode-on-ubuntu/](http://sublimerobots.com/2016/02/snort-ips-inline-mode-on-ubuntu/)), register it as a Service in TF, and then adding it to a Namespace as a transparent Network IPS service.

Would need to figure how/where it could be inserted for application flows, as in service chaining materials I've seen VFNs are inserted between actual Pods, which doesn't match how the app works in the sense that Pods talk to Services, not to other Pods.

I think this would be valuable since no other CNIs support this AFAIK

**Alternative:** we're launching cSRX soon; if there will be a public Docker image for it, we could do a cSRX in front of our sample app]

## Advanced use case 7: Application connectivity across multiple Kubernetes clusters

[I'm not sure if this can be fit into a reasonable form factor, but this is another area where TF is ahead of some of competition: use one TF instance to provide CNI to 2 or more K8s clusters, with Pods in different clusters being able to talk to each other directly]
-->
