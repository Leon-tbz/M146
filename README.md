# M146 LB1

Einleitung 
<br>
Dieses Repo wurde erstellt, um die Inhalte des Moduls 146 an einem Ort zusammenzubringen.


<b>Teammitglieder</b>

Zeender Yanic 
<br>
Lennemann Noah
<br>
Rezek Leon

Inhaltsverzeichnis
---
![GitHub Logo](https://www.pro-fekt.de/media/image/31/70/44/pfSenseColorLogoRegisteredRGB.png)
5.VT-5: Web-Proxy mit pfsense 

Ziel ist es ein Web-Proxy mit pfsense zu realisieren. Der Internetverkehr (http und https) soll auf der pfsense analysiert und ausgewertet können (Stichworte: Squid, Lightsquid). Weiter gilt es alle Schritte nachvollziehbar zu dokumentieren. Mithilfe der Dokumentation soll eine Fachperson in der Lage sein das Projekt ohne Unklarheiten nachzubauen.

--- 
Die Präsentation beinhaltet:

o Einen Erfahrungsbericht

o Erklärung, welche Herausforderungen die Überwachung des SSL/TLS Datenverkehrs mit sich bringt.

----
#Dokumentation
---
**1. Installation**
---
Im ersten Schritt, mussten wir auf der Virtuellen Serverumgebung, die uns Herr Albrecht zur Verfügung gestellt haben, die einzelnen Komponenten installieren.
Dazu haben wir den Wan-Anschluss indem Fall die Wolke, die Pfsense Firewall, einen Switch und zwei Debianclients installiert. Bei der Pfsense Firewall musste man zusätzlich das Iso File installieren, um sie danach starten zu können. 

![grafik](https://user-images.githubusercontent.com/89446419/134162446-d5015b77-cc9f-4ae3-835c-db780d70301e.png)

---
**2. Konfiguration der Pfsense Firewall
---

