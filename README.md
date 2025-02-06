# KMU Netzwerk 

IP-Adressierungskonzept
 Netzwerkübersicht:
•	Netzwerk: 192.168.10.0/24
•	Subnetzmaske: 255.255.255.0
•	Gateway (Router): 192.168.10.1
VLAN 10 – Admin (Subnetz: 192.168.10.0/26)
•	IP-Bereich: 192.168.10.1 – 192.168.10.62
•	Gateway: 192.168.10.1
•	Geräte:
o	Router: 192.168.10.1
o	Server (DNS/DHCP): 192.168.10.2
o	Admin-PC 1: 192.168.10.3
VLAN 20 – Mitarbeiter (Subnetz: 192.168.10.64/26)
•	IP-Bereich: 192.168.10.65 – 192.168.10.126
•	Gateway: 192.168.10.65
•	Geräte (via DHCP):
o	Client 1: 192.168.10.66 (dynamisch)
o	Client 2: 192.168.10.67 (dynamisch)
VLAN 30 – Gäste (Subnetz: 192.168.10.128/26)
•	IP-Bereich: 192.168.10.129 – 192.168.10.190
•	Gateway: 192.168.10.129
•	Geräte (via DHCP):
o	Gastgerät 1: 192.168.10.130 (dynamisch)
o	Gastgerät 2: 192.168.10.131 (dynamisch)
Management-Netzwerk (Switch & Router-Management – 192.168.10.192/28)
•	IP-Bereich: 192.168.10.193 – 192.168.10.206
•	Geräte:
o	Switch: 192.168.10.194
o	Router-Management-Interface: 192.168.10.195
Reservierte Adressen:
•	192.168.10.250–254 für zukünftige Geräte
•	192.168.10.255 = Broadcast-Adresse

Netzwerktopologie für ein KMU-Netzwerk:
1.	Internet → Router
2.	Router → Firewall (optional)
3.	Firewall → Switch
4.	Switch → Server, Access Point, Clients
Namens Konzept 
•	Server: med-ZRH-SRV-01 (Zürich, Server 01)
•	Switch: med-ZRH-SW-01
•	Access Point : med-ZRH-AP-01
•	PCs/Clients : med-ZRH-CL-01
•	Drucker: med-ZRH-PR-01
•	Zugriff auf Router
•	Web-Oberfläche 192.168.1.1
passwort: password
VLANs erstellen:
•	Menü „VLAN“ oder „LAN-Einstellungen“ öffnen
VLAN-ID und Name angeben und die range
VLANs speichern


Remote Desktop (RDP) installieren und konfigurieren
1.	RDP auf dem Server aktivieren
o	Öffne den Server-Manager und navigiere zu "Lokaler Server" → "Remote Desktop".
o	Aktiviere "Remoteverbindungen zulassen".
2.	Benutzer für RDP-Zugriff hinzufügen
o	Rechtsklick auf "Dieser PC" → "Eigenschaften" → "Remoteeinstellungen".
o	Unter "Remotedesktop-Benutzer" die gewünschten Benutzer hinzufügen.
3.	Vom Client aus verbinden
o	"Win + R" drücken und "mstsc" eingeben.
o	Die Server-IP eintippen und auf "Verbinden" klicken.
