## **1.5 Workloadsystem (Fertig, Parameter fehlen)**

erstellt von [Maulwurf, Tristan]

>Abgeschlossen: Maulwurf, TNT, Tristan 
Datum: 31.01.2021 


Grundlegende Funktionen
*   Regulierung der Auslastung der Hardware.
*   Zuweisung von Leistung an die Programme/Prozesse.

## **1.5.1 Leistung der Hardware**

*   Für jede Hardware-Art gibt es bestimmte Leistungspunkte (CPU, RAM, GPU, Netzwerk (NET)). E.g: Zwei RAM Sticks haben in Summe nur einmal “RAM-Leistungspunkte”
*   Ausnahme: Die Festplatte wird im Workloadsystem nicht beachtet.
* Die Leistungspunkte werden für jedes Hardwareteil einzeln festgelegt - siehe [Computer](Computer.md).

## **1.5.2 Leistungsverbrauch Prozesse**

*   Jeder Prozess zieht Leistung, je nach Aktivität wird unterschieden (Angabe bei den Prozessen):
Leistungsstufe 0 (Grundlast), wenn Prozess an ist (kann 0 sein)
    *   Verbrauch bei Leistungsstufe 1
    *   Verbrauch bei Leistungsstufe 2 (nicht bei jedem Prozess erforderlich)
    *   Verbrauch bei Leistungsstufe 3 (nicht bei jedem Prozess erforderlich)
    *   Der Verbrauch steigt von Stufe 0 zu 3 an
*   Der Leistungsverbrauch wird stufenweise (0, 1, 2, 3) für jeden Prozess einzeln festgelegt (auch per Formel möglich)
*   Der Leistungsverbrauch kann abhängig von der verbauten Hardware sein
z.B. 20% der verbauten CPU-Leistung
*   Der Leistungsverbrauch schwankt zufällig um diesen Wert in einer gewissen Spanne (Prozentsatz) (Angabe bei den Prozessen)
*   Mit jeder Aktion des Prozesses wird der Verbrauch neu ermittelt.
*   Prozesse brauchen Leistung beim Starten und Beenden. (Angabe bei den Prozessen)

## **1.5.3 Sonstiger Leistungsverbrauch (durch Frontend)**

[Zukünftig: Leistungsverbrauch durch Frontend-Aktionen wird zur v0.3.0 nicht implementiert]

## **1.5.4 Prioritätensystem**

*   Es gibt 4 verschiedene Prioritäten
    *   Priorität 1: Sehr wichtig, Leistungsreduzierung möglich. (E.g. später Betriebssystem)
    *   Priorität 2: Wichtig, Prozess wird vorrangig Leistung zugewiesen. Reduzierung nur, wenn keine Prozesse auf Prio 3 und 4 aktiv sind und nach 1.5.5.
    *   Priorität 3: Standard für alle Prozesse und Apps. Reduzierung erfolgt, wenn keine Prozesse auf Prio 4 aktiv sind und nach 1.5.5.
    *   Priorität 4: Unwichtig, Reduzierung erfolgt vorrangig. Reduzierung kann pro Prozess nur vollständig erfolgen (aktiv oder inaktiv).
