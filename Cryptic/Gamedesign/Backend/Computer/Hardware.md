### 1.7.1 Hardware

```Anmerkung: Die Daten der Hardware werden separat in einer Spielparameter-Datei gespeichert und dort bearbeitet.```

**Allgemeines**:

* Die Tabellen stellen nur das Grundgerüst jeder Hardware dar (ohne Inhalt)
    * In der Gameconfig wird die Hardware mit Inhalt definiert
* Jedes Hardwareteil ist mit einer einzigartigen ID gekennzeichnet. Die ID darf niemals geändert werden.
    * Ersten zwei Ziffern geben die Hardware an und die nächsten zwei Ziffern den Index des Elements.
        * Mainboard 01
        * Index 05
        * Beispiel: 0105
* Jede Hardware hat einen Namen
* Jede Hardware hat einen festen Preis
* Jede Hardware hat ein “powerUsage” Attribute [noch ohne Stromkostenrechnung]
* Betrifft auch Netzwerk-Hardware - [siehe Router](1.9.2)

<br>

#### 1.7.1.1 Definition Mainboard

|Attribute | Bezeichnung | Einheit |
|---|---|---|
| id | Definiert eine einzigartige Zahl für das Element. Ersten zwei Ziffern geben die Hardware an und die nächsten zwei Ziffern den Index des Elements. Mainboard 01 Index 05 Beispiel: 0105  | Ganzzahl |
| name | Der Name der Hardware | Text |
| case | Größe des Mainboards gibt an, ob es ins Gehäuse passt. (ATX,...) | Text |
| cpuSocket  | Socket der CPU | Text |
| coreTemperatureControl  | Temperaturkontrolle der CPU  (ohne Funktion) | Boolean |
| usbPorts  | Anzahl der USB-Ports  (ohne Funktion) | Ganzzahl |
| **ram (Nur Obergruppe)** | **RAM-Objekt** |  |
| ramSlots  | Anzahl wieviele RAM-Slots das Mainboard hat | Ganzzahl |
| maxRamSize  | Maximale Größe aller RAM-Riegel zusammen in MB | Ganzzahl |
| ramTyp  | Typ RAM z.b. DDR1, DDR2, usw. | Array von Text |
| frequency  | RAM-Frequenz die kompatibel mit dem Mainboard sind in MHz | Array von Ganzzahlen |
| **graphicUnitOnBoard**  | **graphicUnitOnBoard-Objekt**<br> Werden Spezifikationen angegeben, ist eine Grafikeinheit vorhanden, wenn nicht, ist keine Grafikeinheit vorhanden. |  |
| name  | Name der OnBoard Grafikeinheit | Text |
| vRamSize  | VRAM-Größe in MB | Ganzzahl |
| frequency  | VRAM-Frequenz der Grafikeinheit in MHz | Ganzzahl |
| capabilityGPU | Sagt aus wieviel GPU-Leistung es für das Workloadsystem bereitstellt | Ganzzahl |
| **expansionSlots**  | **Erweiterungs-Steckplätze-Objekt** |  |
| interface  | Schnittstelle mit Version z.b. AGP 1.0, PCI 1.0 Kann mehrere, in der Version unterschiedliche Schnittstellen enthalten | Array von Text |
| interfaceSlots  | Anzahl der Steckplätze pro Interface | Array von Ganzzahlen |
| **diskStorage**  | **Festplatten-Objekt** |  |
| diskSlots | Anzahl der Festplatten Steckplätze | Array von Ganzzahlen |
| interface  | Schnittstelle mit Version z.b. IDE 1.0, SATA 1.0 | Array von Text |
| **networkPort** | **Netzwerk-Objekt** |  |
| networkPortOnBoard | Sagt aus, ob eine OnBoard Netzwerkkarte vorhanden ist oder nicht. Kann true oder false sein. Es gibt nur Onboard oder externe Netzwerkkarte | Boolean |
| capabilityNET | Sagt aus wieviel Netzwerkleistung es für das Workloadsystem bereitstellt | Ganzzahl |
| name  | Netzwerkkarten-Name | Text |
| connectorType | Schnittstelle zum Router | Text |
| ports | Anzahl der Steckplätze | Ganzzahl |
| speed  | Geschwindigkeit der Netzwerkverbindung in MB/s | Ganzzahl |
| powerUsage | Energieverbrauch in Watt | Ganzzahl |
| price | Der Preis der Hardware in MC | Ganzzahl |

