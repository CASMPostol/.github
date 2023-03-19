# Integration of GIS and Remote Control and Monitoring Systems for Lodz Heating Municipal System

The purpose of the project is to integrate a GIS application (based on Smallworld engine) with industrial automation systems at the Heat & Power Generating Plants Group in Lodz (ZEC Lodz S.A.). Due to the integration, real-time display of process data from the following systems on GIS screens is possible:

- Monitoring of heat sources (i.e. 3 heat & power generating plants of ZEC Lodz S.A., of the total heat output of 2560MW);
- Remote control system of valves in heat chambers (19 heat chambers in key locations of Lodz heat distribution system);
- Monitoring of Smulsko Heat Exchanger Plant (a big heat exchanger plant providing heat for an estate of detached houses);
- Radio remote control system of pressure reduction stations (SOC) (two stations).

In order to ensure a reliable and open solution, technologies based on the following standards are used to integrate all components:

- OPC – advanced communication standards for industrial process control.
- SQL (Structured Query Language) and Oracle database – a standard language to query the data bases.
- XML (eXtensible Markup Language) – a standard, very flexible text format, originally designed to meet the challenges of large-scale electronic publishing.
- HTTP (HyperText Transport Protocol) – a text protocol of information exchange – a standard one for e.g. web browsers.
- SOAP (Simple Object Access Protocol) – a text protocol providing access to and calling of remote ob-ject functions.
- WSDL (Web Services Description Language) - is an XML format for describing network services as a set of endpoints operating on messages containing either document-oriented or procedure-oriented information.

Finally, the software provides a safe, flexible and optimal way to access the process from all systems it cooperates with and acquires data from.

## System architecture

A client station of the GIS system acquires data from OPC servers, installed in individual remote control & monitoring systems (OPC servers as components of Wizcon applications, an OPC server of a BUSSSniffer computer and a base station - collecting data from remote control & monitoring systems of the heat chambers, Smulsko Heat Exchanger Plant and SOC, based on an OPC server Commserver), additionally, data on modifications made to the heat chamber fittings are transmitted using advanced mechanisms of buffers.

Exchange of information between the GIS system, the remote control & monitoring system can be divided into two elements:

- Reading of actual, current values of measuring points and system control.
- Updating of the GIS system database on modifications to fittings in individual chambers.

The integration requires utilization or establishment and configuration of the following communication links:

- Base Station – heat chambers – the existing connections based on SBUS serial communication proto-col are used.
- Base Station – Smulsko – the existing connections based on SBUS serial communication protocol are used.
- Base Station – Base Station SOC – a new serial connection and SBUS protocol are used. The Base Station SOC is configured as a slave station on the next channel, from which the Base Station (CommServer) reads process data.
- Base Station – CDC EC2 and EC3 – there is used the OPC connection based on OPC servers of Wizcon application, configured previously.
- Base Station – CDC EC4 – a computer and BUSSniffer software are installed, that passively acquire data from SBUS local link and make them available remotely through an OPC server.
- Base Station – GIS Application – Oracle Data Base – there is installed an OPC client (DataPorter™ with OPC2GISSMALLWORLD and OPC2SQL modules), that makes the process data available through Internet services based on HTTP/SOAP protocols and makes recording in the data-base possible.
