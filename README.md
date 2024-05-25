# BL-okawango-oss
Host based blocklist of malicious domains

Pi-hole list: 

https://raw.githubusercontent.com/okawango-oss/BL-okawango-oss/main/BL-okawango-oss

# Over blocking?
Mit ca. 4 Millionen Blocklisteneinträgen werden durchschnittlich nur 12,3% geblockt. Es wurden dazu die top 10.000 domains weltweit im batch mode getestet (cloudflare radar top domains). 12,3 % ist eine moderate Anzahl von Blockierungen.

![Bildschirmfoto 2024-05-25 um 06 57 40](https://github.com/okawango-oss/BL-okawango-oss/assets/125760839/7090d149-4c5c-41d9-8a61-35dfdfa96976)

![Bildschirmfoto 2024-05-25 um 09 00 48](https://github.com/okawango-oss/BL-okawango-oss/assets/125760839/d8474992-dadb-48a1-9db0-3d09f6d4d1c1)

# Over blocking testen:

## Vorbereitungen:
Pi-hole GUI -> Settings/System 
##### Flush logs

Pi-hole GUI -> Settings/DNS
##### Rate-limiting auf 100.000 pro 10 sec temporär hochsetzen, um ungewollte Pausen zu vermeiden

##### $ sudo su


## Download cloudflare top 10.000 weltweite domains
[https://radar.cloudflare.com](https://radar.cloudflare.com/domains)
##### $ nano top_10000_domains.txt
##### $ copy paste der 10.000 domains vom Download in die geöffnete Datei
##### $ ctrl + o und ctrl + x zum Speichern und Schließen

## DNS starten im batch mode für DNS type A
##### $ dig -f top_10000_domains.txt -t A +short
