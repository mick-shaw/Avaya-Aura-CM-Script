Avaya-Aura-CM-Script
====================
 MAC Address, Serial Number and Firmware Report for Avaya
# IP Endpoints
#
# This script will run a list-registered command followed
# by a status station command using the output of the
# list-registered command.  Finally, it will perform a 
# snmpget using the SNMP_Session module.
#
#
# "$PBX" variable defines the CM instance. The connection
#  details of each instance are defined in the OSSI
#  Module (cli_ossi.pm).
#
# Note: If the $PBX variable changes, the OSSI Module must
#       be updated as well
#
# Note: 2420 Handsets registered as IP-Agents are excluded
