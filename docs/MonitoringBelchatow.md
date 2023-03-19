# Monitoring System for an Open Pit Control Center

## System Description

Appropriate selection of a control system for a complex industrial process is very difficult. The main part of control is often retained by men and, then, the computer function is limited to adequate determination and provision of comprehensive information concerning the plant operation status in a readable form to enable making optimal decision by a dispatcher. This kind of computer system has been applied to the open pit in Bełchatów Poland. It is one of the largest brown coal mines all over the world, with coal output of 38500000 Mg and overlay output of 125 Mm3 per annum. Coal is conveyed to a 4320MW power plant. The exploitation process employs the following machines:

- 13 excavators mining coal and overlay,
- 6 dumping conveyers scattering overlay onto a dumping ground,
- 4 belt conveyers transporting coal to the power plant,
- 5 loader - dumpers working in coal deposits.

Each machine has, among others, a measurement device providing an instantaneous output value and a current machine state (work/standstill) signal. For excavators there are available signals indicative of coal or overlay digging and for loader-dumpers - signals of conveying direction. Directly accessible signals have been insufficient for efficient manual control. Available information should take the following form, for convenience of the dispatcher:

- total output for each machine taking into account the kind of winning (coal/overlay) for excavators and loading/dumping for loader-dumpers,
- total working time measured from the beginning of a shift for each machine and average productivity from the beginning of a shift for each machine,
- mean productivity measured within ten-minute periods for the previous hour,
- beginning and length of downtime for each machine.

The part of this information is important as it is used in economic accounts. Current information has to be provided continuously using a radio link. A dedicated real time computer system has been designed for this critical task. It measures signals and processes them to display required information in a readable form on a CRT display and it prints out reports. A report is printed out at request and automatically after the end of each shift. Considering the place where the computer system takes over the control hierarchy, its reliability is of decisive importance. Therefore, there were designed two identical computers working simultaneously but independently of each other. This ensures an increased hardware reliability. The next step towards the reliability improvement is a special algorithm construction. The computer system is designed to acquire and process data, and finally to display and print appropriate information describing the process state independently of the technologic and energy consumption points of view. Output data enable the dispatcher to control the work of all mining devices and guarantee:

- appropriate amount and quality of coal fed to the power station
- minimizing of energy consumption
- operation just below an ordered power limit

## Installation structure

The computer system consists of the following (fig):

- a computer responsible for the acquisition and processing of data (APD),
- a computer responsible for monitoring of the current state of the process (MS),
- a dispatcher workstation (DWS).

The mentioned computers exchange data using the local network. The data acquisition and processing computer (APD) reads data from sensors at discrete intervals, processes them and saves the description of the mining process current state results. A system printer can be connected optionally to APD or MS. The result data from APD are provided to both computers by the local network. The monitoring station (MS) is responsible for displaying vital information about the current mining state on the 6 following CRT's designed for:

- monitoring of coal output
- monitoring of mining devices downtime (beginning of work and length of standstills for each machine)
- measuring of mean productivity within ten-minute periods for the previous hour and one-hour periods for the whole current shift
- monitoring of coal quality
- monitoring of power and energy consumption by mining devices
- monitoring of power and energy consumption by the whole mine

To increase reliability, monitoring stations equipped with additional CRT's can work as dispatcher workstations. In that case the possibility of standstill description in not available. The dispatcher workstation makes system configuration possible and enables the input of process parameters and data not available from sensors, e.g. substitution values for selected signals, standstill reasons, mining device names, power limits, current time and date, etc. Monitoring of the power supply system is divided into:

- monitoring of digger and conveyor sets,
- monitoring of dumping conveyor sets,
- coal conveyor feeding the power plant,
- mine drainage system,
- additional supporting devices and buildings,
- whole mine.

If ordered power is exceeded the system warns and aids reduction of current power.

## Read more to get the whole story

- Arendt, Daniel; Postol, Mariusz. (1990). [Realtime multiprogramming system for mine control centre.](https://www.researchgate.net/publication/256398395_Realtime_multiprogramming_system_for_mine_control_centre) Microprocessors and Microsystems. 14. 39–46. DOI `10.1016/0141-9331(90)90012-K`.

### What is a DOI

A DOI is a unique and permanent number used to identify digital content. DOIs provide a reliable link to your work online, making it easy for others to cite you. Please make a note of your DOIs for future reference.

To learn more about DOI visit the [DOI® Handbook](https://www.doi.org/hb.html)