*   Der Spieler kann den Prozessen die Prioritäten 2-4 frei zuordnen. Standard ist Priorität 3 soweit nichts anderes bestimmt ist. Priorität 1 kann nicht vergeben werden.
*   Ein Prozess kann geupgradet werden.
*   Die Priorität eines Prozesses kann ab einem bestimmten Level des Prozesses durch den Spieler geändert werden. (Benötigtes Prozesslevel  x zur Änderung steht bei den Prozessen) 
    >(ThisIsForGameParameters /process/*/priority/playercanchangeonlevel)

    *   Ab einschließlich Level x (x ∈ ℤ)  kann die Priorität geändert werden. 
    *   Bei x = -1 kann die Priorität nicht geändert werden.

## **1.5.5 Begrenzung des Leistungsverbrauchs (“Reduzierung”)**

1.  Kann die geforderte Leistung nicht bereitgestellt werden, ist eine Reduktion der zugewiesenen Leistung von Prozessen durchzuführen.
-> Es wird weniger Leistung zugewiesen als gefordert.
2.  Die Reduktion erfolgt innerhalb der Prioritäten proportional bei allen Prozessen gleichermaßen (z.B. Reduktion pro Prozess um 5%)(außer bei Prio 4, s.u.) 
3.  Bei Priorität 4 kann jeder Prozess nur deaktiviert werden. 
4.  Innerhalb einer Priorität kann nur Leistung reduziert werden, wenn in allen niedrigeren Prioritäten keine Prozesse aktiv sind (erst Prio 4, dann 3, dann 2).
5.  Sollten mehrere Prozesse gleichzeitig die Schwelle zum Abstürzen überschreiten, stürzt zuerst der ab, der am meisten Leistung benötigt. Im Zweifel wird zufällig entschieden, welcher abstürzt.
6.  Es wird nicht zwischen startenden und aktiven Prozessen unterschieden.
7.  Die von einem Prozess beanspruchte Leistung kann abgerufen werden (in % pro Hardwareart).
8.  Die Reduzierung pro Prozess kann abgerufen werden (in %).
9.  Die Hardwareauslastung ist für jede Hardware-Art abrufbar (genutzte LP pro gesamt verfügbare LP in %).

## **1.5.6 Auswirkungen reduzierter Leistung auf Prozesse**

### **1.5.6.1 Bei aktiven Prozessen**

1.  Die Definition, welche Auswirkung wann eintritt, wird individuell für jeden Prozess festgelegt.
2.  Auswirkungen hängen von der Stärke der Reduzierung ab.
    -  Prozesse geben eine Leistungsgrenze für jede Auswirkung an. 
        -  Die Grenze ist in einem Quotienten aus erhaltener und geforderter Leistung beschrieben.
        -   Die verfügbaren Auswirkungen sind fix.
    -   Beispiel:
        -   crashBelowPercentage: 0.5
        -   ⇒ Wenn der Prozess weniger als 50% der geforderten Leistung zugewiesen bekommt, crashed er.
3.  Ein Prio 1 Prozess stürzt sofort unter 100% ab. Er muss zwingend die volle Leistung bekommen.
4.  Ein Prio 4 Prozess stürzt sofort unter 100% ab. Er muss zwingend die volle Leistung bekommen.

5.  Folgende Auswirkungen sind möglich:
    -   Prozess stürzt ab
        -   Ohne Abschaltzeit oder Abschaltleistung sofort deaktiviert.
    -   Prozess startet beim nächsten Mal langsamer (nach Absturz)
        -   Nächste Startzeit nach Crash ist länger.
    -   Prozess antwortet nicht
        -   Beansprucht immer noch die zugewiesene Leistung, führt allerdings keine Aktionen mehr aus, bis er die Leistungsgrenze wieder nach oben überschreitet. (E.g: Es werden keine Morphcoins berechnet / Es werden keine Befehle dieses Prozesses ausgeführt)
    -   Prozess kann nicht “rechnen” 
        -   Gleiches wie Prozess antwortet nicht, nur wird eine Fehlermeldung angezeigt.
    -   Prozess arbeitet ineffektiver
        -   z.B. es werden weniger MCs generiert/ die Erfolgschance sinkt
        -   Der Ineffektivitätsfaktor wird von dem 
Intervall [cannotCalculateGrenze ; 1] auf [0 ; 1] gemapped/interpoliert

            (Beispiel:
             Grenze e) < 100%; Grenze d) < 80%
             zugewiesene Leistung = 90%
            -> mittig zwischen beiden Grenzen -> nur noch zu 50% effizient.)

### **1.5.6.2 Bei startenden/stoppenden Prozessen**

*   Während der Start-Stop-Phase können Reduzierungen eintreten.
*   Welche Auswirkung wann eintritt, wird individuell für jeden Prozess festgelegt.
*   Folgende Auswirkungen sind möglich:
    *   Die Start- bzw. Stoppzeit wird um die Zeit verlängert, die nicht die ganze Leistung zur Verfügung stand (“Die Uhr hält an”). Pendant zum freezen
    *   ggf. nur anteilige Verlängerung der Startzeit. Pendant zum ineffektiven Rechnen
    *   Die Startzeit beim nächsten Starten verlängert sich, wenn er beim Stoppen reduziert wurde.

