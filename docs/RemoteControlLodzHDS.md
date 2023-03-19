# Remote Control of Lodz Municipal Heat Distribution System

Operation of the Central Dispatching Room (DSC) is aided by the following systems:

- GIS - Geographical Information System;
- TCH - source monitoring system (actually 3 power plants supplying hot water to central municipal heating network),
- SOC - remote control system of backbone pumping stations (pressure reduction stations) along with a simulator of the heat distribution network,
- KOM - remote control system of heat chambers.

Each of the mentioned subsystems works independently; data exchange between their components is provided by one of the two computer networks used: the general purpose corporate network (the main plant network available for all Departments) and the field network (a separate corporate network available only for the users, who have to access the process data). The Central Dispatching Room has access to both networks.

GIS has been developed on the basis of the SmallWorld software and allows inventory of the heat distribution network infrastructure and illustration of its current condition. The data are collected in the database in a geographical arrangement. In the Dispatching Room there are situated two GIS workstations, which provide full access to the data of that system.

The system of source monitoring consists of two workstations, which use SCADA software. The data are read by the field network from the similar stations situated at the sources end.

## Remote control of heat chambers

In the 19 selected network nodes, the system is to enable monitoring of network working parameters and unmanned remote control of the chambers fittings in order to switch over the supply areas from one to another individual heat source. Finally, the next 200 nodes are to be connected to the system.

In the chambers, the following functions are performed by remote control:

- control and monitoring of the sectional and bypass fittings condition,
- monitoring of the selected parameters, i.e. pressure and temperature,
- monitoring of missing availability for the electric circuit, controllers and fittings,
- monitoring of damages to the hydraulic system (flooding of the chamber and increase in humidity inside the chamber),
- monitoring of fires and burglaries,
- automatic power supply shutdown of all electric devices in the chamber, in danger of gas explosion or flooding of the drives in the chamber,
- remote control of the chamber supply switch as well as cabinet and chamber main switch.

After an analysis of propagation and requirements as to the channel throughput, it was assumed that the data digital transmission in the 400 MHz band would be the basic communication channel of the system, as for the system described above. Basing on digital simulations of propagation for several tall objects, where there are access points to the field network, an optimal location of the central data transmission station (SCk) was selected.

The subsystem concerned consists of:

- workstations (KOM),
- communication server (SBk),
- data transmission central station (SCk),
- database server (ORACLE),
- heat chambers controllers (Kxxx).

In the system there are provided two double-monitor workstations (KOM), which use Wizcon SCADA software. They are responsible for the performance of the system basic functions, i.e.:

- monitoring of the heat distribution network functioning,
- remote control of the fittings,
- recording of the most important process data values in their own database and external database,
- archiving of their own database,
- preparing of reports basing on the archival data acquired in the ORACLE database.

The communication server (SBk) is the main component responsible for communication in the system. It provides a data transparent transmission path between the workstations (KOM) and chamber controllers (K-xxx). Basing on the analysis of propagation, the central station of data transmission (SCk) was situated in a building in another city region, the radio modem was connected to SBk through a field network using device server. The SBk communication software was so designed as to make target communication for at least 200 nodes (chambers, exchangers, pumping stations, etc.) possible and provide connecting of data transmission backup channels in the future. In order to increase the territorial range, it is also possible to connect the next data transmission central stations to the communication server.

Communication witch such a big number of nodes through a relatively slow channel is possible due to implementation of a sophisticated algorithm of station scanning scheduling. The basic element of the algorithm is a dynamically variable scanning cycle for any station according to its current state. The scanning time is automatically changed as a result of configured events. Thus, all time constraints described above can be met.

The basic task of the system server is to manage the database designed to archive process data. The workstations are responsible for entering the data into the database in a cyclic way.

In the system concerned, the heat chambers are provided with programmable controllers. They are responsible for carrying out of all algorithms, which are initialized by the orders and set points remotely from DSC or locally from a control panel.

The controller of any chamber carries an algorithm of fittings control in one of the following modes:

