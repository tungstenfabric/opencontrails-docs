
========================
New and Changed Features
========================

The features listed in this section are new or changed as of Tungsten Fabric Release 5.0. A brief description of each new feature is included.

   -  `Ansible Scripts to Provision Tungsten Fabric`_ 


   -  `Tungsten Fabric Microservices`_ 


   -  `Containerization of DPDK vRouter`_ 


   -  `Distributed Source Network Address Translation (SNAT)`_ 


   -  `EVPN vRouter MultiHoming to Multiple ToRs`_ 


   -  `Fat Flow Enhancements`_ 


   -  `Implementing Kubernetes Network Policy with Tungsten Fabric Firewall Policy`_ 


   -  `Kubernetes Updates`_ 


   -  `Routing Policies Enhanced for Interface Routes`_ 


   -  `Service Instance Health Check Failure`_ 


   -  `Support for Load Balancing as a Service (LBaaS) in the Web UI`_ 


   -  `Support for Security Policies Draft Mode`_ 


   -  `Support for Virtual Network Route Tables in Tungsten Fabric Introspect`_ 


   -  `Support for a Flow-Hold Entries Counter in vRouter UVEs`_ 


   -  `Timestamp In UVE API Response`_ 


   -  `Timestamp In UVE Stream Response`_ 


   -  `Using Helm Charts to Provision Tungsten Fabric`_ 


   -  `Tungsten Fabric Plugin For VMware vRealize Orchestrator—Beta`_ 


   -  `RBAC Support for Tungsten Fabric Analytics API—Beta`_ 


   -  `Remote Compute—Beta`_ 


   -  `OpenShift Enterprise`_ 




Ansible Scripts to Provision Tungsten Fabric
--------------------------------------------

Tungsten Fabric Release 5.0 introduces microservices architecture. The ``contrail-ansible-deployer`` is a set of Ansible playbooks designed to deploy Tungsten Fabric 5.x with microservices architecture on a CentOS-based system.

For more information, see `Overview of contrail-ansible-deployer for Installing Tungsten Fabric with Microservices Architecture`_  and `Installing Tungsten Fabric with OpenStack Ocata and Kolla Ansible`_  .



Tungsten Fabric Microservices
-----------------------------

In Tungsten Fabric Release 5.0, components are being containerized that each container encapsulates the services needed for that container into microservices. The microservices are still encapsulated in their respective containers, however, only the essential functions relative to each container’s functions are present as microservices. This enables a more agile system, avoiding monolithic containers.

Employing microservices provides a number of benefits, including the ability to deploy patches without updating the entire Tungsten Fabric deployment, offering better ways to manage the lifecycles of containers, and improving user experiences with Tungsten Fabric provisioning and upgrading. The microservices architecture enables provisioning with minimum information provided, and enables every feature to be configurable, Utilizing microservices also simplifies application complexity by implementing small, independent processes.

For more information, see `Introduction to Tungsten Fabric Microservices Architecture`_  .



Containerization of DPDK vRouter
--------------------------------

In Tungsten Fabric Release 5.0, the Tungsten Fabric DPDK vRouter to run in a Docker container. The contrail-vrouter-dpdk container provides data plane functionality when Tungsten Fabric vRouter is run in DPDK mode in a Tungsten Fabric cluster.

For more information, see `Configuring Tungsten Fabric DPDK vRouter to Run in a Docker Container`_  .



Distributed Source Network Address Translation (SNAT)
-----------------------------------------------------

The distributed SNAT feature allows virtual machines to communicate with the IP fabric network using the existing forwarding infrastructure for compute node connectivity. This functionality is achieved through port address translation of virtual machine traffic using the IP address of the compute node as the public address.

The following distributed SNAT use case is supported:

- Virtual networks with distributed SNAT enabled can communicate with the IP fabric network. The session must be initiated from a virtual machine. Sessions initiated from the external network are not supported.


Distributed SNAT is supported only for TCP and UDP, and you can configure discrete port ranges for both protocols.

For more information, see `Source Network Address Translation (SNAT)`_  .



EVPN vRouter MultiHoming to Multiple ToRs
-----------------------------------------

