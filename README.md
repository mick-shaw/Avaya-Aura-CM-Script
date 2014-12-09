Avaya-Aura-CM-Script
====================
There are a few data elements that cannot easily be gathered through the traditional system administration terminal or System Manager. I find it useful to perform an audit of all of your Avaya H323 endpoints before and after upgrades. In the event you lose an endpoint, knowing the mac-address can significantly help you track down the endpoint to a specific port. Unfortunately, the only means of doing this is to perform a status station on each and every endpoint - not very practical or efficient when you're dealing with thousands of endpoints.

In addition, there is useful information about the end-points that can only be gathered via SNMP. For example, the serial number of the phone, the list of alternate gate keepers, active DHCP server, etc. Unless you have expensive management tools already actively managing these devices, it can be extremely difficult to gather this information.

This program in its current form can be used to generate a CSV report of the following elements:

* Extension
* Serial number
* Configured set-type
* IP-Address
* Service State
* Connected Set-type
* MAC-Address
* Firmware version

The first subroutine performs a 'list-registered' command against a given Communication Manager instance. The second subroutine performs a status station for each extension gathered in the list-registered sub-routine. The third subroutine performs an snmp get on each endpoint using the ip-address gathered int he list-registered subroutine.

Any of the subroutines can be modified to gather alternative data elements. However, the Avaya OSSI labels the data elements as hexadecimal field identifiers (FIDs). Therefore, you may need to run a few test commands to determine what FIDs you want.

The $MIB1 value in the SNMP subroutine can be changed to any Avaya endpoint OID you want to snag.

The "$PBX" variable defines the CM instance. The connection details of each instance are defined in the OSSI Module (cli_ossi.pm).

The cli_ossi module included is a modified version of Ben Roy's Definity.pm which is used to interface with Communication Manager via XML Interface. https://github.com/benroy73/pbxd.

The SNMP modules included should not be confused with the SNMP perl modules found in CPAN (i.e. Net::SNMP). The modules I've included were previously maintained by http://www.switch.ch/misc/leinen/snmp/perl/ They are now publicly available on code.google.com/p/snmp-session The entire package which includes all three modules can be downloaded from https://snmp-session.googlecode.com/files/SNMP_Session-1.13.tar.gz
