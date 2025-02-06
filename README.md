# KMU Netzwerk

### IP-Adressierungskonzept

#### Netzwerkübersicht:
- **Netzwerk**: `192.168.10.0/24`
- **Subnetzmaske**: `255.255.255.0`
- **Gateway (Router)**: `192.168.10.1`

#### VLAN 10 – Admin (Subnetz: `192.168.10.0/26`)
- **IP-Bereich**: `192.168.10.1 – 192.168.10.62`
- **Gateway**: `192.168.10.1`
- **Geräte**:
  - Router: `192.168.10.1`
  - Server (DNS/DHCP): `192.168.10.2`
  - Admin-PC 1: `192.168.10.3`

#### VLAN 20 – Mitarbeiter (Subnetz: `192.168.10.64/26`)
- **IP-Bereich**: `192.168.10.65 – 192.168.10.126`
- **Gateway**: `192.168.10.65`
- **Geräte (via DHCP)**:
  - Client 1: `192.168.10.66` (dynamisch)
  - Client 2: `192.168.10.67` (dynamisch)

#### VLAN 30 – Gäste (Subnetz: `192.168.10.128/26`)
- **IP-Bereich**: `192.168.10.129 – 192.168.10.190`
- **Gateway**: `192.168.10.129`
- **Geräte (via DHCP)**:
  - Gastgerät 1: `192.168.10.130` (dynamisch)
  - Gastgerät 2: `192.168.10.131` (dynamisch)

#### Management-Netzwerk (Switch & Router-Management – `192.168.10.192/28`)
- **IP-Bereich**: `192.168.10.193 – 192.168.10.206`
- **Geräte**:
  - Switch: `192.168.10.194`
  - Router-Management-Interface: `192.168.10.195`

#### Reservierte Adressen:
- `192.168.10.250–254` für zukünftige Geräte
- `192.168.10.255` = Broadcast-Adresse

---

## Netzwerktopologie für ein KMU-Netzwerk:
1. **Internet → Router**
2. **Router → Firewall (optional)**
3. **Firewall → Switch**
4. **Switch → Server, Access Point, Clients**

## Namenskonzept
- **Server**: `med-ZRH-SRV-01` (Zürich, Server 01)
- **Switch**: `med-ZRH-SW-01`
- **Access Point**: `med-ZRH-AP-01`
- **PCs/Clients**: `med-ZRH-CL-01`
- **Drucker**: `med-ZRH-PR-01`

## Zugriff auf Router
- **Web-Oberfläche**: `192.168.1.1`
- **Passwort**: `password`

## VLANs erstellen:
1. Menü **„VLAN“** oder **„LAN-Einstellungen“** öffnen
2. **VLAN-ID und Name** angeben sowie den **IP-Bereich** definieren
3. **VLANs speichern**

---

## Remote Desktop (RDP) installieren und konfigurieren

### 1. RDP auf dem Server aktivieren
- Öffne den **Server-Manager** und navigiere zu **"Lokaler Server" → "Remote Desktop"**.
- Aktiviere **"Remoteverbindungen zulassen"**.

### 2. Benutzer für RDP-Zugriff hinzufügen
- Rechtsklick auf **"Dieser PC" → "Eigenschaften" → "Remoteeinstellungen"**.
- Unter **"Remotedesktop-Benutzer"** die gewünschten Benutzer hinzufügen.

### 3. Vom Client aus verbinden
- **"Win + R"** drücken und **"mstsc"** eingeben.
- Die **Server-IP** eintippen und auf **"Verbinden"** klicken.

---

## Monitoring-Tool
Ich habe **Wireshark** als Monitoring-Tool installiert, um den Netzwerkverkehr zu analysieren und den Datenaustausch zu überwachen.

## Internes Webportal zur Netzwerküberwachung und Log-Anzeige

### 1. Einrichtung des Webservers
- Installation und Konfiguration von **IIS**.

### 2. Erstellung der Weboberfläche
- Entwicklung einer einfachen **HTML-Seite** als Benutzeroberfläche.

### 3. Integration von Netzwerküberwachungstools
- Einbindung relevanter **Monitoring-Tools** zur Anzeige des Netzwerkstatus.

### 4. Log-Management
- Abruf und Darstellung von **Server-Logs** im Webportal.

### 5. Zugriffskontrolle
- Konfiguration der **Berechtigungen**, um den Zugriff intern zu beschränken.
