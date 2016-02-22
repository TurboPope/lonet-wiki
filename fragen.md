1. Was versteht man unter einem Ad Hoc Netzwerk? Welche Ausprägungen gibt es? Wie unterscheiden sich diese?

2ez

2. Was versteht man unter Single-Hop bzw. Multi-Hop Netzen? Welche Vorteile bieten Multi-Hop gegenüber Single-Hop Netzen?

Single-Hop hat direkte Verbindungen, Multi-Hop geht um Ecken. Multi-Hop hat eine potentiell einfachere Graphstruktur, weniger Energieverbrauch (weil Kürzere Strecken), weniger Channels/Kabel.

3. Was versteht man unter dem Begriff Pfadverlust?

Signalverlust in Dezibel wenn es ankommt.

4. Welche vereinfachten Graphmodelle gibt es und wie sind diese definiert? Wieso wird bei QUDG typischerweise angenommen, dass $\frac{r_{max}}{r_{min}} \leq sqrt{2}$ gilt?

UDG, QUDG? Und keine Ahnung.

5. Was versteht man unter einem lokalen Algorithmus und was ist der Unterschied zu einem globalen Algorithmus? Welchen Preis bezahlt man für die Lokalität?

Lokale Algorithmen beachten nur die ($k$-)Nachbarn eines Knotens bei der Berechnung, wobei globale Algorithmen den ganzen Graph kennen und damit Entscheidungen treffen. Lokalität ist weniger optimal.

6. Was versteht man unter Topologiekontrolle? Wie ist k-lokale Topologiekontrolle definiert? Wie ist die lokale Sicht eines Knotens auf einen Graphen definiert und was ist damit gemeint?

Graph zu Subgraph. Eine $k$-lokale Topologiekontrolle betrachtet nur die $k$-Nachbarn jedes Knotens. Die lokale Sicht eines Knotens sind diese Nachbarn und die Pfade dahin.

7. Was ist ein Euklidischer Spanner bzw. Euklidischer Graph Spanner bzw. Topologischer Graph Spanner? Wie sind diese definiert?

Ein Spanner ist ein Subgraph mit limitierten stretch-Faktoren. Der stretch-Faktor ist das Verhältnis zwischen Pfadlänge im Subgraphen und dem ursprünglichen Graphen. Ein Euklidischer Spanner vergleicht mit dem vollständigen Euklidischen Graphen. Der Euklidische Graph Spanner vergleicht mit einem beliebigen Euklidischen Graphen. Der Topologische Graph Spanner macht das gleiche, aber für topologische Graphen.

8. Ist ein Euklidischer Spanner automatisch auch immer ein Topologischer Spanner? Ist ein Topologischer Spanner automatisch immer ein Euklidischer Spanner? Begründen Sie Ihre Antworten. Welche Eigenschaften muss ein Graph bspw. erfüllen damit jeder Euklidische Spanner auch automatisch ein Topologischer Spanner ist?

Ja. Nein. Weil die Graphen selbst sich auch so verhalten.

9. Was ist ein Euklidischer Minimaler Spannbaum (EMST)? Ist EMST eine k-lokale Graphstruktur? Wieso nicht? Welche vergleichbare Graphstruktur kann lokal konstruiert werden? Wie kann LMST lokal konstruiert werden? Welche Subgraphrelation erfüllen EMST und LMST? Ist LMST Knotengradbeschränkt?

Es ist der optimalste Spanner in einem euklidischen Graphen. Nein. Weil es in der VL so steht. LMST. Mit Kruskarl. $EMST \subseteq LMST$ falls $UDG$ verbunden. Ja, auf 6.

10. Wie sind RNG, URNG, GG und UGG definiert? Welche Eigenschaften haben diese Graphen bzgl. Gradbeschränkung, Zusammenhang, Planarität, k-lokale Konstruierbarkeit und welche Subgraphrelation erfüllen sie? Wie beweist man das GG planar ist?

Schau in die Zusammenfassung und lern es auswendig.

11. Wie ist die Hop- bzw- Euklidische Spanning Ratio von GG bzw. RNG? Nennen Sie die Obere- und Untere-Schranke und die entsprechenden Beweisideen.

Das hat der Frey gesagt es kommt nicht dran.

12. Wie ist die Delaunay Triangulierung (DT) definiert und welcher Zusammenhang besteht zu Voronoi Diagrammen? Unter welchen Annahmen ist die DT wohldefiniert? Was ist eine konvexe Menge und was die konvexe Hülle einer Punktmenge?

Kante existiert wenn sich Voronoi-Regionen eine Voronoi-Kante teilen. Nicht-Cozirkularität und Nicht-Colinearität. Unsicher.

13. Wie kann man beweisen, dass DT ein Euklidischer Spanner für den vollständigen Euklidischen Graphen ist? Was ist der DT-Pfad und welche Rolle spielt er im Spanner Beweis von Dobkin?

Mit dem Dobkin-Beweis. Direkter pfad durch Voronoi-Regionen und keine Ahnung.

14. Was ist die Unit Delaunay Triangulierung (UDT) und ist diese lokal konstruierbar? Wieso?

Nope, weil Del ist auch nicht lokal.

