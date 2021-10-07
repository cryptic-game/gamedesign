## **1.3 Wallet**

erstellt von [Marius, Tristan]

### **1.3.1 Allgemein**

Das Wallet ist an den [Spieler-Account](../Account/Account.md#11-accountuser) gebunden. Es ist für Fremde nicht angreif-
oder sichtbar. Der Owner kann auf die Wallets zugreifen, indem er das Terminal oder die Wallet-App nutzt. Eine
Authentifizierung ist nicht mehr nötig. Ein Hacker kann „Geld klauen", indem er die Befehle zum Kontostand auslesen und
Geld überweisen untergräbt/hackt. Er hat keinen direkten Zugriff auf das Wallet, sondern nur die Möglichkeit, den Owner
zu imitieren und damit eine „gehackte Transaktion durchzuführen". Siehe [Kapitel 1.6.2.5.5]() Wallet hacken.

### 1.3.2 Detailliert

* Das Wallet wird genutzt, um die Währung “[Morphcoin](../Kryptowaehrung/Kryptowaehrung.md#12-kryptowhrung)” sowie eine
  Transaktionshistorie und Einstellungen zu speichern.
* Das Wallet besitzt eine UUID als Adresse (analog IBAN). Über diese wird Geld gesendet und empfangen.
* Das Wallet ist an den Spieler-Account gebunden.
    * Nur der Spieler selber kann ein Wallet erstellen oder löschen.
    * Das Erstellen oder Löschen kann nur von einem eigenen, laufenden PC aus getätigt werden.
    * Wallet kann nicht übertragen werden.
    * Nur der Owner hat vollen Zugriff auf das Wallet. Über das Terminal kann die Transaktionsmechanik des Wallets
      gehackt werden (siehe [Wallet hacken]())


* Der Spieler kann bis zu x Wallets gleichzeitig besitzen.
    * Alle Wallets können auf allen eigenen Computern verwaltet werden


* Definition Wallet-Name
    * Name wird manuell durch den Spieler vergeben
    * Kein Name von der [Blacklist](../Filesystem/Filesystem.md#144-blacklist)
    * Regex: [A-Za-z]{3,12}
        * 3 bis 12 Zeichen (Buchstaben a-z/A-Z)
    * Name darf jederzeit geändert werden


* Zum ersten Spieleintritt ist kein Wallet vorhanden.
* Der Spieler muss Wallets manuell erstellen.
    * Voraussetzung: Computer muss eingeschaltet bzw. das OS muss vollständig [gestartet]() sein. Unabhängig auf welchem
      eigenen Computer.


* Auf dem Wallet kann ein Überweisungslimit von 1.000 bis {+inf} MC pro Tag eingestellt werden. Das Überweisungslimit
  greift immer.
    * Default-Limit: 1.000 MC / Tag
    * Das Limit ist in 500er Schritten anzugeben
    * Das Überweisungslimit kann alle 2 Tage verändert werden
    * Nur der Owner kann diese Einstellung tätigen.


* Jedes Wallet besitzt eine Sicherheitszahl. Standard 1 bis 3
    * Sicherheitszahl wird vom System generiert bei Angriff eines Hackers, s. Kapitel [Wallet hacken]()
    * Für 500 MC kann der Spieler die Sicherheitszahl für 24 Stunden auf 1 bis 4 erhöhen. Nach Ablauf der Zeit fällt die
      Zahl auf 1 bis 3 zurück.


* Einstellungen müssen für jedes Wallet einzeln vorgenommen werden.m9
    * Einstellungsänderungen werden mit Unix Timestamps geloggt


* Von allen Wallets die man besitzt, kann folgendes jeweils abgefragt werden:
    * Kontostand
    * Wallet-UUID
    * Transaktionshistorie
    * Einstellungsänderungen


* Folgen des Löschens des Wallets:
    * Der User verliert damit den Zugang zum Wallet.
    * Alle Verbindungen zum Miner, Hardware-Shop, Wallet-App, usw. werden getrennt
    * Das Wallet wird mit Inhalt (Morphcoins + UUID + Historie) unwiderruflich gelöscht

### 1.3.3 Transaktionen

* Voraussetzungen:
    * Spieler A und Spieler B besitzen jeweils mindestens ein Wallet
    * Die [Computer]() von Spieler A und Spieler B sind beide eingeschaltet


* Transaktionen können nur ausgeführt werden:
    * wenn der [Netzwerktreiber]() läuft und eine Netzwerkverbindung zwischen Sender und Empfänger besteht.
    * wenn die gewählte Summe MC auf dem gewählten Wallet vorhanden ist
    * Transaktionen können vom Besitzer des Wallets ausgeführt werden. Hacker können über eine
      Hackerattacke ([Wallet hacken]()) eine Transaktion ausführen.


* Ein Hacker kann die Transaktionsmechanik untergraben und somit als “Nicht-Owner” Geld von dem Wallet senden. Er hat
  dabei keinen direkten Zugriff auf das Konto, sondern nur auf die Transaktionsmechanik.

#### 1.3.3.1 Transaktionen von Spieler zu Spieler

* Es sind Transaktionen unter Spielern möglich (Geld überweisen).
* Es können MCs von Wallet zu Wallet transferiert werden. Auch an eigene Wallets \
  **Absender:**\
  Folgende Angaben macht der Spieler selbst:
    * Angabe des Ziel-Wallets mit der Wallet-UUID
    * Angabe der Summe [Gleitkommazahl]
    * Optional: Nachricht [Text]
        * RegEx: [A-Za-z0-9,. ]{0,150}
            * max. 150 Zeichen
            * Buchstaben (a-z, A-Z) und Zahlen 0-9, Leerzeichen und Punkt “.”
        * Wörter mit [Blacklist](../Filesystem/Filesystem.md#144-blacklist) prüfen
    * Zeitstempel Absenden wird automatisch gesetzt.\
      \
      **Empfänger:**
    * Absender Wallet-UUID
    * Empfänger Wallet-UUID
    * Summe in MC
    * Zeitstempel Empfangen wird automatisch gesetzt
    * Optional: Nachricht des Absenders [Text]

#### 1.3.3.2 Transaktionen zwischen Spielern und System-Servern

* Es sind Transaktionen mit dem [Hardware-Shop]() möglich (Teile kaufen)
* Es sind Transaktionen mit dem [Versanddienst]() möglich (Versand für Hardware zahlen)
* Es sind Transaktionen mit dem [Inventar]() möglich (Teile verkaufen)
* Es sind Transaktionen mit [versteckten]() oder [öffentlichen Netzwerken]() möglich (Für Zugriff zahlen).
* Es können MCs von Wallet zu Service transferiert werden.\
  \
  **Transaktion wird automatisch ausgeführt.**\
  Folgende Informationen erhält der Spieler:
    * Abgebucht/Überwiesen von:  z.b. Hardware-Shop
    * Summe in MC z.b. Betrag der Hardwareteile
    * Autom. Nachricht [Text] zb Name und Anzahl der Hardwareteile
    * Zeitstempel Absenden im Unix Timestamp wird automatisch gesetzt

#### 1.3.3.3 Transaktionen von Miner an Spieler

* Es werden Morphcoins vom [Miner]() zum Wallet transferiert.\
  \
  **Empfänger:**
    * Empfänger ist immer der User
    * Absender Miner von Computer X
    * Empfänger Wallet-UUID Spieler
    * Summe in MC
    * Zeitstempel Empfangen im Unix Timestamp wird automatisch gesetzt
    * Autom. Nachricht [Text] Miner leeren

* Absender ist der Miner

### 1.3.4 Transaktionshistorie

* Die letzten 30 Transaktionen werden chronologisch gespeichert und können abgerufen werden (Transaktionshistorie).
    * Transaktionen, die durch Hacks ausgeführt wurden, werden in der Historie gesondert gekennzeichnet.
* Die letzten 15 Einstellungsänderungen werden chronologisch gespeichert und können abgerufen werden. 