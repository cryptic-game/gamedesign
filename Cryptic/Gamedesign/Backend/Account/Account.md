## **1.1 Account/User**

erstellt von [Allen]

>Abgeschlossen: Security, Defelo, Tristan \
Datum: 31.01.2021

<br>

### **1.1.1 Registrieren**

Funktion um neue Spieler zu registrieren.

Folgende Angaben müssen zwingend erfolgen:

*   Benutzername
*   Passwort

Der Benutzername muss folgende Kriterien erfüllen:

*   Länge zwischen 4 und 32 Zeichen
*   Darf nur Buchstaben (a-z, A-Z) und Zahlen (0-9) enthalten
*   Derselbe Benutzername darf nicht mehrfach vergeben werden
*   (zukünftig: Kein Name von der Blacklist)

Das Passwort muss folgende Mindestkriterien (vgl. gelber Balken) erfüllen:

*   mind. 10 Zeichen lang
*   keine Maximallänge
*   mind. 1 Großbuchstabe
*   mind. 1 Kleinbuchstabe
*   mind. 1 Zahl <span style="text-decoration:underline;">oder</span> 1 Sonderzeichen

<br>

### **1.1.2 Anmelden / Login**

Funktion, um sich als bereits registrierter Spieler anzumelden.

Folgende Angaben müssen zwingend erfolgen:

*   Benutzername
*   Passwort

Der Login hat ein Timeout von 2 Wochen (im Backend einstellbar).

<br>

### **1.1.3 Benutzerverwaltung**

*   Der User kann sein Passwort ändern. \
Er muss folgende Angaben tätigen:
    *   bisheriges Passwort
    *   neues Passwort
    *   Anforderungen an das neue Passwort: s. [Registrieren](Cryptic/Gamedesign/Backend/Account/Account.md#111-registrieren)
*   Der Benutzer kann seinen Nutzernamen monatlich 1x ändern
    *   Anforderungen  s. [Registrieren](Cryptic/Gamedesign/Backend/Account/Account.md#111-registrieren)

<br>

### **1.1.4 Verifizierungssystem**

Tokens werden nur gehashed gespeichert.

#### **1.1.4.1 Recovery Tokens**

*   Bei der Registrierung werden für jeden User 5 zufällige Recoverytokens (UUID4) generiert
*   Die Recoverytokenliste kann jederzeit erneuert werden. 
*   Mit einem Recoverytoken kann das Passwort des Accounts zurückgesetzt werden.

#### **1.1.4.2 Support Tokens**

*   Ingame kann ein Supporttoken abgerufen werden. Dieser wird erst bei Abruf generiert und ist 12 Stunden gültig. 
*   Mit einem Support Token kann ggü dem Team nachgewiesen werden, dass einem der Account gehört
    *   Der Token kann mit entsprechender Berechtigung im Adminpanel gegengeprüft werden.
