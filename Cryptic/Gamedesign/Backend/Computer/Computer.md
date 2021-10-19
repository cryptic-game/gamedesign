## 1.7 Computer

erstellt von [Marius, Maximilian]

### 1.7.2 Leistungspunkte

Hardwarekomponente die keine Leistungspunkte (LP) besitzen, sind nicht aufgeführt. \
GitHub:
Datei [hardware_gameconfig](https://github.com/cryptic-game/gamedesign/blob/parameter-pre-alpha-3/Cryptic/Gameparameter/hardware_gameconfig.yaml)
, Stand: 29.08.2021

**Start-PC:**

* Mainboard: Zero MX One / GPU = 5.000 LP / NET = 10.000 LP
* CPU: CoreOne A100 / CPU = 10.000 LP
* RAM: Crossfire One / RAM = 10.000 LP
* Externe GPU: Nein
* Externe Netzwerkkarte: Nein
* 50 MC/Tag

**Unterklasse-PC**

* Mainboard: Zero MX Pro / NET = 10.000 LP
* CPU: CoreOne A110 / CPU = 20.000 LP
* RAM: Crossfire ZX100 / RAM = 44.000 LP
* Externe GPU: Forcevid MX1000 / GPU = 40.000 LP
* Externe Netzwerkkarte: Nein
* 80 MC/Tag

**Mittelklasse-PC**

* Mainboard: Zetta Ultimate M150
* CPU: DualCore M101 / CPU = 40.000 LP
* RAM: Crossfire ZX200 / RAM = 139.000 LP
* Externe GPU: Zetta TX2066 / GPU = 204.000 LP
* Externe Netzwerkkarte: Network Element One / NET = 20.000 LP
* 180 MC/Tag

**High-End PC**

* Mainboard: Zeus Professional X3
* CPU: QuadCore TX950 / CPU = 205.000 LP
* RAM: Crossfire P60 + Crossfire P60 / RAM = 1.100.000 + 1.100.000 = 2.200.000 LP
* Externe GPU: Zetta TX2066 Pro / GPU = 460.000 LP
* Externe Netzwerkkarte: Network Element One / NET = 20.000 LP
* 300 MC/Tag

### 1.7.3 Basisfunktionen

#### 1.7.3.1 Allgemein

* Jeder Computer bekommt eine einzigartige UUID
* Die UUID wird beim kompletten Auseinanderbauen eines Rechners gelöscht und beim Zusammenbauen neu vergeben. Die UUID
  wird erst gelöscht, wenn das Mainboard entfernt wird, siehe Reihenfolge Schritt 2
  bei [Hardwareteile tauschen](#1773-hardwareteile-tauschen).
* Jeder funktionsfähige Computer besteht aus Mindestbestandteilen
* Jeder Computer ist konfigurierbar - siehe  [Konfiguration ändern](#177-konfiguration-ndern).
    * Besonderheit beim Start-PC beachten
* Anmerkung für Start-Computer: Die Hardwareteile des Start-PC befinden sich zum ersten Spieleintritt im [Inventar](1.8)
  . Der User muss den Computer aktiv [zusammenbauen](#176-zusammenbauen).

* Computer die insgesamt gebaut/erstellt werden können:
    * max. 6 Computer
    * Ein Computer kann vollständig oder unvollständig sein. Beides zählt als erstellt - siehe Definition
      unter [zusammenbauen](#176-zusammenbauen)
    * der Neu erstellte Computer ist Inaktiv und wird im Inventar abgelegt

* Aktive Computer die gleichzeitig benutzt werden können:
    * min. 0 Computer
    * max. 4 Computer
    * [Server zur späteren Version]
    * Anmerkung: Aktiver Computer bezeichnet nur das “einstecken des Stromkabels in die Steckdose”. Ein aktiver Computer
      verbraucht trotzdem 1x Slot im Inventar.

* Computername ist vom Spieler zu benennen:
    * Owner darf den Computer-Namen jederzeit ändern. Der Computer muss dazu aktiv sein, unabhängig ob ein- oder
      ausgeschaltet.
    * 2 bis 10 Zeichen (Zahlen 0-9, Buchstaben a-z/A-Z)
    * mind. 1x Buchstabe
    * RegEx: (?=.*[a-zA-Z])[\da-zA-Z]{2,10}
    * Kein Name von der [Blacklist](../Filesystem/Filesystem.md#144-blacklist)
        * Name muss ab dem Einbau von “Mainboard” angegeben werden.
    * Für den User müssen alle Computer im Inventar unterschiedliche Namen besitzen
        * Hinweis: Global gesehen können PCs von unterschiedliche Usern, den gleichen PC-Namen haben
* Computername kann vom Hacker geändert werden
    * Der Netzwerktreiber muss Kommunikation zulassen
    * Sobald der Fremde User die Hacker-Rolle besitzt, kann er den Computernamen genau einmal ändern. Der Hacker wird
      für Zeit x gesperrt. [wird später eventuell überarbeitet und ist abhängig von der Firewall]
    * Für Hacker-Rolle - siehe Kapitel [1.6.1.1.5.1 Rollensystem]()

* Die Computer-UUID kann abgerufen werden
* Der Name des Computers kann abgerufen werden
* Anzahl verbauter Hardwarteile eines Computers kann abgerufen werden
* Für jedes Hardwareteil eines Computers können dessen Merkmale abgerufen werden.

#### 1.7.3.2 Mindestbestandteile

Mindestbestandteile eines funktionsfähigen Computers bestehend aus 7 Teilen:

* 01 Mainboard
* 02 CPU
* 03 CPU-Kühler
* 04 RAM
* 05 Festplatte
* 06 Gehäuse
* 07 Netzteil Wenn es keine Onboard-Möglichkeit gibt, greift immer die externe Komponente -
  siehe [1.7.5 Hardwarekompatibilität.](#175-hardwarekompatibilitt)
* Grafikkarte gehört nicht zu den Mindestbestandteilen
    * OnBoard-Config ist möglich (Mainboard oder CPU)
* Netzwerkkarte gehört nicht zu den Mindestbestandteilen
    * OnBoard-Config ist möglich (Mainboard)

* Start-PC hat die Mindestbestandteile mit den leistungsschwächsten Bauteilen -
  siehe [Start-Computer](#174-start-computer)

### 1.7.4 Start-Computer

Anmerkung für GD: Start-PC Teile kosten etwas

* Hardware-Komponente
    * Option 1: false: Komponente lagern zum ersten Spieleintritt im Inventar
    * Option 2: true: Computer ist zum ersten Spieleintritt autom. erstellt
    * Einstellung steht auf => false: Komponente lagern zum ersten Spieleintritt im Inventar <br> Folglich greift dies
      nur ein mal.
    * Hardwareteile sind bei jedem Spieler gleich - siehe Tabelle in diesem Kapitel
* Die Teile des Start-PCs können nicht gelöscht, nicht verkauft und nicht versendet werden (verhindert, dass der Spieler
  aus versehen Komponenten schon vorher aus dem Inventar z.b. löscht und somit Spielunfähig wird). Beachte Besonderheit
  bei [Hardwareteile tauschen](Hardware.md#17112-hardware-kaufen)
* Start-Computer ist bis zu einem gewissen Grad konfigurierbar
    * Mainboard und Gehäuse können nicht getauscht werden, bleiben fester Bestandteil. Somit kann der Start-Computer
      nicht vollständig auseinandergebaut werden.
    * Alle anderen Teile sind konfigurierbar/Teile tauschen möglich.
* Computer wird als 1 Item (Komplett-PC) im Inventar abgelegt
* Verbraucht 1x Slot im Inventar
* Einzelteile können nicht gelöscht, nicht verkauft und nicht versendet werden

**Start-PC**
Der Start-PC definiert die Hardware die der User zum Start des Spiels bekommt. Es definiert den Leistungsschwächsten
Computer. Hardware wird in der Gameconfig definiert.

| Hardware | ID |
|---|---|
| Mainboard | Ganzzahl |
| CPU | Ganzzahl |
| ProcessorCooler | Ganzzahl |
| GPU | nicht verbaut => OnBoard |
| RAM | Ganzzahl |
| Disk | Ganzzahl |
| NetworkCard | nicht verbaut => OnBoard |
| Powerpack | Ganzzahl |
| Case | Ganzzahl |

### 1.7.5 Hardwarekompatibilität

Die genaue Kompatibilität der einzelnen Hardwareteile wird in einem Diagramm erläutert. Link zum
Diagramm: [Hardwarekompatibilität Cryptic v0.3.0](https://nextcloud.cryptic-game.net/s/oPkZze6at3LQPXo)

**Möglichkeiten Grafikeinheit GPU:**

* Option 1: OnBoard-Grafikeinheit auf Mainboard
* Option 2: OnBoard-Grafikeinheit auf CPU
* Option 3: Externe Grafikeinheit
* Computer ist mit OnBoard-Grafikeinheit lauffähig (günstige Variante).

Priorität:

* Es wird die nächst beste GPU verwendet, gemessen am Leistungswert. Wenn KEINE OnBoard-GPU vorhanden ist, dann muss
  eine externe GPU eingebaut werden!

**Möglichkeiten Netzwerkkarte NET:**

* Option 1: OnBoard-Netzwerkkarte auf Mainboard
* Option 2: Externe Netzwerkkarte
* Computer ist mit OnBoard-Netzwerkkarte lauffähig (günstige Variante).

Priorität:

* Es wird die nächst beste Netzwerkkarte verwendet, gemessen am Leistungswert. Wenn KEINE OnBoard-Netzwerkkarte
  vorhanden ist, dann muss eine externe Netzwerkkarte eingebaut werden!

**Expansion Slots / Erweiterungssteckplatz**

* Es können nur GPU, Netzwerkkarte und Disks installiert werden
* Hierbei muss das Attribute “interface” immer zusammenpassen
    * Beispiel: GPU “interface: PCI 2.0” => expansionslot “interface: PCI 2.0”
    * Interface-Name und Version müssen zusammen passen

### 1.7.6 Zusammenbauen

Teile aus dem Inventar können zum Bau eines neuen Computers verwendet werden.
**Bedingungen**:

* Alle Mindestbestandteile müssen zum erstellen eines funktionsfähigen Computers verbaut sein.
    * Computer kann aber auch “erstellt” und trotzdem unvollständig sein.
* Alle Hardware-Komponenten müssen miteinander kompatibel sein für einen funktionsfähigen Computer
* Computername muss ab Schritt 2 “Mainboard” angegeben werden. Definiton für Namen
  unter [1.7.3.1 Allgemein](#1731-allgemein) zu finden.

Reihenfolge:

| Schritt | Hardwarekomponente | Anmerkung |
|---|---|---|
| 1 | Gehäuse | Zuerst wird das Gehäuse festgelegt |
| 2 | Mainboard | Danach wird das Mainboard eingebaut |
| 3 | CPU | Danach kann die CPU eingebaut werden (Optional: CPU kann auch nach Schritt 4 eingebaut werden) |
| 3.1 | CPU-Kühler | Der CPU-Kühler kann erst nach der CPU-Komponente eingebaut werden |
| 3 &#124; 4 | RAM, Grafikkarte, Festplatte, Netzwerkkarte, Netzteil | Alle weiteren Teile können ohne Reihenfolge (aber nach Schritt 2) eingebaut werden |

* Bei jedem Bauteil, welches hinzugefügt wird, wird die Kompatibilität geprüft
    * Hinweis: Die vollständige Abfrage durch eine Funktion “Erstellen” entfällt. Somit auch ein Button “Erstellen” im
      Frontend.
    * Situation 1: Wenn kompatibel, i.O.
    * Situation 2: Wenn nicht kompatibel, wird das Bauteil nicht akzeptiert
    * Ein Computer hat folgende Stadien:
        * Status 1: Alle Bauteile sind verbaut und kompatibel. Der Computer ist vollständig und funktionsfähig (
          Betriebssystem startet).
        * Status 2: Unvollständig und nicht funktionsfähig. Ein unvollständiger Computer gilt ab Gehäuse + Mainboard und
          wenn nicht alle weiteren Mindestbestandteile verbaut sind bsp. es fehlt ein RAM-Modul.
* Sind alle Bauteile kompatibel und der Computer funktionsfähig wird die Computer-UUID erzeugt. Ansonsten nicht. Die
  UUID wird mit dem Mainboard verknüpft.
* Jeder zusammengebaute Computer ist zu Beginn ausgeschaltet
    * Ein zusammengebauter Computer zählt sobald Gehäuse und Mainboard verbunden sind.
    * Ein (neu) erstellte Computer ist Inaktiv und wird im Inventar abgelegt
* Jeder zusammengebaute Computer verbraucht 1x Slot im Inventar
    * Hinweis: Verbaute Hardwareteile verbrauchen kein Platz im Inventar

### 1.7.7 Konfiguration ändern

#### 1.7.7.1 Allgemein

* Es gibt folgende Möglichkeiten:
    * Option 1: [Computer auseinander bauen](#1772-computer-auseinander-bauen)
    * Option 2: [Hardwareteile tauschen](#1773-hardwareteile-tauschen)
* Wenn das Inventar gar keine oder zu wenige Plätze frei hat:
    * kann der Computer nicht in einem rutsch auseinander gebaut werden => Ausbauen wird gesperrt (Anzahl Teile vom
      Computer muss mit freie Plätze im Inventar verglichen werden).
    * können die Hardwareteile nur einzelnen oder gar nicht getauscht werden
* Dateien bleiben auf der Festplatte erhalten, wenn Festplatte getauscht werden sollte
* Wenn Spieler-Inventar voll
    * Auseinanderbauen nicht möglich
    * Teile tauschen nicht möglich
    * Option: Hardware kann im [Inventar](1.8) gelöscht/verkauft werden

#### 1.7.7.2 Computer auseinander bauen

* Option 1: Computer kann vollständig in einem rutsch auseinandergebaut werden
    * → Bedingung: Device muss ausgeschaltet sein - siehe [Betriebssystem](1.6.1.1)
    * UUID und Computername werden gelöscht
    * Voraussetzung es sind ausreichend Slots vorhanden.
        * Alle Hardwareteile werden im Spiel-Inventar abgelegt.
    * **Ausnahme**: Der Start-PC kann nicht auseinandergebaut werden

#### 1.7.7.3 Hardwareteile tauschen

* Option 2: Hardwareteile können einzeln ausgetauscht werden
    * → Bedingung: Device muss ausgeschaltet sein - siehe [Betriebssystem](1.6.1.1)

**Reihenfolge Teile tauschen:**

1. Zuerst können RAM, Grafikkarte, Festplatte, CPU-Kühler => CPU, Netzwerkkarte und Netzteil getauscht werden
2. Mainboard kann erst getauscht werden, wenn alle genannten Teile aus Schritt 1 entfernt sind
3. Gehäuse kann erst getauscht werden, wenn ALLE Hardwareteile entfernt sind
   **Besonderheit Onboard-Nwk/Netzwerkkarte:**

* Wenn zur Onboard-Netzwerkkarte eine Netzwerkkarte eingebaut wird, wird diese aktiv -
  siehe [Generierung der Morph-IP](1.9.6)
* Wird die Netzwerkkarte wieder ausgebaut, wird die Onboard-Karte aktiv
    * Voraussetzung: Das Mainboard besitzt eine - siehe [1.9.1.2 Generierung der Morph-Adressen]()

**Besonderheit Start-PC:**

* Fall 1 - Neue Teile: Neu eingebaute Hardwareteile können anschließend beim wieder herausnehmen nicht gelöscht oder
  verkauft werden. Voraussetzung diese werden direkt im Inventar abgelegt und nicht wiederverwendet. Diese bleiben
  unzerstörbar.
* Fall 2 - Teile tauschen: Hardwareteile die durch andere ausgetauscht werden, können anschließend gelöscht, verkauft
  oder versendet werden.
    * Voraussetzung:
        * ein Austausch (Ersetzen des vorigen Teils) findet statt.
        * die Komponente ist kompatibel
* Es muss also immer ein Komplett-Computer vorhanden sein bzw. die einzelnen Teile davon sollen nicht löschbar, nicht
  verkäuflich und nicht versendbar sein

