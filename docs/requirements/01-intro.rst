Introduction
============

The purpose of this Requirements Project is to articulate the capabilities
and behaviours needed in Edge NFV platforms, and how they interact with
centralized NFVI and MANO components of NFV solutions.


Problem description
-------------------

Edge NFVI location has certain specific requirements related to:

1. Appropriate Tunneling for User Traffic across WAN (Ethernet, IP/MPLS) links
#. Appropriate Tunneling for Management Traffic across WAN links
#. Including reachability requirements to the compute platform (‘eth0’ resilience,
   this also include backup path through other media e.g. 4G/5G)
#. Extending Multi-DC management to address many small "DC" locations
#. Monitoring Capabilities required for a remote Compute Node
#. Squaring Bare Metal with remote survivability and whether IaaS is more appropriate for remote locations
#. Security.As demarcation technology is operated in an un-trusted environment (CSP perspective)
   additional means need to be implemented. Similarly, the enterprise might have concerns if
   the security architecture is impacted as VNFs provide functions at different locations than
   the precious hardware; topics like authentication, authorization, securing the traffic.
