.. This work is licensed under the Creative Commons Attribution 4.0 International License.
   To view a copy of this license, visit http://creativecommons.org/licenses/by/4.0/ or send a letter to Creative Commons, PO Box 1866, Mountain View, CA 94042, USA.

==========================================
Getting Started with Tungsten Fabric 5.0.1
==========================================

Prerequisites
-------------

Deployment instructions presented in this document install and configure Tungsten Fabric SDN solution in a 3 node environment (1 OpenStack/Tungsten Fabric Controller, 2 OpenStack/Tungsten Fabric Computes) using OpenStack Ocata as orchestrator. We will further refer to these 3 nodes as 'Target nodes'.
A node can be either a virtual machine or a bare-metal server; either way, user experience is seamless.

Tungsten Fabric solution is provisioned via `Ansible` automation tool. In order to deploy Tungsten Fabric solution, besides the 3 nodes mentioned earlier, we also need another node, from which we will run `Ansible` commands. Similarly, this node can be either a virtual machine or a bare-metal server. We will refer to this node as 'Deploy node'.

Supported Operating Systems for the Target nodes and the Deploy node are `RedHat7.5` or greater and `CentOS7.5` or greater.


Hardware and Software Requirements
----------------------------------

1st thing that needs to be established before deploying Tungsten Fabric solution is the hardware on which we will deploy it. Below are specified the minimum hardware and software requirements that need to be met for a smooth Tungsten Fabric experience.

Hardware:

    * Target Nodes:
        * At least 4 CPU cores
        * At least 64 GB RAM
        * At least 300 GB storage
        * At least one Ethernet port
    * Deploy Node:
	* At least 2 CPU cores
        * At least 4 GB RAM
        * At least 50 GB storage
        * At least one Ethernet port
     
Software:

    * `RedHat 7.5` or greater/`CentOS 7.5` or greater
    * valid `RedHat 7.5` subscription, in case `RedHat 7.5` is used as OS (Operating System)
    * `Kernel release 3.10.0.862*` or greater
    * `Ansible 2.6.4` or greater
    * `Docker 18.06.1-ce` or greater
    * `OpenStack Newton/Ocata/Pike/Queens`

Steps on All Target Nodes
-------------------------

Please note that all commands, on all Target nodes, have been run as **root**.

#. Update all installed packages and reboot:

   ``# yum update -y``

   ``# reboot``

#. Generate SSH public key:

   ``# ssh-keygen -t rsa``

#. Copy SSH public key (from each Target node) to the Deploy node:

   ``# ssh-copy-id root@<Deploy_Node_IP_Address>``

Steps on the Deploy Node
---------------------------

Please note that all commands, on the Deploy node, have been run as **root**.

#. Install prerequisites:

   ``# yum install -y yum-plugin-priorities yum-utils vim net-tools git ansible``

#. Generate SSH public key:

   ``# ssh-keygen -t rsa``

#. Copy SSH public key from the Deploy node to the 3 Target nodes:

   ``# ssh-copy-id root@<Target_Node_IP_Address>``

#. Clone the `contrail-ansible-deployer` repo, `R5.0` branch:

   ``# git clone https://github.com/Juniper/contrail-ansible-deployer.git -b R5.0``

#. Replace the content of `contrail-ansible-deployer/config/instances.yaml` with the following and fill in placeholders - marked as ``<...>`` - with info from your setup:

   Worth mentioning that it is recommended for each Target node to have at least 2 Ethernet ports. 
   1st Ethernet port should be used for management/provisioning and control plane traffic. 2nd Ethernet port should be used for dataplane traffic. Info regarding the dataplane traffic is set in the following lines in ``instances.yaml``:

   ``PHYSICAL_INTERFACE: <Iface_Name_That_vhost0_Will_Use>``

   ``VROUTER_GATEWAY: <Gateway_IP_Address_for_Dataplane_Network>``

   Therefore, if we have a 2nd Ethernet port for the dataplane traffic, we will fill in the placeholders from the lines above with info associated to the 2nd Ethernet port.
   Otherwise, if only 1 Ethernet port is used, we will fill in all the placeholders with info associated to this Ethernet port.

