# graylog-extractor-firepower
Graylog GROK extractors for Cisco Firepower **Intrusion events** log (simple syslog, not estreamer)

Utilizes GROK patterns from https://marketplace.graylog.org/addons/407e8aa2-67b2-41a7-9bf5-9fc7f7d3915b

![alt tag](http://i.piccy.info/i9/31db09a41a64693952cf821cd274e5f4/1477571240/103371/1059582/_Fh_fi00576graylog_firepower_extractor_scr1.png)

## Installation
1. Go to *System => Inputs*
2. Choose your Input and select *Manage extractors*
3. *Actions => Import extractors*
4. Paste a body of the extractor into a form.

## On Cisco Firepower
http://www.cisco.com/c/en/us/td/docs/security/firepower/60/configuration/guide/fpmc-config-guide-v60/Configuring_External_Alerting_for_Intrusion_Rules.html#ID-2212-000000f8

I use and section **Configuring Syslog Responses**, Facility: *Alert*; Priority: *Alert*.
###### Note №1
In the section *Configuring Syslog Responses* I only could configure an IP of syslog server, not custom port. In my production environment I use dedicated syslog-ng server for log storage, archieving and retraslating some into graylog.

###### Note №2
It is important that all your sensors and sources send in source addresses in the field with the same name. The standard *src_addr* naming scheme is used in this example. If source addresses are being sent with differing names, analysis will become quite painful. Please edit this extractor to change field names if needed.

###### Note №3
I had some troubles with correct parsing end of a syslog line. Example:
`.........NAPPolicy: Balanced Security and Connectivity, HTTPResponse: 200`
Field `HTTPResponse` is optional. Unfortunately, a code below didn't work when a field `HTTPResponse` is absent:
`NAPPolicy: %{DATA:nap_policy}(, HTTPResponse: %{INT:statuscode})?`
