# 02: Hierarchical architecture: Why do we have to do so?

With more complex business logics, the intial system without hierarchy will face problems of coupling and mutual dependency between each module, which makes it hard to expand.

## What is hierarchical architecture?

Hierarchical architecture is a common design in software engineering which breaks the whole system into `N` layers with independent reponsibilities which can cooperate to function as a whole. For example,

- MVC: Model, View, and Controller
- Simple hierarchy of representation (web), logic (service), and data access (DAO) layers
- OSI 7-layer network model
- TCP/IP 5-layer model: physical, data link, network, transport, and application layer
- Linux file system

## Benefits of hierarchical architecture

- Hierarchical architecture can simplify the system design and let different people focus on the details of a specific layer.
- A well designed layer can be reused for other projects.
- Hierarchical architecture allows us to scale out only for one layer which becomes bottleneck.

## How to design hierarchy?

The most important thing is to clearly define the boundary/interface of each layer.

## Limitations of hierarchical architecture

The most obvious limitation is it will increase the complexity of the overall design. The other limitation is if we deploy the components of each layer independently we should anticipate the loss of performance due to the network latency.
