# Splunk-to-Phantom-Portscan-PoC
Basic PoC code for Splunk exported CSV lookup table to Phantom event &amp; artifact.

This script is a simple yet effective PoC of Splunk + Phantom integration. In case of any port-scanning activity detected, firewall creates a simple log to Splunk. I have created an alert in Splunk, in case of port-scanning activity log received on Splunk, it exports this record as CSV file (portscan.csv in script, example data in splunk_alert.csv) and runs following script. 

Basically this script does: 
  1) it creates a blank new container (event) in Phantom and gets generated "container_id" (which is unique event ID in Phantom. We will use this ID to create artifacts under newly-generated event) 
  2) Then it gets Splunk log file from portscan.csv and fetches source_IP address of the attack. 
  3) Then it creates a new artifact under newly-created container and pushes src_ip from csv log under Phantom event as indicator. 
  
Script is not suitable for your own usage out-of-the-box but will give you an idea about creating artifacts and events in Phantom.
