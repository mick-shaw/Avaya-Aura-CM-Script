Avaya-Aura-CM-Script
====================
 MAC Address, Serial Number and Firmware Report for Avaya IP Endpoints

There are a few data elements that cannot easily be gathered
through the traditional system administration terminal or System Manager.
It's useful to perform an audit of all of your H323 IP-Phones.
For me, it's useful to gather mac-addresses before a sytem or firmware upgrade.
In the event you lose a phone, knowing the mac-address allows you to track
down the phone to a specific port.Unfortunately, the only means of doing this 
is to peform a status station on each and every IP-endpoint.  

In addition, there is useful information about the end-points 
that can only be gathered via SNMP.  For example, the serial number of 
the phone, the list of alternate gate keepers, active DHCP server, etc.

This script can be used to generate a CSV report of the following elements:

1) Extension
2) Serial number
3) Configured set-type
4) IP-Address
5) Service State
6) Connected Set-type
7) MAC-Address
8) Firmware version

The first subroutine performs a 'list-registered' command against a 
givenvCommunication Manager instance.  The second subroutine performs
a status station for each extension gathered in the list-registered 
sub-routine. The third subroutine performs an snmp get on each endpoint
using the ip-address gathered int he list-registered subroutine.

Any of the subroutines can be modified to gather alternative
data elements.  However, the Avaya OSSI labels the data elements
as hexadecimal field identifiers (FIDs).  Therefore, you may need
to run a few test commands to determine what FIDs you want.

The $MIB1 value in the SNMP subroutine can be changed to
any Avaya endpoint OID you want to snag.

The "$PBX" variable defines the CM instance. The connection
details of each instance are defined in the OSSI
Module (cli_ossi.pm).

The cli_ossi module listed below is a modified version of 
Ben Roy's Definity.pm which is used to interface with 
Communication Manager via XML Interface.
https://github.com/benroy73/pbxd.

SNMP LIBRARY
The following modules should not be confused with the 
SNMP modues perl modules found in CPAN (i.e. Net::SNMP).
These modules were previously maintained 
by http://www.switch.ch/misc/leinen/snmp/perl/ They are now 
publicly available on code.google.com/p/snmp-session
The entire package which includes all three modules can be downloaded
modules can be downloaded from
https://snmp-session.googlecode.com/files/SNMP_Session-1.13.tar.gz