::

       global_configuration:
         CONTAINER_REGISTRY: &CONTAINER_REGISTRY tungstenfabric
         REGISTRY_PRIVATE_INSECURE: True
       provider_config:
         bms:
           ssh_pwd: <ssh_root_password>
           ssh_user: root
           ntpserver: pool.ntp.org
           domainsuffix: local
       instances:
         bms1:
           provider: bms
           ip: &tungsten_fabric_ip_address <Tungsten_Fabric_Controller_Mgmt_IP_Address>
           roles:
               config_database:
               config:
               control:
               analytics_database:
               analytics:
               webui:
               openstack:
         bms2:
           provider: bms
           ip: <Tungsten_Fabric_Compute1_Mgmt_IP_Address>
           roles:
               vrouter:
               openstack_compute:
         bms3:
           provider: bms
           ip: <Tungsten_Fabric_Compute2_Mgmt_IP_Address>
           roles:
               vrouter:
               openstack_compute:
       contrail_configuration:
         CONTAINER_REGISTRY: *CONTAINER_REGISTRY
         CONTRAIL_VERSION: r5.0.1
         CLOUD_ORCHESTRATOR: openstack
         RABBITMQ_NODE_PORT: 5673
         VROUTER_GATEWAY: <Gateway_IP_Address_for_Dataplane_Network>
         PHYSICAL_INTERFACE: <Iface_Name_That_vhost0_Will_Use>
         AUTH_MODE: keystone
         KEYSTONE_AUTH_HOST: *tungsten_fabric_ip_address
         KEYSTONE_AUTH_URL_VERSION: /v3
         KEYSTONE_AUTH_ADMIN_USER: admin
         KEYSTONE_AUTH_ADMIN_PASSWORD: &keystone_passwd <KeyStone_Admin_Password>
         imageManager_ip: *tungsten_fabric_ip_address
         computeManager_ip: *tungsten_fabric_ip_address
         ANALYTICSDB_NODES: *tungsten_fabric_ip_address
         CONTROLLER_NODES: *tungsten_fabric_ip_address
         WEBUI_NODES: *tungsten_fabric_ip_address
         ANALYTICS_NODES: *tungsten_fabric_ip_address
         CONTROL_NODES: *tungsten_fabric_ip_address
         CONFIGDB_NODES: *tungsten_fabric_ip_address
       kolla_config:
         kolla_globals:
           enable_haproxy: no
           enable_ironic: no
           enable_swift: no
         kolla_passwords:
           keystone_admin_password: *keystone_passwd

6. Go to `contrail-ansible-deployer` folder and run the following `ansible` commands:

   ``# cd contrail-ansible-deployer``

   ``# ansible-playbook -i inventory/ -e orchestrator=openstack playbooks/configure_instances.yml``

   ``# ansible-playbook -i inventory/ playbooks/install_openstack.yml``

   ``# ansible-playbook -i inventory/ -e orchestrator=openstack playbooks/install_contrail.yml``

#. After the Tungsten Fabric deployment, we can run ``contrail-status`` command on both Tungsten Fabric Controller node and Tungsten Fabric Compute Node(s) to check whether Tungsten Fabric Docker containers are up and running. A successful installation should display all Tungsten Fabric containers as `active`.

   Below it is displayed the output of ``# contrail-status`` command run on Tungsten Fabric Controller node and on Tungsten Fabric Compute node, respectively:

   ``# contrail-status``

::

   == Contrail control ==
   control: active
   nodemgr: active
   named: active
   dns: active

   == Contrail config-database ==
   nodemgr: active
   zookeeper: active
   rabbitmq: active
   cassandra: active

   == Contrail database ==
   kafka: active
   nodemgr: active
   zookeeper: active
   cassandra: active

   == Contrail analytics ==
   snmp-collector: active
   query-engine: active
   api: active
   alarm-gen: active
   nodemgr: active
   collector: active
   topology: active

   == Contrail webui ==
   web: active
   job: active

   == Contrail config ==
   api: active
   zookeeper: active
   svc-monitor: backup
   nodemgr: active
   device-manager: active
   cassandra: active
   rabbitmq: active
   schema: active

   # contrail-status

::

   vrouter kernel module is PRESENT
   == Contrail vrouter ==
   nodemgr: active
   agent: active


Run Tungsten Fabric
-------------------

   Sometimes, the `neutron-server` Docker container is continuously restarting. 

   **Workaround** Comment out `service_plugins` line from `/etc/kolla/neutron-server/neutron.conf` located on the Tungsten Fabric Controller node and then restart `neutron_server` docker container so that the change is taken into consideration:

    ``sed -i 's/^service_plugins = neutron_plugin_contrail.plugins.opencontrail.loadbalancer.v2.plugin.LoadBalancerPluginV2/#service_plugins = neutron_plugin_contrail.plugins.opencontrail.loadbalancer.v2.plugin.LoadBalancerPluginV2/g' /etc/kolla/neutron-server/neutron.conf``

    ``docker restart neutron_server``

   Next, the user can login via Tungsten Fabric Web UI, by accessing:

   ``https://<Tungsten_Fabric_Controller_Mgmt_IP_Address>:8143``

   with the following credentials:
   
   Username: ``admin``

   Password: ``<KeyStone_Admin_Password>``

   After successful login, the following page is displayed:


   .. figure:: TF_GUI.png


   Happy Hacking!


External References
-------------------

Below are reference links related to further details of features and use cases.

* OpenStack: https://www.openstack.org/
* DPDK: https://www.dpdk.org/
* Kubernetes: https://kubernetes.io/
* Red Hat: https://www.redhat.com/
* Ubuntu: https://www.ubuntu.com/
* Contrail Feature Guide: https://www.juniper.net/documentation/en_US/contrail5.0/information-products/pathway-pages/contrail-feature-guide-pwp.html

