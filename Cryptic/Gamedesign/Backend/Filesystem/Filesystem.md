## **1.4 Dateisystem**

erstellt von [Marius, Tristan, Maulwurf]

>Abgeschlossen: Marius, Marcel, Yannes, Maulwurf \
Datum: 03.04.2021

<br>

**(Hinweis: Das Dateisystem ist in den <span style="text-decoration:underline;">Prozess Betriebssystem</span> eingegliedert!)**

* Jeder Spieler kann auf einem Computer Ordner und Dateien anlegen.\
Anm. Devs: Stufe je nach Rechten auswählbar
* Die Dateien und Ordner sind Festplattenabhängig, d.h. sie sind auf der jeweiligen Festplatte gespeichert unabhängig in welchem Computer sie verbaut ist.\
Anm. Devs: (PC mit mehreren Festplatten)
* Die Anzahl der Ordner und Dateien ist abhängig von der verbauten Festplatte des Computers (s. [Speichernutzung](Filesystem.md#143-speichernutzung))
* Die Dateien können nur abgerufen werden, wenn man Zugriff auf das Dateisystem der Festplatte hat.

<br>

### **1.4.1 Ordnerstruktur**

* Ordner können weitere Ordner und Dateien enthalten.
* Ordner sind vom Spieler zu benennen: - auch beim Umbenennen beachten
    * kein Name von der [Blacklist](Filesystem.md#144-blacklist)
    * RegEx: [a-zA-z0-9.\-_]{1,32}
      * 1 bis 32 Zeichen im Namen
      * Namen dürfen nur Buchstaben, Ziffern und \`.-_\` enthalten. (ASCII Großbuchstaben, Kleinbuchstaben, Punkt, Unterstrich, Minus, Ziffern (0-9) - die Namen “..” und “.” sind Verboten

* Ordner können verschoben werden (mit Inhalt).
* Ordner können gelöscht werden. Im Ordner enthaltene Dateien und Ordner werden dann rekursiv gelöscht.
* Ordner können kopiert werden (mit Inhalt, nur vollständig)
* Ordner können umbenannt werden.
* Ordner können sichtbar oder unsichtbar sein.
* Es kann abgerufen werden, welche Ordner und Dateien in einem Ordner enthalten sind (nicht rekursiv).
    * Art (Ordner/Datei), Rechte und Name

<br>

### **1.4.2 Text-Dateien**

* Dateien enthalten Texte.
* Inhalte werden auf [Blacklist](Filesystem.md#144-blacklist)-Begriffe geprüft.
* Inhalt muss UTF-8 konform sein.
* Dateien sind vom Spieler zu benennen:
    * Siehe [1.4.1 Ordnerstruktur](Filesystem.md#141-ordnerstruktur)
* Dateien können sichtbar oder unsichtbar sein, siehe <span style="text-decoration:underline;">1.6.1.1.5.2 Stufensystem</span>
* Dateien können umbenannt werden.
* Dateien können verschoben werden.
* Dateien können kopiert werden.
* Dateien können gelöscht werden.
* Der Inhalt einer Datei kann vom Spieler abgerufen werden.
* Der Inhalt einer Datei kann vom Spieler geändert werden. Abhängig vom Rechtesystem - siehe <span style="text-decoration:underline;">1.6.1.1.5 Benutzerverwaltung</span>
* Die Dateigröße kann vom Spieler abgerufen werden, abhängig von Rechten.
* Der Inhalt einer Datei darf max. 1’800 Zeichen betragen 
<br>

### **1.4.3 Speichernutzung**

* Umrechnung:
    * 1.000 MB = 1 GB
    * 1.000 GB = 1 TB
    * 1.000 TB = 1 PB
* Es können nur Ordner und Dateien angelegt werden, wenn Platz auf der verbauten Hardware (ingame Festplatte) ist.\
Anm. Dev: (Speicherbedarf bevor der Aktion ausrechnen) (Jede Festplatte einzeln betrachtet)
* Ordner verbrauchen jeweils 1 MB (Ingame) 
* Dateien verbrauchen je begonnene 20 Zeichen 5 MB (Ingame) \
**Vorgehensweise:**

Anzahl Zeichen | Speicher in MB
------------ | ------------
0-20 (leere Datei auch!) | 5 MB
21-40 | 10 MB
41-60 | 15 MB
... | ...

<br>

### **1.4.4 Blacklist**

Blacklist für beschreibbare Bereiche. Dateiinhalte, Dateinamen, Ordnernamen, PC-Benennungen, Nutzername des Spielers.

Änderungen der Blacklist treten nur mit Wirkung für die Zukunft ein, d.h. alte Dateien/Ordner bleiben bestehen.

* Bad Words gute Liste finden. Vorschlag: [Schimpfwortliste für die Option Zensur! - Closed Suggestions - WoltLab®](https://community.woltlab.com/thread/5044-schimpfwortliste-f%C3%BCr-die-option-zensur/)
* Internationalität (mindestens noch eine ENG Variante)
