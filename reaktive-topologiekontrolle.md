*TODO, was ist das, was will man erreichen, Beispiel PDT bauen, aber nicht auswendig, warum PDT nachrichtenoptimal, O-Reaktivität angucken, $O_k$-reaktiv, BFP-GG, $\Omega_k-reaktiv$, Redundanzkoexistenz hinmalen können*

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

Reactive PDT für Knoten $u$:

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
