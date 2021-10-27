## 1.8 Inventar

erstellt von [Marius]

### 1.8.1 Basisfunktionen

Das Inventar wird genutzt um Items zu lagern

* Jeder zusammengebaute Computer, jedes unverbaute Hardwareteil, sowie Router verbraucht entsprechend 1x Slot im
  Inventar.
    * verbaute Hardwareteile verbrauchen kein Slot
* Zu Beginn des Spiels befinden sich im Inventar:
    * Alle Bestandteile für den Start-PC (abhängig von der Hardware-Gameconfig)
    * 1x Standard Spieler-Router
    * Die Startzahl darf nicht kleiner sein, als die Gesamtzahl der Teile für den Start-PC + 1x Router - Beachte
      Mindestanzahl [1.7.4 Start-Computer](../Computer/Computer.md#174-start-computer)
* Pro aktiven PC wird das Inventar um 7 Plätze erweitert
    * Nur wenn ein PC mit einem anderen, unterschiedlichen Mainboard aktiv geschaltet wird, können weitere Slots dazu
      geschaltet werden. Identifizierung anhand der Mainboard-Hardware-ID (Computername zur identifizierung ist nicht
      zulässig).
    * Die Slotanzahl kann 4x erweitert werden. Somit können max. 7*4 = 28 Slots zusätzlich freigeschaltet werden. Es ist
      also von x unterschiedlichen Mainboards abhängig => Festlegung in der Hardware-Gameconfig.
    * Wenn ein aktiver PC inaktiv geschaltet wird, bleiben die Slots weiterhin erhalten.
    * Das bereits eingesetzte Mainboard, sowie bei Neukauf und Verwendung des gleichen Mainboard-Modells, ist für die
      Erweiterung der Slots nicht zulässig.
    * **Besonderheit Gameconfig**: Wenn in der Gameconfig die max. Slotanzahl niedriger gewählt wird, als zu Beginn
      festgelegt war, bleiben die Items erhalten. Auch wenn mehr Items im Inventar enthalten sind als zugelassen. Der
      Spieler kann keine weiteren Items aufnehmen und muss entscheiden, welche seiner Items gelöscht oder verkauft
      werden, solange bis Slots frei werden.
* Der Inhalt des Inventars kann abgerufen werden
* Die Anzahl der abgelegten Items kann abgerufen werden
* Die Anzahl der noch verfügbaren Slots kann abgerufen werden
* Items können verschickt werden - siehe [1.8.2 Items verschicken](#182-items-verschicken)
* Items können gelöscht werden - siehe [1.8.3 Items löschen](#183-items-lschen)
* Items können verkauft werden - siehe [1.8.4 Items verkaufen](#184-items-verkaufen)

### 1.8.2 Items verschicken

#### 1.8.2.1 Kernfunktionen

* Einzelne Hardwareteile und Router können per User-UUID oder Usernamen an einen beliebigen Spieler mit dem
  Versanddienst gesendet werden. Spieler A (Absender) sendet an Spieler B (Empfänger).
    * Der Absender (Spieler A) muss einer dieser Daten zum Verschicken angeben.
    * **Bedingung beim Absenden**: Irgendein Computer des Versenders muss eingeschaltet sein und der Netzwerktreiber
      muss Kommunikation zulassen (Verbindung zum Internet). Nach dem Absenden kann der Computer ausgeschaltet sein
      und/oder der User (Sender und Empfänger) kann ausgeloggt sein.
    * Nur der Absender muss mit dem Versanddienst (Dispatch-Service-Server) verbunden sein, unabhängig mit was der
      Empfänger verbunden ist. Und unabhängig in welchem Netzwerk sich beide Spieler befinden.
    * Der Empfänger benötigt keinen Computer
    * Der Empfänger muss das Paket bestätigen, sodass es abgeschickt wird.
        * Erst nach dem Bestätigen vom Empfänger, wird das Paket versendet
        * Wenn das Paket nicht innerhalb von 4 h angenommen wird, verfällt das Paket und die Teile bleiben beim
          Absender.
* Das Geld wird beim Absenden direkt von Spieler A vom Versanddienst abgebucht.
    * Angabe des Wallets
    * Wenn nicht ausreichend Geld vorhanden, dann kein Paket Senden möglich
    * Das Geld wird vom Wallet Spieler A abgebucht
* Es können max. 3 Pakete in 7 Tagen versendet werden. Die Zeit wird immer ab dem Absendedatum des zuletzt gesendeten
  Pakets gemessen.
    * Anzahl Pakete
    * Intervall in Tagen
    * Es können gleichzeitig unterschiedliche Versanddienste gewählt werden
* Pro Paket können max. 5 Items verschickt werden
    * Versenden von Computern nicht möglich
* Folgendes wird beim Absender ausgegeben:
    * Das Absende- und Sendedatum wird beim Absender angezeigt
    * Zeitstempel mit Unix Timestamps
    * Ziel-User wird angezeigt
    * Aktiver Versanddienst
    * Anzahl Pakete mit Inhalt werden angezeigt
* Folgendes wird beim Empfänger ausgegeben:
    * Das Sendedatum wird beim Empfänger angezeigt
    * Zeitstempel mit Unix Timestamps
    * Absender-User wird angezeigt
    * Aktiver Versanddienst

#### 1.8.2.2 Versanddienste

* Verschiedene Versanddienste zur Auswahl
* Zeit die das Paket braucht bis zur Ankunft bei anderen Spielern

| Versandart | Paketpreis |
|---|---|
| Standardversand <br>Dauer: 3 Tage (72 Std)<br> | Kostenlos |
| Premiumversand <br>Dauer: 1 Tag (24 Std)<br> | 45 MC  |
| Premium NOW  <br>Dauer: 5 min<br> | 120 MC  |

### 1.8.3 Items löschen

* Alle Items (Computer und Hardware) können unwiderruflich im Inventar gelöscht werden
    * Item wird aus dem Inventar genommen
    * Der bisher belegte Slot wird frei
    * **Besonderheit**: Wird eine Netzwerkkarte oder ein Mainboard mit OnBoard Netzwerkkarte gelöscht, wird auch die IP
      gelöscht - siehe [1.9.1.3 Generierung](193) der Morph-Adresse Gleiche gilt auch, wenn ein Computer gelöscht hat der diese
      Konfiguration hat.
    * **Besonderheit**: Wenn eine Festplatte mit Inhalt gelöscht wird, werden auch alle darauf liegenden Dateien
      unwiderruflich gelöscht

### 1.8.4 Items verkaufen

* Nur einzelne Computer-Hardwareteile (Items) können für eine Erstattung von 20% des Kaufpreises zurückgegeben
  werden [wird zur späteren Version durch den Schrotthändler ersetzt]
    * Item wird aus dem Inventar genommen
    * Es können x Items pro Tag verkauft werden
    * Der bisher belegte Slot wird frei
* Das Geld wird direkt auf das angegebene Spieler-Wallet gebucht


