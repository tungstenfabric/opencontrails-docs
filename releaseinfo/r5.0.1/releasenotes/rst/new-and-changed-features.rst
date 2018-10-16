.. This work is licensed under the Creative Commons Attribution 4.0 International License.
   To view a copy of this license, visit http://creativecommons.org/licenses/by/4.0/ or send a letter to Creative Commons, PO Box 1866, Mountain View, CA 94042, USA.

========================
New and Changed Features
========================

The features listed in this section are new or changed as of Tungsten Fabric Release 5.0.1. A brief description of each new feature is included.

Support for Advertising of Local AS to BGP Peers
------------------------------------------------

Tungsten Fabric Release 5.0.1 supports advertising of local autonomous system (AS) numbers to BGP peers. With the support for local AS, virtual network functions can advertise AS numbers of the received networks to Tungsten Fabric, which results in the routing table getting updated and in turn enabling the sites to communicate. A new parameter  ``local-autonomous-system`` has been added in the BgpSessionAttributes field in the Tungsten Fabric configuration schema to support local AS. You can configure this parameter either from the Tungsten Fabric web UI or by using the VNC API.

In earlier releases, Tungsten Fabric supported advertising of only Tungsten Fabric AS numbers, so the virtual machines could not advertise the AS numbers of received networks. This is because most BGP implementations do not advertise routes received from a given AS back to the same AS. With the support for local AS in Tungsten Fabric, this check can be avoided, thus ensuring that VNF routes get correctly propagated by BGP.

Support for Red Hat OpenShift Container Platform Version 3.9
------------------------------------------------------------

OpenShift Container Platform version 3.9 is supported on Tungsten Fabric Release 5.0.1 and validated with CentOS 7.5.


Support for EVPN Route Type 5
-----------------------------

Tungsten Fabric Release 5.0.1 supports EVPN Route Type 5 messages as defined in the IETF specification *IP Prefix Advertisement in EVPN* . EVPN Route Type 5 is an extension of EVPN Route Type 2, which carries MAC addresses along with their associated IP addresses. EVPN Route Type 5 facilitates in inter-subnet routing.

Tungsten Fabric Plugin For VMware vRealize Orchestrator
-------------------------------------------------------

The Tungsten Fabric plugin for VMware vRealize Orchestrator is available in Tungsten Fabric Release 5.0.1. You can use the dedicated Tungsten Fabric plugin to connect Tungsten Fabric to VMware vRealize Orchestrator (vRO). vRO is used to automate the management processes in data centers. You can use the Tungsten Fabric plugin to view the Tungsten Fabric controller configurations in the vRO inventory. You can also use the plugin to modify configurations by using vRO workflows. You can deploy the Tungsten Fabric plugin in any Java Virtual Machine (JVM) compatible language and load it on an active vRO instance. In Release 5.0.1, Tungsten Fabric plugin for vRO does not support draft mode.


Support for Mellanox Connectx-5 NIC
-----------------------------------

Starting with Tungsten Fabric Release 5.0.1, Tungsten Fabric vRouter in DPDK mode supports the Mellanox Connectx-5 Network Interface Card (NIC). The NIC works in a no-offload mode in which all packets through the interface are transmitted to the vrouter-dpdk application and then sent to the respective virtual machines (VMs) or the host.

To deploy a node with the Mellanox Connectx-5 NIC, set  ``"DPDK_UIO_DRIVER" : "mlnx"`` for that node under  ``vrouter`` in the ``instances.yaml`` or ``host.yml`` files. The vrouter-dpdk application cannot work if the  ``"DPDK_UIO_DRIVER"`` is not set.

Example ``instances.yml`` file in Ansible-based provisioning setups:
::

 Bms1:
 provider: bms
 ip: 192.0.2.0
 roles:
 vrouter:
 AGENT_MODE: dpdk
 CPU_CORE_MASK: 0xff
 DPDK_UIO_DRIVER: mlnx
 HUGE_PAGES: 32000


