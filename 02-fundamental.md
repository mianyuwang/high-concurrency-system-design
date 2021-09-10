# 02: Hierarchical architecture: Why do have to do so?

With more complex business logics, the intial system without hierarchy will face problems of coupling, mutual dependency, hard to expand.

## What is hierarchical architecture?

Hierarchical architecture is a common design in software engineering which breaks the whole system into N layers with independent reponsibilities which can cooperate to function as a whole. For example,

- MVC: Model, View, and Controller
- Simple hierarchy of representation (web), logic (service), and data access (DAO) layers
- TCP/IP
- Linux file system

## Benefits of hierarchical architecture

- Hierarchical architecture can simplify the system design and let different people focus on a specific layer.
- A well designed layer can be reused for other projects.
- Hierarchical architecture allows us to scale out only for one layer which becomes bottleneck.

## How to design hierarchy?

The most important thing is to clearly define the boundary/interface between layers.