independent separate control of the selected fittings,
sequential control of the chamber,
emergency closing of the section.
The controller software is responsible for an appropriate sequence of closing and opening of fittings in the chambers, while considering their current position. The dispatcher decides the order of closing down and starting up the next sections each time. The speed of fittings movement is chosen automatically in order to minimize undesirable rapid changes of pressure in the network and thereby provide stable operation of the sources. In the emergency mode, transition times are selected in such a way as to provide the quickest safe shutdown of any endangered section of the network.

In case of communication loss, the controller software starts to operate in the emergency mode, where all operations are carried out in such a way as to provide the safest functioning of the network.

The radio modem connected directly to the controller provides communication of the chamber with SCk.

## System Integration

All IT systems presented in the article have generally one purpose, i.e. improvement of effectiveness of the heat distribution network operation. From the point of view of the user their variety is of no importance and makes use of them difficult. In other words, their construction and functional properties should be maximally integrated and mutually consistent.

Considering the design, combining of system functions in one system and, consequently, developing systems with wider functionality create technical and organizational problems. Additionally, it decreases reliability and availability.

To meet these two contradictory requirements at the same time, i.e. maximum integration of the functions and keeping the systems size within reasonable limits, it is suggested that a three-plane cooperation of the systems be provided:

- common visualization
- central database and reporting system
- making process data values available between the systems

In 2002, in the Central Dispatching Room (CDS) there was installed a large-format visualization using solutions provided by Synelec. It consists of a wall display of 4 modules 67", which gives a picture of 273 x 205 cm, with resolution of 2048 x 1536 pixels. The modules are controlled by a dedicated controller. MASTERPIX can take pictures generated by the workstations of the particular systems. There are also installed applications of the clients of the selected systems, including the client of the GIS system.

Integration of the systems with the large-size visualization involved solving the problem of communication between systems. At first, for safety reasons, the SOC system was designed as a totally separated one. As it has been already mentioned, the common purpose corporate network is the communication layer for the GIS system. This network was not connected to the field network, also for safety reasons. Only the workstations of the source monitoring system (TCH) were connected to the field network.

The basic assumption of the project is that integration will not violate the autonomy of the systems and decrease the level of their separation. To meet this requirement, the VLAN and NAT technologies are used for communication.

NAT is used for connecting the corporate network to the field one. Thanks to such a solution, shielding of the field network access from the corporate network is achieved. However, access to the corporate network on the side of the field network is only possible from a separated virtual segments, so - except for computers operating on this segments - access to the corporate network on the side of the field network is completely separated.

Separation of access to the workstations of the SOC system on the side of the field network is provided by connecting them to the separated virtual segments, on which the MASTERPIX controller also operates. However, to make the data of the system available in the field network, there is installed a dedicated application server which reads the data from the workstations and publishes them on the field network.

The database server of the heat chambers remote control system should serve as a common working basis for all described systems. Such a solution will decrease neither the autonomy nor the safety of their operation because reading and entering into the database can be accomplished for each system independently. Relevant works are at the stage of making assumptions and developing its general outline.

The possibility of data exchanging between individual systems is another important issue at the point where they meet. It is a simple task if a uniform software platform has been used for applications of the workstations of the systems described, e.g. WIZCON. Data exchange between the GIS system and other systems requires modification of the former and introduction of communication mechanisms. Integration is possible as to:

- archival data included in the ORACLE database,
- current data rendered available by the communication server.

After a preliminary analysis it was found that access to the current data through the database server within a dozen or so seconds was an inefficient solution, because it led to a very great number of transactions and, consequently, overloading of the server. Therefore, it is assumed that the workstations of the GIS system be additionally provided with communication modules allowing direct reading of process data values from the communication server using open standard OPC. At present the project is scheduled to start at the beginning of the next year.

## See also

- [Remote Control Of Łódź Agglomeration Heat Distribution System](https://www.researchgate.net/publication/334251468_Remote_Control_Of_Lodz_Agglomeration_Heat_Distribution_System); DOI: `10.13140/RG.2.2.25755.00804/1`; CAS; 2005

### What is a DOI

A DOI is a unique and permanent number used to identify digital content. DOIs provide a reliable link to your work online, making it easy for others to cite you. Please make a note of your DOIs for future reference.

To learn more about DOI visit the [DOI® Handbook](https://www.doi.org/hb.html)