Example ``host.yml`` file in Helm-based provisioning setups:
::

 AGENT_MODE: dpdk
 CPU_CORE_MASK: 0xff
 DPDK_UIO_DRIVER: mlnx
 HUGE_PAGES: 32000




Support for Remote Compute
--------------------------

Tungsten Fabric Release 5.0.1 supports remote compute, a method of managing a Tungsten Fabric deployment across many small distributed data centers. Remote compute employs a subcluster that manages compute nodes at remote sites to receive configurations and exchange routes.


Support for Red Hat OpenStack Platform Director 13
--------------------------------------------------

Tungsten Fabric Release 5.0.1 supports integration with Red Hat OpenStack Platform Director 13.

`Table 1`_ lists the the OpenStack releases and the corresponding operating systems and deployer versions supported by Tungsten Fabric Release 5.0.1.

.. _Table 1:

*Table 1* : Supported Release Versions


+------------------------------+----------------------+-------------------------------+-------------------+
| Tungsten Fabric Release      | Operating System     | OpenStack                     | Deployer          |
+==============================+======================+===============================+===================+
| Tungsten Fabric 5.0.1        | RHEL 7.5             | Red Hat OpenStack Platform 13 | RHOSP 13 director |
+------------------------------+----------------------+-------------------------------+-------------------+



Ansible Scripts to Provision Tungsten Fabric
--------------------------------------------

Tungsten Fabric Release 5.0 introduces microservices architecture. The ``contrail-ansible-deployer`` is a set of Ansible playbooks designed to deploy Tungsten Fabric 5.x with microservices architecture on a CentOS-based system.


Tungsten Fabric Microservices
-----------------------------

Starting with Tungsten Fabric Release 5.0, more components are being containerized, and the fat containers are being decomposed into thin containers with microservices. The microservices are still encapsulated in their respective containers, however, only the essential functions relative to each container’s functions are present as microservices. This enables a more agile system, avoiding monolithic containers.

Nothing is changing with regard to Tungsten Fabric functionality, however, employing microservices provides a number of benefits, including the ability to deploy patches without updating the entire Tungsten Fabric deployment, offering better ways to manage the lifecycles of containers, and improving user experiences with Tungsten Fabric provisioning and upgrading. The microservices architecture enables provisioning with minimum information provided and enables every feature to be configurable. Utilizing microservices also simplifies application complexity by implementing small and independent processes.


Containerization of DPDK vRouter
--------------------------------

Starting with Tungsten Fabric Release 5.0, you can configure the Tungsten Fabric DPDK vRouter to run in a Docker container. In earlier releases, DPDK vRouter runs on a compute host. The contrail-vrouter-dpdk binary file provides data plane functionality when Tungsten Fabric vRouter is run in DPDK mode in a Tungsten Fabric cluster.


Distributed Source Network Address Translation (SNAT)
-----------------------------------------------------

The distributed SNAT feature allows virtual machines to communicate with the IP fabric network using the existing forwarding infrastructure for compute node connectivity. This functionality is achieved through port address translation of virtual machine traffic using the IP address of the compute node as the public address.

The following distributed SNAT use case is supported:

- Virtual networks with distributed SNAT enabled can communicate with the IP fabric network. The session must be initiated from a virtual machine. Sessions initiated from the external network are not supported.


Distributed SNAT is supported only for TCP and UDP, and you can configure discrete port ranges for both protocols.


EVPN vRouter MultiHoming to Multiple ToRs
-----------------------------------------

The Tungsten Fabric control node can be in a situation in which it peers with a set of provider edge (PE) nodes that also contain a multihome CE device or top-of-rack (ToR) that is multihomed to the PE nodes, and the PEs are in all-active multihoming mode.

In this situation, any EVPN route originating through the multihome device is exported to Tungsten Fabric with two paths—the multihome device path and the PE path. Those routes need to be load-balanced to prevent skewed traffic flow.

In previous releases, only the Tungsten Fabric controller supports this scenario. In Tungsten Fabric Release 5.0, this support has been added to the Tungsten Fabric vRouter supporting both Layer 2 and Layer 3 traffic.

