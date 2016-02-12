Gap analysis in upstream projects
=================================

Network  related gaps
---------------------

1. Terminology.
    Consider to keep upstream/downstream terminology for the traffic leaving/coming to Edge NFV. This gives
    unambiquies names 'uplink/downlink' or 'access/network' for CPE interfaces. Inside DC this traffic is
    calles east-west and no special meaning for interfaces on compute/network node.
2. Uplink interface capacity.
    In most cases those are 1GE as opposite to DC where 10/40G interfaces are prevaling. As result
    1GE interfaces are not part of CI.
3. Tunneling technology:
    a. Case stand-alone NFVI - 802.1ad S-VLAN or MPLS.
    #. Case distributed NFVI - VXLAN or NVGRE over 802.1ad.
        * VXLAN and NVGRE tunnels don't support OAM check.
    #. All above tunneling technology don't support integrity check.
    #. All above tunneling technology don't support payload enryption (optional).
4. Management traffic:
    a. Management traffic should come inband with tenant traffic.
    b. Management traffic shoud be easiliy come trough firewalls, i.e. single IP/port woudl be ideal
       (compare with OpenStack bunch of protocols [firewall]_).
    c. Management connection might be disrupted for a long period of time; once provisioned Edge NFV device
       must keep its functionaly with no respect of management connection state.
5. Resiliency:
    a. Network resiliency is based on dual-homing, service path shall be forked in that case. A VM presumable shall
       be able to select active virtual link for data forwarding
    #. SLA assurance for tenant virtual link - mandatory
    #. Fault propagation towards VM is mandatory
Hypervisor gaps
---------------
#. Monitoring Capabilities required for a remote Compute Node; Hypervisor shall provide extended monitoring of
   VM and its resource usage.
OpenStack gaps
--------------
Later shoudl be per specific component? (nova, neutron...)

  OpenStack Nova
  1. Management system should support dozen of thousands individual hosts.
     Currently each Edge Host is allocated in individual zone, is this approach scalable?
  2. Host is explicitly selected effectively bypassing NOVA scheduler

Deployment gaps
---------------
1. Only traffic interfaces are exposed (e.g. no eth0, no USB); SW deployment is different from DC.
#. Linux shell shall not be exposed; linux CLI shall be replaced presumable by REST.
#. Kernel and Hypervisor are hardened. Only OpenStack agents might be added during deployment.
#. AMT or IPMI shall not be used for SW deployment.