The Tungsten Fabric control node can be in a situation in which it peers with a set of provider edge (PE) nodes that also contain a multihome CE device or top-of-rack (ToR) that is multihomed to the PE nodes, and the PEs are in all-active multihoming mode.

In this situation, any EVPN route originating through the multihome device is exported to Tungsten Fabric with two paths—the multihome device path and the PE path. Those routes need to be load-balanced to prevent skewed traffic flow.

In Tungsten Fabric Release 5.0, this support has been added to the Tungsten Fabric vRouter supporting both Layer 2 and Layer 3 traffic, in addition to Tungsten Fabric Controller.



Fat Flow Enhancements
---------------------

The fat flow feature has been enhanced to support aggregation of multiple flows into a single flow by ignoring source and destination ports and/or IP addresses, or a combination of these. This extends the existing option of ignoring by either source or destination for a given protocol only.

Also added is support for fat-flow configuration at the VN level, extending the existing support at only the VMI level.

For more information, see `Understanding Flow Sampling`_  .



Implementing Kubernetes Network Policy with Tungsten Fabric Firewall Policy
---------------------------------------------------------------------------

Tungsten Fabric Release 5.0 supports implementing Kubernetes network policy in Tungsten Fabric using the Tungsten Fabric firewall security policy framework. While Kubernetes network policy can be implemented using other security objects in Tungsten Fabric like security groups and Tungsten Fabric network policies, the support of tags by Tungsten Fabric firewall policy allows decoupling of routing from security policies and provides multi dimension segmentation and policy portability, while significantly enhancing user visibility and analytics functions.

For more information, see `Implementing Kubernetes Network Policy with Tungsten Fabric Firewall Policy`_  .



Kubernetes Updates
------------------

Tungsten Fabric Release 5.0 includes the following Kubernetes updates.

- The IP fabric forwarding feature enables reachability to public cloud services for Kubernetes pods. The IP fabric forwarding feature enables the overlay network to be a part of the underlay network or the IP fabric network, eliminating the need for encapsulating data packets between Kubernetes pods.


- The ip-fabric-snat feature enables service or ingress reachability from external clusters in isolated namespaces.


- Multiple Ingress Controllers can co-exist in Tungsten Fabric. Since Tungsten Fabric ensures the reachability between pods and services, any ingress controller can reach the endpoints or pods directly or through services.


- Tungsten Fabric 5.0 supports custom networks in namespace level as well as for ingress resources.


- Tungsten Fabric network policy is created between the IP fabric network and pod-network to provide reachability between node and pods. So, any process in the node can reach the pods. Kubernetes Service Node-Port is also supported.


For more information on Kubernetes updates in Tungsten Fabric Release 5.0, see `Kubernetes Updates`_  .



Routing Policies Enhanced for Interface Routes
----------------------------------------------

Service interface and static routes are proliferating as leaked routes in the routing table of the SDN gateway. To reduce these leaked routes, routing policies have additional term match conditions under the protocol options to distinguish interface routes, service interface routes, and static routes from other VM routes. Also, a new action attribute, ASPATH (autonomous system path), is added that can be appended with a configurable AS list. All of the action attributes of Add/Set/Remove Community, SetLocal-Pref, and Set Med are supported with the new protocol match conditions and the new ASPATH list append action.

Users will be able to configure the new term match and action attributes as needed in the following cases:

- Setting LocalPref on service interface static routes when exporting to distinguish routes and take further action.


- Setting different LocalPref for all other reoriginated routes to distinguish routes and take further action.


Additionally, Tungsten Fabric can set the LocalPref based on community onto imported routes, instead of the data center gateway, allowing direct access to VPN Internet-Shared from Tungsten Fabric.



Service Instance Health Check Failure
-------------------------------------

In Tungsten Fabric Release 5.0, when one or more than one service instance (SI) in a service chain fails, reorigination of routes on the ingress and egress sides of the service chain is stopped. The routes automatically converge to a backup service chain that is part of another Tungsten Fabric cluster. You can detect an SI failure by keeping track of corresponding connected routes of the service chain address.

For more information, see `Service Instance Health Checks`_  .



Support for Load Balancing as a Service (LBaaS) in the Web UI
-------------------------------------------------------------

