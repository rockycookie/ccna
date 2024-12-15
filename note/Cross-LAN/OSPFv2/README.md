# OSPFv2

## Concepts

- LSA (Link-State Advertisements)
    - a data structure that contains info about network topology
- LSDB (Link-State Database)
    - collection of all the LSAs known to a router
- Dijkstra Shortest Path First (SPF)
    - algorith applied to LSDB to get shortest path to each node

## Procedure
1. Become neighbors
    1. a router sends multicast OSPF Hello packets to each interface periodically
        - which contains router ID (RID) --> 32bit, IP addr
        - multicast IP address `224.0.0.5` --> a multicast IP address intended for all OSPF-speaking routers
        - array of seen router IDs
    2. when reciving OSPF Hello packets, the router
        - the receiver list the sender as a neighbour with state `Init`
        - checks all OSPF parameters
        - add the source router ID to the seen array
        - send new Hello packet
    3. For a router state change from `Init` to `2-Way`
        - The router needs to receive a Hello packet from the neighbour whose seen array contains the receiver's router ID
    4. when both routers reach `2-Way` state
        - they become neighbours and ready to share their LSDB
2. Exchange databases
    1. [exchange] both neighbour routers exhange their database description (list of LSAs)
    2. [loading] the receiver router checks and ask the sender for details of the receiver-missing LSAs
    3. when finished, the neighbours reach `Full` state
3. Maintain neighbour-relationship and LSDB
    - routers monitor neighbour relationship using Hello messages with Hello Interval and Dead Interval
    - routers need to flood LSAs being changed
    - each router that creates an LSA also has the responsibility to reflood the LSA every 30 minutes by default, even if no changes occur
4. Add best route

### Become Neighbours
Routers that both 
- use OSPF
- sit on the same data link
