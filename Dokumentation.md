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
**5. Installation der Squid Proxy Pakete auf Pfsense** 
----
Um den Squid Proxy zu betreiben, mussten wir zu erst die Packages installieren.

![grafik](https://user-images.githubusercontent.com/89446419/134197647-cd3417fa-75b4-47ee-ba42-1f72d1d48049.png)
---
**6. Konfiguration des Squid Proxy Servers**
---
1. Als nächstes ist das Ziel den Proxy inbetrieb zu nehmen. Darum gehen wir in den Reiter: "Services > Squid Proxy Server" und legen die Grösse des Cache fest.

2. Als nächstes ist es nötig den Hacken unter: Squid General Settings zu setzen, das Interface und den Port zu definieren. In diesem Fall hatten wir als Interface LAN mit dem Port 3128 augewählt. Um den Zugriff der User zu gewährleisten, muss man zusätzlich noch den Hacken bei " Allow Users on Interface" rein tun, sodass die Users automatisch im gleichen Proxy LAN verbunden sind.
3. Im nächsten Schritt hat man nun die Möglichkeit, im Menu: "Squid Access Control List" mit Proxy, Internetwebsiten zu blocken.
4. Zum Schluss muss man noch die Destination IP und den entsprechenden Port definieren und auf der Firewall den Zugriff geben, dass der Internetverkehr über den Proxy Server laufen darf.
---
**7. Funktionalität**
---
Um den Squid Proxy zu testen, haben wir über ein Debian Client, der vom DHCP automatisch eine IP-Adresse zugewiesen bekommen hat, folgende Befehle getestet:
_ping 192.168.1.1_

_telnet 192.168.1.1 3128_

# Troubleshooting #
Beim Versuch die benötigten Packages für den Web-Proxy zu installieren, hatten wir das Problem, dass man über die Firewall, die Adresse: 8.8.8.8 und den Gateway nicht pingen konnten, obwohl eine Gültige IP-Adressen zugwiesen wurden. Beim wechslen des Anschlusses auf WAN von br0 auf ens18 konnte das Problem auch nicht gelöst werden.

![grafik](https://user-images.githubusercontent.com/89446419/134184334-b29296a1-9561-4c93-93ac-ab1d4a98eb0d.png)

Lösung: Die Internetverbindung konnte durch die erneute Installation eines NAT-WAN-Anschlusses und durch die anpassung einzelner Firewallregeln gelöst werden.
Durch ein MicroTik, der über ein Switch zwischen WAN zu Pfsense hinzugefügt wurde, konnte man feststellen, dass schlussendlich die Firewall regeln nicht offen waren, was die Verbindung blockierte. 

![grafik](https://user-images.githubusercontent.com/89446419/134189005-a5fc7417-b9a9-490a-a47b-80c72c046b85.png)






