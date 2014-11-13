Avaya-Aura-CM-Script
====================
 MAC Address, Serial Number and Firmware Report for Avaya IP Endpoints

This script will run a list-registered command followed 
by a status station command using the output of the
list-registered command.  Finally, it will perform a 
snmpget using the SNMP_Session module.

The "$PBX" variable defines the CM instance. The connection
details of each instance are defined in the OSSI
Module (cli_ossi.pm).

The cli_ossi module listed below is a modified version of 
Ben Roy's Definity.pm which is used to interface with 
Communication Manager via XML Interface.
https://github.com/benroy73/pbxd

SNMP LIBRARY
The following modules should not be confused with the 
SNMP modues perl modules found in CPAN (i.e. Net::SNMP).
These modules were previously maintained 
by http://www.switch.ch/misc/leinen/snmp/perl/ They are now 
publicly available on code.google.com/p/snmp-session
The entire package which includes all three modules can be downloaded
modules can be downloaded from
https://snmp-session.googlecode.com/files/SNMP_Session-1.13.tar.gz
