# Marco

* Was sind die einfachsten Graphmodelle? Was sind UDG und QUDG?

* Was ist eine lokale Topologiekontrolle? Wie ist sie definiert?

* Was sind Spanner? Wie sind sie definiert?

* „Was gibt es so für Topologiekontrollen?” Wie sind sie definiert? Wie stehen sie in Relation mit einander?

    * Ich hab RNG, GG, URNG und UGG genannt und musste sie dann beschreiben

* Wie kann man im Allgemeinen beweisen, dass ein Graph Subgraph eines anderen ist

    * Ich hab im Endeffekt nur graphisch gezeigt wie der GG im RNG enthalten ist

* Was ist UDel? Warum ist es nicht lokal? Zeige ein Beispiel an dem man sieht, dass UDel nicht lokal ist. Was ist Delauney-Triangulierung? Wie sind die 3 Definitionen? Sind sie gleich? Was sind Cozirkularität und Kolinearität? Warum ist UDel trotzdem nützlich? Warum kann man Spanning-Aussagen über einen Graphen auf dessen Supergraphen übertragen?


# Dausi

* UDG, QUDG

* PDT

* Beweisideen zu PDT und UDel

* Topologiekontrolle

* Routing


# Carsten

* UDG, QUDG

* Erkläre lokale Topologiekontrolle

    * Schreibe diese Formel da hin: $\tau: \mathcal{C} \rightarrow \mathcal{D}, \forall G \in \mathcal{C} \forall v \in \tau(G) \exists u \in G: \tau(G)[v] = tau(G[u, k])[v]$

* Warum ist die Definition so umständlich?

    * Weil Geoclustering, dieses Raster über die Knotenmenge, imaginäre Kanten und so. Keine Ahnung, ein anderer Prüfling konnte das nicht beantworten und der Frey hat ihm das so kurz erklärt, die Begründung hat ihm gereicht.

* Schreib mal ein paar lokale Graphen hin

    * Antwort mit Graphen die man gut kann, bei mir $URNG, UGG, PDT, LDel^{(k)}$

* Zeige, das $RNG \subseteq GG$

    * Man malt die $RNG$-Kreise, sagt die Schnittmenge ist Lune und malt da den $GG$-Kreis rein $q.e.d.$

* Erkläre Spanner

    * Schreibe die drei Formeln hin für euklidische Ebene, euklidische Graphen und topologische Graphen

* Erklär dann noch $\Omega, \Theta, O$

    * Ja, uff, unten, genau, oben beschränkt. Die Antwort hat wohl gereicht.

* Zeig mal wie man beweist dass $UGG$ beschränkt ist und wie ist das mit der Beschränkung

    * Tower hinmalen, bisschen raten was der zu bedeuten hat

    * Er zeigt anscheinend die $\Omega$-Beschränkung

* Wie zeigt man jetzt auch noch $O$?

    * Keine Ahnung, nächste Frage

* Erklär mal konstante Spanner und welcher von deinen lokalen Topologien oben ist einer

    * Spanner, wo kein $n$ drin vorkommt

    * $PDT, LDel^{(k)}$

* Erzähl mal was von Delaunay

    * Eine der drei Definitionen

    * Die Beschränkungen (colinear, cozirkulär) womit die drei gleich sind

* Und dann noch $UDel$, mündlich sagen was das ist, wie lokal er ist und ein Beispiel für nicht-lokalität

    * $UDG \cap Delaunay$

    * Nicht lokal

    * Drei Punkte hinmalen die beinahe linear sind, das macht einen Kreis der superdupergroß ist und in UDG nicht mehr sichtbar ist, das macht $UDel$ nicht lokal

* Joa, warum ham wir den dann überhaupt behandelt?

    * Weil er ein $UDG$-Spanner ist und ich Supegraphen dafür finden kann, die lokal sind

* Wer und wie?

    * $PDT$, ist gleich wie $PuDel$

    * $PuDel$ ist ein $UDel$-Spanner ist ein $UDG$-Spanner

    * Ersteres beweise ich irgendwie, indem ich einzeln für jede Kante zeige, dass die ein $UDel$-Spanner ist (keine Ahnung was das heißt, hat ihm aber gereicht)

    * Beweis $PDT = PuDel$ nicht wichtig

* Ja und wie berechnet sich der Stretchfaktor insgesamt, also von $PDT$ nach $UDG$

    * Man multipliziert den Faktor zwischen $PDT$ und $UDel$ mit dem Faktor von $UDel$ und $UDG$
