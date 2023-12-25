# Template to monitor winpower UPS with Zabbix over web server

This is simple template that connects to winpower web server and gets data from it. It is tested with Winpower 6.0.0.1. Note that this template is not using Zabbix agent, so you don't need to install it on host with Winpower. 

Template is created for Zabbix 6.0, but you can esily adapt it to older versions, that support http agent items and Javascript(and JSONpath) preprocessing.

Template is not accounting for multiple UPSes, so if you have more than one, you will probably need to create separate template with LLD rule for each UPS.

## Installation
Before using this template, you will need to enable web server in Winpower. To do this, go to Monitor - Web Server Control. If everything is okay, you can open https://localhost:8888/ in your browser and see simple web interface of Winpower.

Then import template to Zabbix and link it to host. Assuming you didn't change default port, you will need to change macro {$UPS.URL} to appropriate value.

## Template macros
All macros is pretty self-explanatory. The only values that may be a little confusing are `{$UPS.INPUT.VOLTAGE.[LOW\HIGH]}` and `{$UPS.INPUT.FREQ.[LOW\HIGH]}`. They are based on values from GOST 12.1.006-84 (Russian standard for voltage and frequency). You can change them to appropriate values for your country.