#### 1.7.1.4 Definition CPU

| Attribute | Bezeichnung | Einheit |
|---|---|---|
| id | Definiert eine einzigartige Zahl für das Element. | Ganzzahl |
| name | Der Name der Hardware | Text |
| frequencyMin | Minimale CPU-Frequenz der CPU in MHz | Ganzzahl |
| frequencyMax | Maximale CPU-Frequenz der CPU in MHz | Ganzzahl |
| socket | Socket-Bezeichnung der CPU | Text |
| cores | Anzahl der Rechenkerne | Ganzzahl |
| turboSpeed | Max Turbo-Frequenz möglich / True oder False (ohne Funktion) | Boolean |
| overClock | Übertakten der CPU / True oder False (ohne Funktion) | Boolean |
| maxTemperature | Maximale CPU Temperatur (ohne Funktion) | Ganzzahl |
| **graphicUnit** | **graphicUnit-Attribut-Objekt** |  |
| name | Name der internen Grafikeinheit / kann auch None sein | Text |
| VRamSize | VRAM-Größe in MB / kann auch None sein | Ganzzahl |
| frequency | VRAM-Frequenz der Grafikeinheit in MHz / kann auch None sein | Ganzzahl |
| capabilityGPU | Sagt aus wieviel GPU-Leistung es für das Workloadsystem bereitstellt | Ganzzahl |
| capabilityCPU | Sagt aus wieviel CPU-Leistung es für das Workloadsystem bereitstellt | Ganzzahl |
| powerUsage | Energieverbrauch in Watt | Ganzzahl |
| price | Der Preis der Hardware in MC | Ganzzahl |

#### 1.7.1.5 Definition CPU-Kühler

| Attribute       | Bezeichnung     | Einheit     |
|---|---|---|
| id     | Definiert eine einzigartige Zahl für das Element     | Ganzzahl     |
| name     | Der Name der Hardware     | Text     |
| coolerSpeed     | CPU-Kühler Geschwindigkeit     | Ganzzahl     |
| socket     | Socket der CPU     | Text     |
| powerUsage     | Energieverbrauch in Watt     | Ganzzahl     |
| price     | Der Preis der Hardware in MC     | Ganzzahl        |

####1.7.1.6 Definition RAM
| Attribute | Bezeichnung | Einheit |
|---|---|---|
| id | Definiert eine einzigartige Zahl für das Element | Ganzzahl |
| name | Der Name der Hardware | Text |
| ramSize | Speichergröße des RAM | Ganzzahl |
| ramTyp | RAM-Speicher-Art (üblicherweise DDR SDRAM [DDR4,...]) | Text |
| frequency | RAM-Frequenz in MHz | Ganzzahl |
| capabilityRAM | Sagt aus wieviel RAM-Leistung es für das Workloadsystem bereitstellt | Ganzzahl |
| powerUsage | Energieverbrauch in Watt | Ganzzahl |
| price | Der Preis der Hardware in MC | Ganzzahl |

####1.7.1.7 Definition Grafikkarte
| Attribute | Bezeichnung | Einheit |
|---|---|---|
| id | Definiert eine einzigartige Zahl für das Element | Ganzzahl |
| name | Der Name der Hardware | Text |
| VRamSize | VRAM-Größe in MB | Ganzzahl |
| VRamTyp | VRAM-Speicher-Art (GDDR1, GDDR2...) | Text |
| frequency | VRAM-Frequenz der Grafikeinheit in MHz | Ganzzahl |
| interface | Schnittstelle mit Version z.b. AGP 1.0, PCI 1.0 | Text |
| capabilityGPU | Sagt aus wieviel GPU-Leistung es für das Workloadsystem bereitstellt | Ganzzahl |
| powerUsage | Energieverbrauch in Watt | Ganzzahl |
| price | Der Preis der Hardware in MC | Ganzzahl |

####1.7.1.8 Definition Festplatte

