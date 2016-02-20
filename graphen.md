Ein **Graph** ist definiert als: $G = (V, E)$, wobei $v \in V$ **Knoten** und $(u, v) \in E$ **Kanten** sind.

Die Kanten sind Teilmenge aller Knotenverbindungen: $E \subseteq V \times V$. Falls $E = V \times V$, dann ist $G$ ein **vollständiger Graph**.

Ein **ungerichteter Graph** hat Verbindungen, die immer in beide Richtungen verlaufen: $uv \in G \Leftrightarrow vu \in G$.

Seien $G = (V_G, E_G)$ und $H = (V_H, E_H)$ Graphen.

Falls $V_G \subseteq V_H$ und $E_G \subseteq E_H$, dann ist $G$ ein **Subgraph** von $H$: $G \subseteq H$. Im Umkehrschluss ist $H$ ein **Supergraph** von $G$: $H \supseteq G$

Der **Schnitt** der Graphen ist definiert als: $G \cap H = (V_G \cup V_H, E_G \cup E_H)$.

Ein **Pfad** ist eine Reihe von Knoten, die mit Kanten verbunden sind: $p = (v_1 ... v_n), v_iv_{i+1} \in E$.

$G$ ist **verbunden**, wenn man zwei beliebige Knoten mit einem Pfad verbinden kann.

Als **k-hop-Nachbarn** $N_k(v)$ von Knoten $v$ werden die Knoten bezeichnet, die $k$ oder weniger Schritte von $v$ entfernt sind. Ohne explizites $k$ gilt $N(v) = N_1(v)$.

Knoten $u$ und $v$ **sehen einander**, wenn sie Nachbarn voneinander sind: $u \in N(v) \wedge v \in N(w)$.


# Graphentypen

## Gewichteter Graph

Zusätzlich zum Graphen gibt es noch eine Funktion $f$, die das Gewicht einer Kante berechnet: $(G, f) = ((V, E), f)$ mit $f: E \rightarrow \mathbb{R}$.

Bei einem gewichteten Graphen kann man die **Pfadlänge** eines Pfades berechnen, indem man alle Kantengewichte im Pfad zusammenzählt: $\hat{f} = \displaystyle{\sum_{i = 1}^{n - 1}} f(v_iv_{i + 1})$

## Euklidischer Graph

Ein Graph im euklidischen Raum (normale Geometrie).

Die Gewichtung ist die euklidische Distanz zwischen zwei Punkten $p = (p_1 ... p_n)$ und $q = (q_1 ... q_n)$ im $n$-dimensionalen Raum: $\|pq\| = \sqrt{\displaystyle{\sum_{i = 1}^n}} (p_i - q_i)^2$

## Topologischer Graph

Laut Dausi ein gewichteter Graph, bei dem die Kantengewichtfunktion aber nicht nur die Distanz zwischen den Punkten ist.

## UDG (Uni-Disk Graph)

Ein UDG hat einen Radius $r$. Mit diesem Radius zieht man einen Kreis um einen Knoten $V$. $UDG(V)$ ist dann die Menge aller Knoten, die sich in dem Kreis befindet.

## QUDG (Quasi-Unit-Disk Graph)

In der Realität kann man nicht einfach um z.B. einen WLAN-Router einen Kreis ziehen und sagen, dass alles im Kreis sich zum Router verbinden kann. Stattdessen nimmt man zwei Radien $r_{min}$ und $r_{max}$ ($r_{min} \leq r_{max}$) und zieht damit zwei Kreise um $V$. $QUDG(V)$ ist dann die Menge aller Knoten, die im $r_{min}$-Kreis sind, aber zwischen $r_{min}$ und $r_{max}$ nur vielleicht.

Besonders interessant ist wenn $\frac{r_{max}}{r_{min}} \leq \sqrt{2}$, aber warum das so ist weiß keiner.
