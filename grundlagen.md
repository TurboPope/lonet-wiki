## Netzstrukturen
Gewöhnlicher Weise sind mobile Endgeräte mit einer **infrastructure**-Verbindung an ein größeres, hierarchiches Netzwerk angebunden. Es gibt jedoch auch so genannte **ad-hoc**-Netze, bei denen mehrere Endgeräte ein kleines, abgeschlossenes Netzwerk mit einander bilden. Es wird unterschieden zwischen **single-hop ad-hoc**-Netzwerken, bei denen alle Geräte direkt mit einander verbunden sind, und **multi-hop ad-hoc**-Netzwerken, bei denen eine komplexere Gliederung vorliegt und in denen Geräte nicht unbedingt *direkt* mit einander verbunden sein müssen.

Ein **Wireless Sensor Network (WSN)** ist ein solches ad-hoc-Netzwerk mit vielen kleinen Sensor-Knoten und wird zum Beispiel zur Erkennung von Waldbränden verwendet.

Ein **Wireless Sensor Actuator Network (WSAN)** erweitert dieses Konzept um Knoten, die nicht nur messen, sondern auch direkt Aktionen ausführen können, zum Beispiel um bei großen Gebäuden automatisch die Fenster zu schließen (es gibt hier anscheinend keine tollen Beispiele).

In **Roboternetzen** können sich die Knoten zusätzlich selbstständig bewegen. Beispiel: Drohnen überwachen ein kontaminiertes Gebiet.


## Schwierigkeiten in Drahtlosnetzwerken
Ein charakteristisches Problem in Drahtlosnetzwerken ist die **Mehrwegeausbreitung** der übertragenen Signale. Diese kann durch eine Vielzahl von Ursachen hervorgerufen werden, die häufigste davon Reflektion des Signals an Oberflächen und damit Überlagerung des **Line of Sight (LOS)**-Signals mit phasenverschobenen Signalen. Dies führt zum typischen **Fading**-Verhalten von Drahtlosnetzwerken.

Zusätzlich können andere Übertragungen im Gebiet das Signal überlagern. Um solche großen **Kollisionsdomänen** zu vermeiden sind **multi-hop**-Netzwerke mit geringer Übertragungsreichweite pro Knoten sinnvoll.

Weiterhin schränkt die begrenzte **Batteriekapazität** die mögliche Sendeleistung ein. Um eine höhere **Energieeffizienz** zu erreichen können **Schlaf-Wach-Zyklen (sleep-cycles)** für die Übertragungskomponenten genutzt werden. Des weiteren können manche Berechnungen auf den Sensordaten bereits vor dem Weitersenden von Netzwerkknoten übernommen werden (**in-network-processing**).









**Pfadverlust**?