| Attribute | Bezeichnung | Einheit |
|---|---|---|
| id | Definiert eine einzigartige Zahl für das Element | Ganzzahl |
| name | Der Name der Hardware | Text |
| diskTyp | Welcher Typ Festplatte zb HDD, SSD, m.2 | Text |
| capacity | Speichergröße der Festplatte in MB | Ganzzahl |
| writingSpeed | Schreibgeschwindigkeit in MB/s | Ganzzahl |
| readingSpeed | Lesegeschwindigkeit in MB/s | Ganzzahl |
| interface | Schnittstelle mit Version z.b. IDE 1.0, SATA 1.0 | Text |
| powerUsage | Energieverbrauch in Watt | Ganzzahl |
| price | Der Preis der Hardware in MC | Ganzzahl |

*   Auf der Festplatte werden alle Dateien gespeichert z.b. Ordner, Textdateien [Später: Malware, Software] - [siehe Speichernutzung](../Filesystem/Filesystem.md#143-speichernutzung)
*   Mit jeder weiteren Festplatte wird deren Kapazität aufaddiert (Gesamtkapazität)
*   Eine einzelne Festplatte muss jeweils genügend Speicherplatz für die Systemdateien des Betriebssystems haben.

####1.7.1.9 Definition Netzwerkkarte
| Attribute | Bezeichnung | Einheit |
|---|---|---|
| id | Definiert eine einzigartige Zahl für das Element | Ganzzahl |
| name | Der Name der Hardware | Text |
| interface | Schnittstelle z.b. PCIe | Text |
| connectorType | Anschlusstyp zb RJ45 | Text |
| speed | Übertragungsrate in MB/s | Ganzzahl |
| capabilityNET | Sagt aus wieviel Netzwerkleistung es für das Workloadsystem bereitstellt | Ganzzahl |
| powerUsage | Energieverbrauch in Watt | Ganzzahl |
| price | Der Preis der Hardware in MC | Ganzzahl |

####1.7.1.10 Definition Netzteil

| Attribute | Bezeichnung | Einheit |
|---|---|---|
| id | Definiert eine einzigartige Zahl für das Element | Ganzzahl |
| name | Der Name der Hardware | Text |
| totalPower | Muss in Summe aller Hardwarteile genügend Leistung (Watt) zur Verfügung stellen | Ganzzahl |
| price | Der Preis der Hardware in MC | Ganzzahl |

####1.7.1.11 Definition Gehäuse
| Attribute | Bezeichnung | Einheit |
|---|---|---|
| id | Definiert eine einzigartige Zahl für das Element | Ganzzahl |
| case | Der Name der Hardware | Text |
| size | Größe des Gehäuse als Name zb. Midi, ITX, ATX Größenstufen Beispiel: Midi (klein) ITX (mittel) ATX (groß) | Text |
| price | Der Preis der Hardware in MC | Ganzzahl |

####1.7.1.12 Hardware kaufen
*   Jede Hardware bekommt einen festen Preis.
    *   Wenn Hardwarepreis -1 MC entspricht, wird diese nicht zum verkauf angeboten
*   Jede Hardware ist käuflich mit der Ingame-Währung
*   Es können 1-n Elemente auf einmal gekauft werden (abhängig vom Kontostand)
*   Dem Hardware-Shop kann immer ein Wallet zugewiesen werden (-> Settings für BE)
    *   Änderung des Wallets jederzeit möglich
*   Wird Hardware gekauft, wird der Gesamtbetrag autom. vom Wallet abgebucht
    *   Wenn nicht genügend Geld vorhanden, kein Hardwarekauf möglich
    *   Das Geld wird beim eingestellten User-Wallet abgebucht
*   Wird Hardware gekauft wird diese im [Inventar](1.7.8) abgelegt
*   Jedes Merkmal einer Hardwarekomponente kann abgerufen werden
*   Es muss eine aktive Verbindung zum [Hardware-Shop-Server]() bestehen. Diese liegt vor, wenn auf einem PC, der dem Nutzer gehört, ein aktiver Netzwerktreiber läuft und eine Verbindung zum entsprechenden Server hergestellt werden kann.
