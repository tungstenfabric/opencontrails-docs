
==============
Known Behavior
==============

This section lists known limitations with this release. Bug numbers are listed and can be researched in `Launchpad.net`_  .

- 1694343 In DPDK vRouter use cases such as SNAT and LBaas that require netns, you cannot set jumbo MTU size. Maximum MTU allowed: <=1500 .

There is no workaround at present.


- 1716308 When the vRouter receives the head fragment of an ICMPv6 packet, the head fragment is immediately enqueued to the assembler. The flow is created as hold flow and then trapped to the agent. If fragments corresponding to this head fragment are already in the assembler or if new fragments arrive immediately after the head fragment, the assembler releases them to flow module. Fragments get enqueued in the hold queue if agent does not write flow action by the time the assembler releases fragments to the flow module. A maximum of three fragments are enqueued in the hold queue at a time. The remaining fragments are dropped from the assembler to the flow module.

As a workaround, the head fragment is enqueued to assembler only after flow action is written by agent. If the flow is already present in non-hold state, it is immediately enqueued to assembler.


- 1730021 In Contrail Security, non-admin users cannot access global scope objects when  global_accessis set to  0.

As a workaround, for non-admin users to access global scope objects, set  global_accessto  5.


- 1733027 In a multi-node analytics cluster, when one of analytics nodes shuts down or is rebooted, the contrail-status on the other analytics nodes displays the status of contrail-analytics-api and contrail-alarm-gen as initializing with the error message:  Redis-UVE:<ip-address of analytics node that was shutdown/rebooted>:6381[None] connection down. This does not impact the functioning of the analytics cluster.


- 1735590 In Kubernetes and OpenShift based deployments when we crate SNAT router and extend cluster-network to that SNAT router host is losing all connectivity.

As a workaround, if you want to use the SNAT feature in Contrail, disassociate the ip-fabric-cluster-network-default policy and delete it.


- 1749614 In a Helm-based provisioned cluster, VM launch fails if MariaDB replication is set to >1.


- 1754742 When you receive an error message during Kolla provisioning, rerunning the code will not work. In order for the provisioning to work, restart provisioning from scratch.


- 1755997 Kubernetes IP fabric feature is supported only on the pods and not the services.


- 1759576 Metadata SSL works only in HA deployment mode.


- 1759695 After deleting a vRouter chart with DPDK, the NICS do not rebind to the host in Helm.


- 1761137 High Availability provisioning of Kubernetes master is not supported.


- 1764739 Docker restart hangs indefinitely and Docker daemon stops running post the hang.


- 1764925 RabbitMQ clustering fails on certain nodes in a setup. As a workaround, restart the container that is not in the cluster.


- 1765277 When a snapshot of an active VM fails, shutdown the VM before generating the snapshot.


- 1765281 On a DPDK compute  vif list –ratecore-dumps with traffic.


- 1765487 A false alarm for config service is generated when  configand  configdbservices are installed on different nodes. Ignore the false alarm.


- 1766035 On a Kubernetes cluster, a controller node reboot fails to re-establish the BGP XMPP connection with compute nodes. As a workaround, flush the iptables on the Kubernetes master.


- 1766315 After provisioning Contrail by using a Helm-based provisioned cluster, restart nova-compute container.


- 1766371 OpenShift use cases work in non-HA environments only.


- 1767094 Kube DNS fails to come online come up in a multi-interface setup.


- 1767466 In Contrail 5.0 release, with Contrail Helm charts, Kubernetes ingress Web UI URL does not work when Web UI is started with secure (TLS) option.


- 1767470 SR-IOV installation is not supported with contrail-helm-deployer.


- 1767472 SR-IOV with DPDK co-existence deployment is not supported using contrail-helm-deployer.


- 1759428 Cannot provision an external MX series router by running the  provision_mx.pyscript that contains the list of external routers.



.. _Launchpad.net: https://bugs.launchpad.net/juniperopenstack
