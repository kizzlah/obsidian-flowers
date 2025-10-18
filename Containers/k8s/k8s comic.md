---
created: 2025-08-30T03:51
updated: 2025-08-30T05:44
---
## Notes
	Monolithic applications were once the go to for containerization. They had impressive feature sets, but too many interdependent parts, resulting in a nightmare for integration and deployment. By instead converting them into individual processes, however, things became easier to control. These smaller units monolithic services are known as "microservices", which can be debugged, updated, and deployed individually without causing the entire infrastructure to go dark.

	Even separated the services still need to be able to communicate w/one another. This is why they remain loosely coupled with a lightweight protocol to cooperate and preserve the network of dependencies which tied the monolithic apps 

	The issue then becomes operational: if all microservices are ran on a single OS, there could be conflicts b/t library versions and application components. If put together in a VM, apps could still conflict. If each has its own VM, the workload becomes heavy, wasteful, and expensive.

	The solution: a self-contained process with each built to run on its own with its components and settings built in, or, everything needed to run on any machine, virtual or bare metal. AKA Containers. 

<center>Modularity + Interpretability = 
Portability, Reproducibility, and Scalability </center>

