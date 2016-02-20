## Netzstrukturen
Gewöhnlicher Weise sind mobile Endgeräte mit einer **infrastructure**-Verbindung an ein größeres, hierarchiches Netzwerk angebunden. Es gibt jedoch auch so genannte **ad-hoc**-Netze, bei denen mehrere Endgeräte ein kleines, abgeschlossenes Netzwerk mit einander bilden. Es wird unterschieden zwischen **single-hop ad-hoc**-Netzwerken, bei denen alle Geräte direkt mit einander verbunden sind, und **multi-hop ad-hoc**-Netzwerken, bei denen eine komplexere Gliederung vorliegt und in denen Geräte nicht unbedingt *direkt* mit einander verbunden sein müssen.

Ein **Wireless Sensor Network (WSN)** ist ein solches ad-hoc-Netzwerk mit vielen kleinen Sensor-Knoten und wird zum Beispiel zur Erkennung von Waldbränden verwendet.

Ein **Wireless Sensor Actuator Network (WSAN)** erweitert dieses Konzept um Knoten, die nicht nur messen, sondern auch direkt Aktionen ausführen können, zum Beispiel um bei großen Gebäuden automatisch die Fenster zu schließen (es gibt hier anscheinend keine tollen Beispiele).

In **Roboternetzen** können sich die Knoten zusätzlich selbstständig bewegen. Beispiel: Drohnen überwachen ein kontaminiertes Gebiet.


## Schwierigkeiten in Drahtlosnetzwerken
Ein charakteristisches Problem in Drahtlosnetzwerken ist die **Mehrwegeausbreitung** der übertragenen Signale. Diese kann durch eine Vielzahl von Ursachen hervorgerufen werden, die häufigste davon Reflektion des Signals an Oberflächen und damit Überlagerung des **Line of Sight (LOS)**-Signals mit phasenverschobenen Signalen. Dies führt zum typischen **Fading**-Verhalten von Drahtlosnetzwerken.

Zusätzlich können andere Übertragungen im Gebiet das Signal überlagern. Um solche großen **Kollisionsdomänen** zu vermeiden sind **multi-hop**-Netzwerke mit geringer Übertragungsreichweite pro Knoten sinnvoll.

Weiterhin schränkt die begrenzte **Batteriekapazität** die mögliche Sendeleistung ein. Um eine höhere **Energieeffizienz** zu erreichen können **Schlaf-Wach-Zyklen (sleep-cycles)** für die Übertragungskomponenten genutzt werden. Des weiteren können manche Berechnungen auf den Sensordaten bereits vor dem Weitersenden von Netzwerkknoten übernommen werden (**in-network-processing**).


## Modellbildung

### Pfadverlust

Auf Grund der räumlichen Ausbreitung des Signals nimmt dessen Stärke exponentiell ab. Der Zusammenhang zwischen Sendeleistung und Empfangsleistung ist:

$$
S_{RX} = a \cdot \frac{P_{TX}}{d^\alpha}
$$

Wobei $S_{RX}$ die Empfangsleistung, $a$ ein Übertragungsfaktor, $P_{TX}$ die Übertragungsleistung, $d$ die Distanz und $\alpha$ die **Path-Loss Exponent** ist (*Nicht sicher ob korrekt*). Dieser **Pfadverlust** kann umgeformt in Dezibel ausgedrückt werden durch:

$$
PL(d) = 10 \cdot \alpha \cdot log_{10}(d) + X_\delta
$$

Wobei $X_\delta$ eine gaußsche Zufalls-Variable mit Varianz $\delta$ ist. Alternativ kann die Verteilung der Zufallsvariable durch zwei Fading-Modelle beschrieben werden:

* **Rayleigh-Fading**: Keine Line of Sight. $X$ ist exponentiell verteilt
* **Ricean-Fading**: Dominante Line of Sight. $X$ ist ricean-verteilt

Vereinfacht kann die benötigte Leistung für eine Übertragung $f(d)$ angegeben werden durch:

$$
f(d) = a \cdot d^\alpha + b
$$

Mit Distanz $d$, Übertragungsfaktor $a$, Path-Loss Exponent $\alpha$ und additiver Konstante $b$ (*???*).

### Graphenmodelle

Der **Unit-Disk-Graph (UDG)** beschreibt einen Graphen auf einer Menge Knoten, bei dem jeder Knoten mit jedem Knoten verbunden ist, der innerhalb seines **Unit-Disk-Radius** $R$ liegt. Dies modelliert die Übertragungsreichweite jedes Knoten. Der **Quasi-Unit-Disk-Graph (QUDG)** erweitert den UDG um eine minimal-Radius (im QUDG heißen die Parameter $r_{max}$ und $r_{min}$).


## Topologiekontrolle

Durch die limitierte Übertragungsreichweite hat ein drahtloses Netzwerk bereits eine implizite Struktur. Um eine Netztwerkstruktur noch weiter zu vereinfachen und somit das **Routing** von Nachrichten zu erleichtern und die Energieeffizienz zu erhöhen, können verschiedene **Topologiekontrollen** zum Einsatz kommen. Die wichtigsten, in dieser Vorlesung teilweise detailliert besprochenen, sind:

* **Neighbor elimination** (Kanten streichen)
* **Backbone construction**
* **Virtual overlays**
* **Relocation**

Ein **lokaler Algorithmus** (für eine Topologiekontrolle) erreicht ein netzwerkweites Ziel mit (Knoten-)lokalen Entscheidungen, während ein **globaler Algorithmus** Wissen über den Zustand des gesamten Netzwerkes mit einbezieht. Lokale Algorithmen haben folgende Vorteile:

* Resourcen sparen
* Beliebig große Netzwerke ermöglichen
* Besser mit dynamischen Änderungen klar kommen
* Arbeiten besser wenn keine gesamte Sicht auf das Netzwerk verfügbar ist


## Datenkommunikation

**Datenkommunikation** bezeichnet die Problematik, eine Nachricht möglichst effizient durch ein nicht oder nur tweilweise bekanntes Netzwerk zu schicken.
