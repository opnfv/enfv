Use cases and scenarios
=======================

There are several use cases related to Edge NFV.
This section will briefly describe them, along with the issues or complexities that they
introduce versus a typical data center (DC) deployment.


1. vE-CPE.
    [vE-CPE]_ is related to most popular NFV use case where a NFVI compute node is
    located at customer premises. 
    Typical applications are virtual firewall and virtual router to replace physical equivalents.
    The service chain can include VNFs hosted in vE-CPE host and/or a centralized data center.
    Complexities include:

    * This application is very cost-sensitive, so the server will typically be lower performance
      than in the DC.
    * There may not be layer 2/Ethernet connectivity at the deployment site, so tunneling may be required.
    * There may not be initial connectivity to the node, so some sort of zero-touch protocol may be required.

#. Stand-alone vE-CPE.
    It is the same as above but all virtual network functions are hosted at the same CPE compute node.

#. Residential GW.
    Similar to vE-CPE, the major difference is scale. Typical VNFs are "WAN fault monitoring",
    "Performance monitoring". 
    Ratio between deployed vE-CPE and Residential GW might reach 1:100 or even 1:1000,
    so VNF management overhead must be minimized.
    For instance, self-termination after predefined activity period seems preferable over
    explicit VNF removing via management system.

#. Distributed Base station.
    TBD. What is the difference for it?

#. Network connectivity.
    In most cases CPE is connected to Metro Ethernet [#f1]_ .

#. Micro Data Center
    NFVI resources may be located at the edge of the network for the use cases listed above.
    Doing so increases the scale of the clouds or locations that must be orchestrated and controlled.
    If OpenStack is run in a distributed fashion, with a central node controlling distributed
    NFVI servers, the following issues may be seen:

    * Lack of security between OpenStack client and server.
    * Lack of compatibility between different versions of OpenStack.
    * Scalability of OpenStack.
    * Operation in low speed or lossy networks is complicated by the amount of messaging required.
    * OpenStack communications are not secured. This creates a vulnerability in a distributed application.
    * OpenStack numbers VNF ports in a sequential manner, with the sequence serially numbered 
      in the VM/VNF. 
      The difficulty comes when trying to verify that the LAN has been connected to the correct LAN port, 
      the WAN has been connected to the correct WAN port and so on.
    * While OpenStack provides a rich set of APIs, critical support is lacking:

      * No APIs for ssh access to VM/VNFs.
      * No APIs for port mirroring in Neutron.
      * No APIs for OpenStack oversubscription parameter setting 

.. [#f1] In all above use cases management traffic is coming inband with tenant traffic.