15. Welche lokalen Konstruktionen für planare Spanner gibt es? Wie ist $LDel^{(k)}$ definiert? Ist LDel^{(1)} planar? Wie kann man $LDel^{(1)}Ä$ planarisieren?

GG, RNG, LDel usw.. Del auf k-hop-Nachbarschaft. Mit PlDel.

16. Erläutern Sie einen 2-lokalen Algorithmus zur Konstruktion von LDel (2).

Alle 2-lokalen Dreiecke aus $S$ finden, deren Kreis drumrum keine weiteren Punkte enthält. Das Ergebnis davon mit UGG $\cup$nifizieren.

17. Kann man planare Spanner auch 1-lokal konstruieren? Nennen Sie zwei 1-lokale Spanner Konstruktionen. Wie sind diese definiert?

Ja. UGG und URNG. UDG+GG und UDG+RNG.

18. Wie ist der Yao-Graph definiert? Welche Subgraphrelation erfüllt er? Ist der Yao-Graph planar und wieso? Was ist eine Cone-Based Topology? Wie kann lokal eine Symmetrische Subtopologie konstruiert werden?

Kuchen. kA. Nein weil Vorlesung. Empfangsreichweite so einstellen, dass in jedem Cone ein Knoten ist. Exkursion.

19. Nennen Sie Beispiele für Topologiekontrollmechanismen die in gerichteten Netzgraphen unzusammenhängende Topologien konstruieren. Wie ist DRNG definiert?

DRNG und DLSS.

20. Erläutern Sie das Prinzip des Chu-Liu/Edmonds Algorithmus zur Konstruktion von Directive Local Spanning Subgraphs (DLSS). Welche Subgraphrelation erfüllen DRNG und DLSS?

Sammelt Kanten mit geringen Gewichten und ersetzt Zyklen durch virtuelle Knoten. DLSS ist Subgraph von DRNG.

21. Was versteht man unter einem k-vertex connected network? Wie kann man mit lokalen Regeln ein k-vertex connected network konstruieren?

Jeder Knoten hat mindestens k Nachbarn. Yao Graph mit 6 cones.

22. Was versteht man unter einem Backbone? Welchen Zweck erfüllen diese? Wie ist ein Dominating Set (DS) bzw. ein Connected Dominating Set (CDS) definiert?

Jeder Knoten ist entweder ein Backbone oder Nachbar eines Backbones. Damit nur Backbones schwere Arbeit machen müssen. Menge von Backbones bzw. verbundene Menge von Backbones.

23. Was versteht man unter dem Begriff Clustering? Welche Rollen nehmen Knoten beim Clustering ein? Erläutern Sie das Funktionsprinzip des Verteilten Clustering Algorithmus aus der VL. Erläutern Sie das lokale Verfahren zur Konstruktion von CDS mittels 2D-Grid Clustering. Erläutern Sie die Funktionsweise der Lightweight CDS Construction nach Wu und Li.

Fasst Knoten logisch zusammen. Cluster-Head, Cluster-Member oder Gluster-Gateway. Cluster entscheiden der Rehe nach ob sie CH oder CM sind und broadcasten ihre Entscheidung. 2D-Grid, Knoten mit höchster ID in Kästchen wird dominating. Wi Tu Lo.

24. Was versteht man unter guaranteed delivery unicast, multicast, ..? Welche Annahmen müssen hierzu getroffen werden und warum?

Garantierte Zustellung. Casts gehen an verschiedene Mengen von Knoten. Graph connected und sinnvolles Routing-Verfahren.

25. Erläutern Sie das Prinzip von Greedy Packet Forwarding. Garantiert dieses Verfahren garantierte Nachrichtenauslieferung? Erläutern Sie anhand eines Beispiels.

Nachricht wird an nächstbesten Knoten weitergeschickt. Nein, weil Sackgassen.

26. Welche Routing Metriken zur Anwendung beim Greedy Routing kennen Sie? Erläutern Sie in Kürze das Cost Over Progress Framework.

Distanz, Verbleibende Batterie, Hops, Zufall, Cost-over-Progress Framework. Das setzt Kosten für nächsten Hop und geschätzte weitere Kosten in Vergleich zu geschätzten aktuellen verbleibenden Kosten.

27. Erläutern Sie das Prinzip von FACE-Routing sowie von Greedy-Face-Greedy (GFG) Routing.

Die Nachricht wandert entlang von Faces zum Ziel. GFG zieht Linie von Start zu Ziel und wechselt Face wenn nächste Kante die Gerade schneidet.

28. Erläutern Sie das Prinzip des Algorithmus Beaconless Forwarder Planarization (BFP). Ist dieser Algorithmus O-reaktiv? Benennen Sie ein Gegenbeispiel.

Knoten antworten mit geschicktem Timing auf RTS mit CTS. Kommt drauf an, BFP-GG ist O-Reaktiv, BFP-RNG nicht.

29. Erläutern Sie das Prinzip des Algorithmus reactive-PDT. Ist dieser Algorithmus O-reaktiv? Wieso?

S.o.. Ja, weil die Nachrichtenkomplexität ist beschränkt auf $O(beteiligte Knoten \cdot log_2(n))$.

30. Wann ist ein lokaler Algorithmus zur Topologiekontrolle $\Omega$-reaktiv?

Wenn die Nachrichtenkomplexität nach unten beschränkt ist auf s.o..
