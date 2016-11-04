# Graylog GROK extractors for Cisco Firepower
Graylog GROK extractors for Cisco Firepower **Intrusion events** and **Access Control** log (simple syslog, not estreamer)

firepower-access_control-extractor.json - **Access Control** log

firepower-intrusion-extractor.json - **Intrusion events** log

firepower-extractor.json - both **Intrusion events** and **Access Control** logs

![alt tag](http://i.piccy.info/i9/31db09a41a64693952cf821cd274e5f4/1477571240/103371/1059582/_Fh_fi00576graylog_firepower_extractor_scr1.png)

## Installation
1. Go to *System => Inputs*
2. Choose your Input and select *Manage extractors*
3. *Actions => Import extractors*
4. Paste a body of the extractor into a form.

###### Note
It is important that all your sensors and sources send in source addresses in the field with the same name. The standard *src_addr* naming scheme is used in this example. If source addresses are being sent with differing names, analysis will become quite painful. Please edit this extractor to change field names if needed.
