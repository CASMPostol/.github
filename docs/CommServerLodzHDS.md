# Redundant, Multi-Protocol, Optimal OPC Server In Lodz Agglomeration Heat Distribution System

The municipal heat distribution network of Łódź (1M citizens) is supplied from three heating plants with total thermal output of 2560MW. Their optimal utilization requires a control system to allow working on common areas. As the system is distributed territorially (about 800km of pipes), safe communication between nodes (automation islands) is critical. Additionally, a great number of nodes (~7000) requires to precede the development of an appropriate system structure by a detailed analysis of the availability, throughput, and connectivity standardization. We have decided to use OPC as a communication engine coupled with VHF network. Because of the propagation limits we have to use several central base station locations. The biggest challenge is to synchronize transmission on one common frequency and provide appropriate level of redundancy and throughput.

Automation islands – PLC’s local controllers (network nodes) – equipped with radio transceivers are connected to a single OPC server – CommServer by CAS. This fully configurable OPC server provides a multi-protocol, multi-medium and multi-channel redundant access to the data of the process control device. To ensure short response time and effective utilization of the communication channels throughput, unique scheduling and scan on demand algorithms were implemented.

CommServer can use many protocols simultaneously and provide redundant links. Any user can define logical sets of devices (segments) with common addresses or scanning rules. New protocols can be added easily by plug-ins. It provides the possibility of using various communication media simultaneously, including copper and fiberoptic wires, digital radio, ISDN, GSM/GPRS, satellite and Internet.

CommServer offers a unique algorithm of scheduling the data cache update, basing on original solutions in the field of multithreaded technology. The unique scanning on demand algorithm manages dynamic priority allocation by using common scanning rules defined for tags grouped into sets.

The radio base station locations were chosen to allow communication with the most important nodes using all of them. For these nodes, redundant communication paths were configured. Failure of one base station causes the immediate use of a redundant one. All redundant communication paths are periodically checked to verify their availability.

The control process requires that many process variables are transferred between nodes and also from power plants local control subsystems. This was fulfilled using OPCClientTransporter Rel 1.0. software by CAS. This software allows to define transactions for groups of tags located on different OPC servers. Each transaction can process selected input tags to calculate the current value of an output tag, e.g. scaling, addition, multiplication, assigning constants and not a value. It is also possible to define a transaction archiving data in SQL data bases.

When controlling energy streams distribution produced by the plants (hot water with flow of up to 7000 m3/h) all components of the system must be monitored in real time – including communication network. Each of the software provides diagnostic and statistics information via OPC tags, therefore can be monitored by HMI and SCADA stations.

Such system cannot work alone. Thanks to the open and coherent infrastructure it was seamlessly integrated with the following systems: power consumption prediction, geographical information, remote control of water main pumping stations, power plant monitoring systems. All systems share a wall visualization to provide ergonomic human process interface.

Using OPC as the core technology we have proven that the obtained structure is open, robust (because of built-in redundancy) and allows a straightforward integration process.

## Read more to get the whole story

- Mariusz Postol, [Object Oriented Internet](https://ieeexplore.ieee.org/abstract/document/7321562), [3rd International Conference on Innovative Network Systems and Applications](https://fedcsis.org/2015/inetsapp), 2015, [IEEE Xplore Digital Library](https://ieeexplore.ieee.org/abstract/document/7321562) [![DOI](https://img.shields.io/badge/DOI-10.15439%2F2015F160-blue)](https://fedcsis.org/proceedings/2015/pliks/160.pdf)

### What is a DOI

A DOI is a unique and permanent number used to identify digital content. DOIs provide a reliable link to your work online, making it easy for others to cite you. Please make a note of your DOIs for future reference.

To learn more about DOI visit the [DOI® Handbook](https://www.doi.org/hb.html)
 