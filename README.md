# KMU Netzwerk

## IP-Adressierungskonzept

### Netzwerkübersicht
- **Netzwerk:** `192.168.10.0/24`
- **Subnetzmaske:** `255.255.255.0`
- **Gateway (Router):** `192.168.10.1`

### VLANs

#### VLAN 10 – Admin (`192.168.10.0/26`)
- **IP-Bereich:** `192.168.10.1 – 192.168.10.62`
- **Gateway:** `192.168.10.1`
- **Geräte:**
  - **Router:** `192.168.10.1`
  - **Server (DNS/DHCP):** `192.168.10.2`
  - **Admin-PC 1:** `192.168.10.3`

#### VLAN 20 – Mitarbeiter (`192.168.10.64/26`)
- **IP-Bereich:** `192.168.10.65 – 192.168.10.126`
- **Gateway:** `192.168.10.65`
- **Geräte (via DHCP):**
  - **Client 1:** `192.168.10.66` (dynamisch)
  - **Client 2:** `192.168.10.67` (dynamisch)

#### VLAN 30 – Gäste (`192.168.10.128/26`)
- **IP-Bereich:** `192.168.10.129 – 192.168.10.190`
- **Gateway:** `192.168.10.129`
- **Geräte (via DHCP):**
  - **Gastgerät 1:** `192.168.10.130` (dynamisch)
  - **Gastgerät 2:** `192.168.10.131` (dynamisch)

#### Management-Netzwerk (`192.168.10.192/28`)
- **IP-Bereich:** `192.168.10.193 – 192.168.10.206`
- **Geräte:**
  - **Switch:** `192.168.10.194`
  - **Router-Management-Interface:** `192.168.10.195`

#### Reservierte Adressen
- `192.168.10.250–254` für zukünftige Geräte
- `192.168.10.255` = Broadcast-Adresse

---

## Netzwerktopologie für ein KMU-Netzwerk
1. **Internet → Router**
2. **Router → Firewall (optional)**
3. **Firewall → Switch**
4. **Switch → Server, Access Point, Clients**

## Namenskonzept
- **Server:** `med-ZRH-SRV-01`
- **Switch:** `med-ZRH-SW-01`
- **Access Point:** `med-ZRH-AP-01`
- **PCs/Clients:** `med-ZRH-CL-01`
- **Drucker:** `med-ZRH-PR-01`

## Zugriff auf Router
- **Web-Oberfläche:** `192.168.1.1`
- **Standard-Passwort:** `password` (ändern empfohlen!)

## VLANs erstellen
1. Menü **„VLAN“** oder **„LAN-Einstellungen“** öffnen
2. **VLAN-ID und Name** definieren
3. **VLANs speichern**

---

## Remote Desktop (RDP) installieren und konfigurieren

### 1. RDP auf dem Server aktivieren
- **Server-Manager** öffnen und zu **„Lokaler Server“ → „Remote Desktop“** navigieren.
- **„Remoteverbindungen zulassen“** aktivieren.

### 2. Benutzer für RDP-Zugriff hinzufügen
- Rechtsklick auf **„Dieser PC“ → „Eigenschaften“ → „Remoteeinstellungen“**.
- Unter **„Remotedesktop-Benutzer“** Benutzer hinzufügen.

### 3. Vom Client aus verbinden
- **„Win + R“** drücken und **„mstsc“** eingeben.
- **Server-IP** eingeben und auf **„Verbinden“** klicken.

---

## Netzwerk-Monitoring

### 1. Wireshark als Monitoring-Tool
- **Wireshark** installiert zur Analyse des Netzwerkverkehrs und Überwachung des Datenaustauschs.

### 2. Internes Webportal zur Netzwerküberwachung

#### Einrichtung des Webservers
- Installation und Konfiguration von **IIS**.

#### Entwicklung der Weboberfläche
- Erstellung einer **HTML-Seite** als Benutzeroberfläche.

#### Integration von Monitoring-Tools
- Einbindung von **Netzwerküberwachungstools** zur Echtzeit-Statusanzeige.

#### Log-Management
- Abruf und Visualisierung von **Server-Logs** im Webportal.

#### Zugriffskontrolle
- **Berechtigungen** konfigurieren, um den internen Zugriff zu beschränken.

---

## Windows Server 2022 – AD Servernamen ändern

### 1. Aktuellen Servernamen prüfen
```powershell
hostname
```

### 2. Falls DC → Degradieren & Neustart
- Server-Manager → Rollen und Features entfernen → AD DS deinstallieren
- Falls Mitgliedsserver: `sysdm.cpl` → Arbeitsgruppe setzen → Neustart

### 3. Servernamen ändern
#### GUI:
- `sysdm.cpl` → Computername → Ändern → Neustart

#### PowerShell:
```powershell
Rename-Computer -NewName "NeuerServerName" -Restart
```

### 4. Server wieder in Domäne aufnehmen
- `sysdm.cpl` → Domäne beitreten → Neustart

### 5. DNS & AD prüfen
```powershell
hostname
nslookup NeuerServerName
repadmin /showrepl
dcdiag /v
