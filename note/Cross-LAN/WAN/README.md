# WAN

## Exam item
1.2 Describe the characteristics of network topology architecture
    1.2.d WAN
5.5 Describe remote access and site-to-site VPNs


## WAN links:
- point-to-point serial (HDLC by default, PPP)
- point-to-point Ethernet WAN
- Metro Ethernet
    - how to use Ethernet links between a customer site and the SP
    - layer 2, "one big switch"  --> SP
- MPLS
- VPN

### Terms
- Customer premise equipment (CPE)
- Ethernet Virtual Connection (EVC)
    - which user (customer) devices can communicate with which

## Metro Ethernet
- typically Ethernet switches at SP edge
- Service types:
    - Ethernet Line Service (E-Line)
        - point-to-point
        - VPWS (wired)
        - one physical link can accept many E-lines (e.g. 100)
        - expensive when the number of sites that need connection increases `E-lines needed = N*(N-1)/2`
        - if using L3, each line has its own subnet
    - Ethernet LAN Service (E-LAN)
        - full mesh
        - VPLS
        - if using L3, everything on one subnet, using the same routing protocol
    - Ethernet Tree Service (E-Tree)
        - hub and spoke

## MPLS (MultiProtocol Label Switching) network
- typically use routers at SP edge and customer edge
- MPLS creates a WAN service that routes IP packets between customer sites
- The routers on the edge of the MPLS network add and remove an MPLS header to packets as they enter and exit the MPLS network
- The devices inside the MPLS network then use the label field inside that MPLS header when forwarding data across the MPLS network
- Problem solving:
    - Customers use private IPs
    - MPLS network needs to support one private IP network per customer
    - SP can use it to learn different routes per customer
- Because it is L3, it discard data-link headers and can add new different data-link headers when routing packets
    - thus it supports many L2 protocols
- MPLS is the first WAN service that supports QoS
- MPLS uses
    - BPBGP internally
        - advertise routes from multiple customers while keeping the routes logically separated
    - OSPF or other between CE and PE
        - CE routers refer to the neighboring PE router as the next-hop router

## VPN, secured WAN network
### IPsec + GRE tunnel: site-to-site
- Applied to edge devices (routers or firewalls) on each site
- Permanent, always on
- GRE tunnel itself is not encrpted

### TLS: remote access
- on-demand
- Cisco AnyConnect client uses it
