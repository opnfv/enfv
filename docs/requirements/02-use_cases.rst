Use cases and scenarios
=======================

There are several use cases related to Edge NFV:

1. vE-CPE.
    [vE-CPE]_ is related to most popular NFV use case where NFVI compute node is
    located at customer premises. Typical applications are virtual Firewall and Virtual BGP router;
    VNF chain can be hosted in vE-CPU host and/or DC

2. Stand-alone vE-CPE.
    It is the same as above but all virtual appliances are hosted at the same CPE compute node.

3. Residential GW.
    Similar to vE-CPE, the major difference is scale. Typical VNFs are "WAN fault monitoring",
    "Performance monitoring". Ratio between deployed vE-CPE
    and Residential GW might reach 1:100 or even 1:1000, thus VNF management overhead must be minimized.
    For instance, self-termination after predefined activity period seems preferable over
    explicit VNF removing via management system.

4. Distributed Base station.
    TBD. What is the difference for it?

5. Network connectivity.
    In most cases CPE is connected to Metro Ethernet [#f1]_ .



.. [#f1] In all above use cases management traffic is coming inband with tenant traffic.