For the LBaaS feature, load balancers using HAproxy can now be created, edited, or deleted using the Tungsten Fabric Web UI.

For more information, see `Configuring Load Balancing as a Service in Tungsten Fabric`_  .



Support for Security Policies Draft Mode
----------------------------------------

In Tungsten Fabric Release 5.0, you can define new security policies and review the policies before enforcing them. You can also edit existing policies and review the changes before updating them. You can define security policies in both global and project scopes.

For more information, see `Security Policies Draft Mode Overview`_  .



Support for Virtual Network Route Tables in Tungsten Fabric Introspect
----------------------------------------------------------------------

In Tungsten Fabric Release 5.0, virtual network route table entries per compute node can be viewed in Tungsten Fabric Introspect.



Support for a Flow-Hold Entries Counter in vRouter UVEs
--------------------------------------------------------

In Tungsten Fabric Release 5.0 , a flow-hold entries counter is transmitted in vRouter User-Visible Entities (UVEs). The counter specifies the number of flows in **hold** state in the vRouter. vRouter uses the flow-hold count to check against a defined limit and when it reaches a defined limit, packets requiring new flows are dropped and new flows are not created till the flow-hold count goes below the defined limit.

Along with the flow-hold entries counter, the vRouter UVEs also provide information associated with a vRouter, such as:

- Virtual networks present on the vRouter


- Virtual machines spawned on the server of the vRouter


- Statistics of the traffic flowing through the vRouter




Timestamp In UVE API Response
-----------------------------

In Tungsten Fabric Release 5.0, a timestamp is added to the ``/analytics/uve`` UVE API response message.



Timestamp In UVE Stream Response
--------------------------------

In Tungsten Fabric Release 5.0, a timestamp is added to the ``/analytics/uve-stream`` UVE Stream API response message.



Using Helm Charts to Provision Tungsten Fabric
----------------------------------------------

In Tungsten Fabric 5.0, Tungsten Fabric Helm charts give you complete life cycle management of installation, update, and deletion of Tungsten Fabric Docker-based containers in a microservices architecture.

Helm is the package manager for Kubernetes which is an open source software for managing containerized systems. The packaging format used by Helm is a chart, a collection of files that describe a related set of Kubernetes resources.

Many Tungsten Fabric components have been broken out into manageable Helm charts, including the following specific features:

- Tungsten Fabric service and IP address numbers are configurable by means of Helm charts.


- Ingress controllers can be implemented by means of Helm charts.


For more information, see:

-  `Installing and Managing Tungsten Fabric 5.0 Microservices Architecture Using Helm Charts`_  


-  `Using Helm Charts to Provision Multinode Tungsten Fabric OpenStack Ocata with High Availability`_  


-  `Using Helm Charts to Provision All-in-One Tungsten Fabric with OpenStack Ocata`_  


-  `Accessing a Tungsten Fabric OpenStack Helm Cluster`_  


-  `Frequently Asked Questions About Tungsten Fabric and Helm Charts`_  




Tungsten Fabric Plugin For VMware vRealize Orchestrator—Beta
------------------------------------------------------------

The Tungsten Fabric plugin for VMware vRealize Orchestrator is available as a Beta feature in Tungsten Fabric Release 5.0. You can use the dedicated Tungsten Fabric plugin to connect Tungsten Fabric to VMware vRealize Orchestrator (vRO). vRO is used to automate the management processes in data centers. You can use the Tungsten Fabric plugin to view the Tungsten Fabric controller configurations in the vRO inventory. You can also use the plugin to modify configurations by using vRO workflows. You can deploy the Tungsten Fabric plugin in any Java Virtual Machine (JVM) compatible language and load it on an active vRO instance.

See `Integrating Tungsten Fabric with VMware vRealize Orchestrator.`_  



RBAC Support for Tungsten Fabric Analytics API—Beta
---------------------------------------------------

In Tungsten Fabric Release 5.0, the Tungsten Fabric Analytics API supports role-based access control (RBAC) as a Beta feature. Based on the user privileges, the logged-in user can access network monitoring information. Tungsten Fabric Analytics API provides this information by mapping the user query and the UVE to the configuration objects on which RBAC rules are applied.



Remote Compute—Beta
-------------------

