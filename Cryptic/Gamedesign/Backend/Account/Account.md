## **1.1 Account/User**

erstellt von [Allen]

>Abgeschlossen: Security, Tristan, Jannik \
Datum: 29.06.2021

<br>

### **1.1.1 OAuth2**

Wir managen die User-Accounts nicht selbst, sondern verwenden [OAuth2](https://oauth.net/2/)-Provider (z.B. Google, Discord, GitHub…). Das bedeutet, dass die Nutzer keine separate Registrierung mit E-Mail und Passwort für Cryptic benötigen.

<br>

### **1.1.2 Erster Login**

Bei dem ersten Login muss der Nutzer einen Benutzername festlegen. Dieser muss folgende Kriterien erfüllen:

*   Länge zwischen 4 und 32 Zeichen
*   Darf nur Buchstaben (a-z, A-Z) und Zahlen (0-9) enthalten
*   Derselbe Benutzername darf nicht mehrfach vergeben werden
*   Kein Name von der Blacklist

<br>

### **1.1.3 Benutzerverwaltung**

*   Der Benutzer kann seinen Nutzernamen monatlich 1x ändern
    *   Anforderungen s. [Erster Login](Account.md#112-erster-login)

<br>

### **1.1.4 Verifizierungssystem**

Tokens werden nur gehashed gespeichert.

#### **1.1.4.1 Support Tokens**

*   Ingame kann ein Supporttoken abgerufen werden. Dieser wird erst bei Abruf generiert und ist 12 Stunden gültig. 
*   Mit einem Support Token kann ggü dem Team nachgewiesen werden, dass einem der Account gehört
    *   Der Token kann mit entsprechender Berechtigung im Adminpanel gegengeprüft werden.
