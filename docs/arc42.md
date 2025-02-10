# Dokumentation nach arc42 
## Einführung und Ziele
Dieses PoC System zeigt eine beispielshafte Verarbeitung von Telemetrie von E-Autos auf deutschen Straßen

### Anforderungen
Das System umfasst eine komplette Telemetrie Pipeline von Erzeugung bis zur Visualisierung
- Ein Agentensystem welches E-Autos simuliert und periodisch (synthetische) Telemetriedaten übermittelt
- Ein MQTT-Server welcher die Telemetriedaten verarbeitet
- Eine Anwendung welche die Telemetriedaten übernimmt und in eine Datenbank speichert
- Eine Datenbank welche die Telemetriedaten speichert
- Eine Oberfläche in welcher die Telemetrie daten analysiert werden kann

### Qualitätsziele
- Skalierbarkeit: Das System soll auch mit steigender Last und Peaks in der Last zurecht kommen
- Robustheit: Ein Ausfall einzelner Komponenten hindert führt nicht zum totalen Systemausfall und das System kann sich
sich wieder aus diesen Zustand befreien
- Operability: Das System ist einfach verständlich und kann einfach benutzt werden

## Randbedingungen
- Das System benutzt möglichst Open Source Komponenten
- Die Anwendung welche die Daten von MQTT in die Datenbank schreibt muss reaktiv programmiert sein und quarkus benutzen
- Alle Komponenten welche mit der Quarkus Anwendung in Berührung kommen müssen einen reaktiven Client unterstützen

## Kontextabgrenzung
Das System empfängt Telemetriedaten über MQTT, verarbeitet sie und speichert sie in einer NoSQL-Datenbank. 
Eine Visualisierungskomponente greift auf diese Daten zu.

## Lösungsstrategie
- Das System wird möglichst als Gesamtpaket ausgeliefert
- Die Auslieferung soll mittels Continous Deployment geschehen
- Die Anbindung der Daten im MQTT-Broker läuft über QoS/1
- Alle Anwendungen laufen möglichst ohne Kontext, sodass diese gut horizontal skaliert werden können

