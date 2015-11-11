Use cases and scenarios
=======================

There are several use cases related to Edge NFV: 

1. Isolated vE-CPE. 
    [vE-CPE]_ is related to most popupar NFV use case where NFVI compute node is 
    located at customer premises. Typical applications are virtual Firewall and Virtual BGP router; 
    in simplest case two virtual appliances are hosted at the same CPE compute node.

#. Distributed VE-CPE. 
    It is the same as above but at least one virtual appliance is 
    hosted on another compute node, presumably in DC.

#. Residential GW. 
    Similar to Isolated vE-CPE, the major difference is scale. Typical VNFs are "WAN fault monitoring", 
    "Performance monitoring". Ratio between deplyed vE-CPE 
    and Residential GW might reach 1:100 or even 1:1000, thus VNF management overhead must be minimized. 
    For instance, self-termination after predefined activity period seems preferable over 
    explicit VNF removing via management system.

#. Distributed Base station. 
    TBD. What is the difference for it?

#. Network connectivity. 
    In most cases CPE is connected to Metro Ethernet [#f1]_ .



.. [#f1] In all above use cases management traffic is coming inband with tenant traffic. 


Revision: _sha1_

Build date: |today|
