# Router Behaviour

Routers add IP routes to their routing tables using three methods:
- connected routes
- static routes
- routes learned by using dynamic routing protocols

## Routing Protocols
1. Learn routing information about IP subnets from neighboring routers.
2. Advertise routing information about IP subnets to neighboring routers.
3. If more than one possible route exists to reach one subnet, pick the best route based
on a metric.
4. If the network topology changes—for example, a link fails—react by advertising that some routes have failed and pick a new currently best route. (This process is called convergence.)
    - The ability to converge quickly, without causing loops, is one of the most important considerations when choosing which IP routing protocol to use

### Interior vs Exterior Routing Protocols
aka, IGP vs EGP (Interior Gateway Protocol vs Exterior Gateway Protocol)
- AS: An autonomous system (AS) is a network under the administrative control of a single organization
- IGP: for use inside a single AS
    - designed to work best inside a single AS by design
- EGP: for use between different autonomous systems
    - designed to exchange routes between routers in different AS
    - today, Border Gateway Protocol (BGP) is the only EGP in-use