Fat Flow Enhancements
---------------------

The fat flow feature has been enhanced to support aggregation of multiple flows into a single flow by ignoring source and destination ports and/or IP addresses, or a combination of these. This extends the existing option of ignoring by either source or destination for a given protocol only.

Also added is support for fat-flow configuration at the VN level, extending the existing support at only the VMI level.


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


- Tungsten Fabric supports custom networks in namespace level. Starting with Tungsten Fabric Release 5.0, custom networks are supported for ingress resources as well.


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



Support for Load Balancing as a Service (LBaaS) in the Web UI
-------------------------------------------------------------

For the LBaaS feature, load balancers using HAproxy can now be created, edited, or deleted using the Tungsten Fabric Web UI.



Support for Security Policies Draft Mode
----------------------------------------

Starting with Tungsten Fabric Release 5.0, you can define new security policies and review the policies before enforcing them. You can also edit existing policies and review the changes before updating them. You can define security policies in both global and project scopes.




Support for Virtual Network Route Tables in Tungsten Fabric Introspect
----------------------------------------------------------------------

Starting with Tungsten Fabric Release 5.0, virtual network route table entries per compute node can be viewed in Tungsten Fabric Introspect.

Support for a Flow-Hold Entries Counter in vRouter UVEs
--------------------------------------------------------

Starting with Tungsten Fabric Release 5.0 , a flow-hold entries counter is transmitted in vRouter User-Visible Entities (UVEs). The counter specifies the number of flows in **hold** state in the vRouter. vRouter uses the flow-hold count to check against a defined limit and when it reaches a defined limit, packets requiring new flows are dropped and new flows are not created till the flow-hold count goes below the defined limit.

Along with the flow-hold entries counter, the vRouter UVEs also provide information associated with a vRouter, such as:

- Virtual networks present on the vRouter


- Virtual machines spawned on the server of the vRouter


- Statistics of the traffic flowing through the vRouter

Timestamp In UVE API Response
-----------------------------

Starting with Tungsten Fabric Release 5.0, a timestamp is added to the ``/analytics/uve`` UVE API response message.

Timestamp In UVE Stream Response
--------------------------------

Starting with Tungsten Fabric Release 5.0, a timestamp is added to the ``/analytics/uve-stream`` UVE Stream API response message.

Using Helm Charts to Provision Tungsten Fabric
----------------------------------------------

Starting with Tungsten Fabric 5.0, Tungsten Fabric Helm charts give you complete life cycle management of installation, update, and deletion of Tungsten Fabric Docker-based containers in a microservices architecture.

Helm is the package manager for Kubernetes which is an open source software for managing containerized systems. The packaging format used by Helm is a chart, a collection of files that describe a related set of Kubernetes resources.

Many Tungsten Fabric components have been broken out into manageable Helm charts, including the following specific features:

- Tungsten Fabric service and IP address numbers are configurable by means of Helm charts.


- Ingress controllers can be implemented by means of Helm charts.


RBAC Support for Tungsten Fabric Analytics API—Beta
---------------------------------------------------

Starting with Tungsten Fabric Release 5.0, the Tungsten Fabric Analytics API supports role-based access control (RBAC) as a Beta feature. Based on the user privileges, the logged-in user can access network monitoring information. Tungsten Fabric Analytics API provides this information by mapping the user query and the UVE to the configuration objects on which RBAC rules are applied.

Remote Compute—Beta
-------------------

Remote compute is available as a Beta feature. The remote compute feature enables the deployment of Tungsten Fabric in many small distributed data centers, up to hundreds or even thousands, for telecommunications point-of-presence (PoPs) or central offices (COs). Because each small datacenter has only a small number of computes running only a few applications, it is not cost-effective to deploy a full Tungsten Fabric cluster of nodes of control, configuration, analytics, database, and the like, on dedicated servers in each distributed PoP. Additionally, manually managing hundreds or thousands of clusters is not feasible operationally.

Remote compute implements a subcluster that manages compute nodes at remote sites to receive configurations and exchange routes.
