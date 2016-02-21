Verwendet man die PDT um eine Nachricht zu versenden, müssen auf dem Weg der Nachricht durch das Netz viele weitere Nachrichten ausgetauscht werden, um die PDT zu bilden. Besser wäre wenn nur die PDT-Nachbarn antworten (**reagieren**) und damit der PDT-graph direkt konstruiert wäre.

Zunächst eine alternative Definition der PDT:

$$
uv \in PDT \Leftrightarrow \forall{w \in circle(u, v)}:\\
circle(u, v) \cap \overline{H^w(u,v)} = \emptyset\\
\land sin(\alpha) \geq \frac{\|uv\|}{r}
$$

Mit

* $\overline{H^w(u,v)}$ Halbebene von $u$ und $v$ die nicht $w$ enthält
* $\alpha$ Winkel zwischen $u$ und $v$ über $w$ ($\measuredangle(u, w, v)$)
* $r$ Unit Disk Radius

In Worten: Die Halbebene gegenüber $w$ muss leer sein und der Winkel muss "ziemlich spitz sein".


# Reactive PDT

**Reactive PDT (RPDT)** für Knoten $u$:

1. Sende Request to Send (RTS) mit Position blind an alle Nachbarn (Broadcast)
2. Setze eigenen Timer auf das Maximum ($t(u) = t_{max}$)
3. Alle anderen Knoten ($v$) empfangen den Broadcast:
    1. Initialisiere Menge bekannter Knoten ($S(v) = \emptyset$)
    2. Speichere Maximalwinkel ($\alpha_{max}(v) = \pi/2$)
    3. Setze Timer entsprechend des normalisierten Abstands ($t(v) = \frac{\|uv\|}{r}\cdot t_{max}$)
        * Bei Timerablauf: Sende Clear to Send (CTS) mit Position an alle Nachbarn
        * Bei fremden CTS (von $z$): Füge $z$ zu $S(v)$ hinzu und prüfe ob $uv$ bezüglich $z$ die PDT-Bedingung verletzt.
            * Ja: Lösche Timer (wird kein CTS senden)
            * Nein: Teste ob $\alpha = \measuredangle(u, v, z) > \alpha_{max}$. Wenn ja aktualisiere den Maximalwinkel ($\alpha_{max} = \alpha$) und aktualisiere den Timer ($t(v) = \frac{\|uv\|}{sin(\alpha)} * \frac{1}{r} * t_{max}$)
4. Empfange CTS von Nachbarn bis der Timer abgelaufen ist. Alle Nachbarn die geantwortet haben sind PDT-Nachbarn.

*TLDR:* Bei CTS-Empfang passen die anderen Knoten ihre Timer so geschickt an, dass nur die PDT-Nachbarn ein CTS senden. Der RTS-Knoten kennt nach Ablauf seines Timers alle PDT-Nachbarn.


# BFP-GG

**BFP-GG** funktioniert ähnlich wie reactive PDT, erzeugt aber einen Gabriel Graphen. Hier kann es allerdings passieren, dass einige nicht-GG Kanten erzeugt werden (*die Details sind kompliziert*) sodass es anschließend eine Protestphase geben muss, in der diese wieder entfernt werden.


# $O_k$-Reaktivität

**Nachrichtenkomplexität** bezeichnet die Speicher-Komplexität der Nachrichten, also der Anzahl von Bits, die übertragen werden müssen (In O-Notation).

Eine lokale Topologiekontrolle ist **$O_k$-reaktiv**, wenn zur Konstruktion:

* ... kein Knoten seine Nachbarn kennen muss
* ... ein Knoten zu Beginn einen Broadcast sendet
* ... die Nachrichtenkomplexität auf $O(beteiligteKnoten \cdot log_2(n) )$ beschränkt ist

$n$ bezeichnet hier die Anzahl Knoten im Ausgangsgraphen und $beteiligteKnoten$ die Anzahl der Knoten, die bei dem Konstruktionsverfahren der Topologiekontrolle beteiligt sind (*Stark vereinfacht*).

Analog dazu ist eine lokale Topologiekontrolle **$\Omega_k$-reaktiv**, wenn zur Konstruktion die Nachrichtenkomplexität auf $O(beteiligteKnoten \cdot log_2(n) )$ *nach unten* beschränkt ist.

## Übersicht der Reaktivität reaktiver Verfahren

| Algorithmus | Topologie | $O_1$-Reaktiv | $\Omega_1$-Reaktiv |
| ----------- | --------- |:-------------:|:------------------:|
| (GDBF)      | GG        | Nein          | Ja                 |
| BFP-GG      | GG        | Nein          | Ja                 |
| (BFP-RNG)   | RNG       | Ja            | Nein               |
| (BFP-CNG)   | (CNG)     | Ja            | Nein               |
| RPDT        | PDT       | Ja            | Nein               |

*Eingeklammertes wurde nicht behandelt.*