Remote compute is available as a Beta feature. The remote compute feature enables the deployment of Tungsten Fabric in many small distributed data centers, up to hundreds or even thousands, for telecommunications point-of-presence (PoPs) or central offices (COs). Because each small datacenter has only a small number of computes running only a few applications, it is not cost-effective to deploy a full Tungsten Fabric cluster of nodes of control, configuration, analytics, database, and the like, on dedicated servers in each distributed PoP. Additionally, manually managing hundreds or thousands of clusters is not feasible operationally.

Remote compute implements a subcluster that manages compute nodes at remote sites to receive configurations and exchange routes.

For more information, see `Remote Compute`_  .



OpenShift Enterprise
--------------------

OpenShift Enterprise is *not* supported in Tungsten Fabric Release 5.0. OpenShift Origin 3.7 is supported.


.. _Overview of contrail-ansible-deployer for Installing Tungsten Fabric with Microservices Architecture: https://www.juniper.net/documentation/en_US/contrail5.0/topics/concept/install-contrail-overview-ansible-50.html

.. _Installing Tungsten Fabric with OpenStack Ocata and Kolla Ansible: https://www.juniper.net/documentation/en_US/contrail5.0/topics/concept/install-contrail-ocata-kolla-50.html

.. _Introduction to Tungsten Fabric Microservices Architecture: https://www.juniper.net/documentation/en_US/contrail5.0/topics/concept/intro-microservices.html

.. _Configuring Tungsten Fabric DPDK vRouter to Run in a Docker Container: https://www.juniper.net/documentation/en_US/contrail5.0/topics/task/configuration/containerzing-contrail-dpdk-vrouter.html

.. _Source Network Address Translation (SNAT): https://www.juniper.net/documentation/en_US/contrail5.0/topics/task/configuration/snat-vnc.html

.. _Understanding Flow Sampling: https://www.juniper.net/documentation/en_US/contrail5.0/topics/concept/flow-sample-overview.html

.. _Implementing Kubernetes Network Policy with Tungsten Fabric Firewall Policy: https://www.juniper.net/documentation/en_US/contrail5.0/topics/concept/k8s-network-policy.html

.. _Kubernetes Updates: https://www.juniper.net/documentation/en_US/contrail5.0/topics/concept/k8s-ip-fabric.html

.. _Service Instance Health Checks: https://www.juniper.net/documentation/en_US/contrail5.0/topics/topic-map/service-instance-health-check.html

.. _Configuring Load Balancing as a Service in Tungsten Fabric: https://www.juniper.net/documentation/en_US/contrail5.0/topics/task/configuration/load-balance-as-service-vnc.html

.. _Security Policies Draft Mode Overview: https://www.juniper.net/documentation/en_US/contrail5.0/topics/concept/security-policy-draft-mode.html

.. _Installing and Managing Tungsten Fabric 5.0 Microservices Architecture Using Helm Charts: https://www.juniper.net/documentation/en_US/contrail5.0/topics/concept/install-microsvcs-helm-chart-50.html

.. _Using Helm Charts to Provision Multinode Tungsten Fabric OpenStack Ocata with High Availability: https://www.juniper.net/documentation/en_US/contrail5.0/topics/concept/install-microsvcs-helm-multi-50.html

.. _Using Helm Charts to Provision All-in-One Tungsten Fabric with OpenStack Ocata: https://www.juniper.net/documentation/en_US/contrail5.0/topics/concept/install-microsvcs-helm-aio-50.html

.. _Accessing a Tungsten Fabric OpenStack Helm Cluster: https://www.juniper.net/documentation/en_US/contrail5.0/topics/concept/access_os_helm_cluster.html

.. _Frequently Asked Questions About Tungsten Fabric and Helm Charts: https://www.juniper.net/documentation/en_US/contrail5.0/topics/concept/install-microsvcs-helm-multi-faq-50.html

.. _Integrating Tungsten Fabric with VMware vRealize Orchestrator.: https://www.juniper.net/documentation/en_US/contrail5.0/topics/concept/integrating-contrail5.0-with-vRO.html

.. _Remote Compute: https://www.juniper.net/documentation/en_US/contrail5.0/topics/concept/remote-compute-50.html
