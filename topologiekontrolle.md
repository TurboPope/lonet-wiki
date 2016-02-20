Eine **Topologiekontrolle** ist eine Abbildung $\tau: C \rightarrow D$ eines Graphen $C$ auf einen Graphen $D$. $D$ ist ein Subgraph von $C$. Eine Topologiekontrolle kann Kanten und Knoten entfernen.

Die **k-lokale Sicht** $G[v, k]$ eines Knotens $v$ ist ein Subgraph von $G$, bestehend aus $v$ und seinen $k$-hop Nachbarn den Pfaden zu diesen. Vereinfachung: $G[v]$ ist die 1-lokale-Sicht von $v$.

Eine **k-lokale Topologiekontrolle** ist eine Topologiekontrolle, die nur die k-lokale Sicht eines Knotens betrachtet, um Entscheidungen zu treffen.


## 2D-Geometrie

Der **Bisektor** zweier Punkte $u$ und $v$ ist die Menge aller Punkte, die zu $u$ und $v$ den gleichen Abstand haben: $B(u,v) = bisektor(u,v) = \{x : \|xu\| = \|xv\|\}$

Die **geschlossene Halbebene** zweier Punkte $u$ und $v$ ist die Menge aller Punkte, die näher zu $u$ liegen als zu $v$: $H(u,v) = halfPlane(u, v) = \{x: \|xu\| \leq \|xv\| \}$

Der **Kreis** um einen Punkt $u$ mit dem Radius $r$ ist die Menge aller Punkte, die zu $u$ den Abstand $r$ haben: $C_r(u) = circle(u, r) = \{ x : \|xu\| \leq r \}$. Weitere relevante Kreise sind der Kreis, der die Punkte $u$, $v$ und $w$ umschließt $C(u, v, w) = circle(u, v, w)$ und der kleinste Kreis, der die Punkte $u$ und $v$ umschließt $C(u, v) = circle(u, v)$.

Des Weiteren wird der **Winkel** zwischen zwei Geraden $uv$ und $vw$ wie folgt notiert: $\measuredangle uvw = angle(u, v, w)$


## Spanner

In einem topologischen, gewichteten Graphen $G$ ist der **kürzeste Pfad** $p_{min}$ zwischen zwei Knoten $u$ und $v$ der Pfad, für den die Pfadlänge minimal ist. Er wird wie folgt notiert: $p_{min} = \Gamma_G(u, v)$

In einem euklidischen Graphen ist das Gewicht der Kanten durch die Distanz der Knoten gegeben und der kürzeste Pfad $p_{min}$ wird notiert mit $p_{min} = \Pi_G(u, v)$.

Ein **euklidischer $c$-Spanner** ist ein Graph, bei dem für alle Knoten das Verhältnis zwischen kürzester Pfadlänge und tatsächlicher euklidischer Distanz den **stretch-factor** $c$ nicht überschreitet. Formell:

$$
\forall{u, v \in G}: \frac{\|\Pi_G(u,v)\|}{\|uv\|} \leq c
$$

Sei $H$ ein euklidischer Graph und $G$ ein Subgraph von $H$. Nun wird das Verhältnis zwischen der kürzesten Pfadlänge des Subgraphen und der des ursprünglichen Graphen gemessen. $G$ ist ein **euklidischer Graph-Spanner**, wenn dieser stretch-factor $c$ nie überschreitet:

$$
\forall{u, v} \in G: \frac{\|\Pi_H(u,v)\|}{\|\Pi_G(u,v)\|} \leq c
$$

Für einem topologischen Graphen gilt das gleiche, aber es werden die topologischen Pfadlängen betrachtet:

$$
\forall{u, v \in G}: \frac{|\Gamma_H(u,v)|}{|\Gamma_G(u,v)|}\leq c
$$


## Planare Graphen

*Graphentheoretisch*: Graph $G$ ist planar, wenn $G$ auf die Ebene gezeichnet werden kann, sodass sich keine Kanten schneiden.

*Definition hier*: Graph $G$ ist als Zeichnung auf der Ebene gegeben. Gesucht ist ein Teilgraph $H$, der keine schneidenden Kanten enthält. Dieser Graph $H$ wird dann als planar bezeichnet.


## EMST (Euclidean Minimal Spanning Tree)

Das euklidische Gewicht eines euklidischen Graphen ist

$$
\|G\| = \sum_{uv \in G} \|uv\|
$$

Der **EMST** über eine Punktemenge $V$ ist der zusammenhängende Graph, für den $\|V\|$ minimal ist. Ist $UDG(V)$ verbunden, so ist $EMST(V) \subseteq UDG(V)$ (*Beweis ausgelassen*). EMST ist jedoch keine k-lokale Topologiekontrolle (*Beweis ausgelassen*).

Der EMST über $V$ lässt sich über den Algorithmus von Kruskal herstellen: Zeichne in jedem Schritt die kurzmöglichste Kante, die keinen Zyklus erzeugen würde, bis der Graph zusammenhängend ist.


## LMST (Local EMST)

Der **LMST** ist eine Graphenstruktur, die "nahme am" EMST ist. Gegeben sei ein Graph $G$ mit zwei Knoten $u$ und $v$ und der Kante $uv$. Wendet man LMST als Topologiekontrolle an, bleibt $uv$ im Graphen, wenn:

$uv \in LMST(G) \Leftrightarrow uv \in EMST(N(u)) \land uv \in EMST(N(v))$

Das heißt: Wenn $uv$ und $vu$ im EMST über die Nachbarn des jeweils anderen Knotens enthalten sind, bleibt $uv$ bestehen (hier etwas kompliziertere Definition um ungerichtete Graphen mit einzubeziehen).

(*Problem mit gleichen Kantenlängen ausgelassen.*)

Der LMST ist eine 2-lokale Topologiekontrolle (*Beweis ausgelassen*).

Ist $UDG(V)$ verbunden, so ist $EMST(V) \subseteq LMST(V)$ (*Beweis ausgelassen*).

Der LMST hat maximalen Grad 6 (*???, Beweis in Übung*).


## RNG (Relativer Nachbarschaftsgraph)

$V$ sei eine Menge von Punkten, die zu einem Graphen verbunden werden sollen.

$$
uv \in RNG(V) \Leftrightarrow \|uv\| \leq max\{\|uw\|, \|vw\|\} \quad \forall{w \in V \backslash \{u,v\}}
$$

Alternativ: Sei Radius $r = \|uv\|$. Sei $c_u$ die Menge der Punkte im Kreis um $u$ mit Radius $r$: $c_u = circleSet(u, r)$ und $c_v$ das Gleiche für $v$. Dann ist

$$
uv \in RNG(V) \Leftrightarrow \exists!{w \in V}: w \in c_u \cap c_v
$$

Das heißt: Die Schnittmenge (**Lune**) der Kreise um $u$ und $v$ mit mit deren Abstand als Radius enthält keine weiteren Knoten.

Der **Unit- Relativer Nachbarschaftsgraph (URNG)** ist die Schnittmenge aus RNG und UDG:

$$
URNG(V) = RNG(V) \cap UDG(V)
$$

Der URNG ist eine 1-lokale Graphkonstruktion und $LMST(V) \subseteq URNG(V)$ (*Beweis ausgelassen*).

Sei $V$ eine Punktemenge mit $n$ Punkten. Dann ist

$$
\frac{\|\Pi_{URNG}(u,v)\|}{\|\Pi_{UDG}(u,v)\|} \leq n-1
$$

(*??? Keine Ahnung was das soll, Beweis ausgelassen*)