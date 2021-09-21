# Dokumentation #
---
**1. Installation**
---
Im ersten Schritt, mussten wir auf der Virtuellen Serverumgebung, die uns Herr Albrecht zur Verfügung gestellt haben, die einzelnen Komponenten installieren.
Dazu haben wir den Wan-Anschluss indem Fall die Wolke, die Pfsense Firewall, einen Switch und zwei Debianclients installiert. Bei der Pfsense Firewall musste man zusätzlich das Iso File installieren, um sie danach starten zu können. 

![grafik](https://user-images.githubusercontent.com/89446419/134162446-d5015b77-cc9f-4ae3-835c-db780d70301e.png)

---
**2. Konfiguration der Pfsense Firewall**
---
Nach dem man die Pfsense starten konnte, hatte man die Möglichkeit, das Netzwerkinterface zu konfigurieren. Mit der Auswahl "1" konnte man die Zuordnung des externen WAN und internen LAN Inter-faces anpassen. Im nächsten Schritt konnte man mit der Auswahl "2" im Terminal die IP-Adresse der Firewall konfigurieren. Da, das Netzwerk: 192.168.23.0 ist, haben wir uns für die Pfsense auf die IP: 192.168.23.134 entschieden. 

![grafik](https://user-images.githubusercontent.com/89446419/134164514-d5c9cd44-6c18-415f-8acf-dc3da922cd34.png)

---
**3. Zugriff/Konfiguration im Webinterface**
---
Nachdem erfolgreichen Aufsetzen der Pfsense, hat man nun die Möglichkeit, mit der gesetzten IP-Adresse per Browser Zugriff auf das Webinterface zu erhalten. Nun hat man folgende Möglichkeiten: 
- Statusabfragen des Netzwerktraffics
- Erstellung von Firewallregeln
- Erstellen von VLANs usw.

![grafik](https://user-images.githubusercontent.com/89446419/134165610-f87976c8-7430-467c-ab2c-f0873417010b.png)
---
**4. OPT-Anschluss**
---
Um Zugriff auf das Internet zu haben, musste man zusätzlich einen OPT-Anschluss erstellen, der als WAN-Anschluss dient.
Nach der Erstellung des Anschlusses musste man in den Firewalleinstellungen, eine neue Firewall-Regel erstellen und die Protokolle zulassen, sodass man nach dem wechseln des WAN-Anschluss immer noch Zugriff auf das Webinterface hat.

![grafik](https://user-images.githubusercontent.com/89446419/134173182-89aad81d-da4a-4b1b-952d-0a4417a5b76c.png)

---

