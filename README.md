# Zusätzliche Values, Validates und Actions für REDAXO 5 YForm 4

Das Addon `yform_field` ergänzt YForm um weitere Feldtypen, Validierungen und Aktionen.

## Features

* **E-Mail Attachments** - nur eine Zeile, um Anhänge aus Formularen an E-Mails zu hängen
* **Echtes Datetime-Value** - optimierte HTML5-Ausgabe mit optionaler Einschränkung per min/max-Auswahl
* **`be_media` mit Bildvorschau** - zeigt statt der Dateinamen die gewählten Bilder als Vorschau
* **`be_manager_relation` als SET** - erweitert be_manager_relation um die Möglichkeit, ein Feld als echtes DB-Feld `SET` anzulegen
* **YRewrite-Domains** - SELECT-Auswahl mit der System-Domain und allen YRewrite-Domains (sofern installiert)
* **Tabs** - Formular-Felder in Tabs gruppieren

![blaupause test_redaxo_index php_page=yform_manager_table_field table_name=rex_staff func=choosenadd list=731ec268](https://github.com/alexplusde/yform_field/assets/3855487/21f9cfe5-0900-48ee-bec0-a1608125e37f)

## Installation

* Im REDAXO-Backend unter `Installer` abrufen und
* anschließend unter `Hauptmenü` > `AddOns` installieren.

Die gewünschten Feldtypen, Validierungen und Actions stehen automatisch bereit.

## Feldtypen

### `datetime_local` HTML5-Eingabefeld 

Stellt ein Eingabefeld für Datum + Uhrzeit zur Verfügung

![image](https://user-images.githubusercontent.com/3855487/209684368-44a136e7-5f75-4d72-b867-3d47eebf796e.png)

### `domain` Auswahlfeld

Stellt ein Select-Feld vom Typ `multiple` zur Verfügung, in dem als Auswahl die System-Domain (bzw. "alle") zur Verfügung steht, oder bei installiertem YRewrite auch alle passenden Domains.

![image](https://user-images.githubusercontent.com/3855487/209684633-7d1c388c-83f2-4363-90a6-fc5665580f1d.png)

### `be_media_preivew` mit Bildvorschau

Erzeugt in der YForm Datentabelle eine Vorschau des aktuell gewählten Bilds

![image](https://user-images.githubusercontent.com/3855487/209685003-546ac381-ad23-4d4e-a16d-79fcb855ba3f.png)

### be_manager_relation_set SET als Datenbankfeldtyp

Exakt dasselbe Feld wie `be_manager_relation` nur mit der zusätzlichen Auswahlmöglichkeit des Datenbankfeldtyps `SET`, verwendbar in allen `1:n`-Beziehungen, die direkt im Feldwert gespeichert werden. 

> **Tipp:** Ändere in der Datenbanktabelle `yform_field` die Felddefinition deines bestehenden `be_manager_relation`-Felds zu `be_manager_relation_set` und lösche den REDAXO-Cache, statt das Feld zu löschen und neu anzulegen.

### `be_user_select` - REDAXO-Benutzer zuordnen

Ähnlich zu `be_user` mit dem Unterschied, den Backend-Benutzer zuweisen zu können, bspw. für zusätzliche Rechtevergabe oder Verantwortlichkeiten.

### `choice_html` HTML innerhalb des durch Choice erzeugten Labels erlauben

Erlaubt HTML in der Ausgabe des Labels von `choice`, was auch gemäß HTML5 möglich ist, um bspw. ein Bild anstelle oder zusätzlich zur Auswahl zu stellen.

> **Tipp:** Ändere in der Datenbanktabelle `yform_field` die Felddefinition deines bestehenden `choice`-Felds zu `choice_html` und lösche den REDAXO-Cache, statt das Feld zu löschen und neu anzulegen.

### `form_url` - Erfahre, von wo das Formular abgeschickt wurde.

Nützlich für statistische Zwecke, wenn ein Formular seitenübergreifend eingebunden wurde und man wissen möchte, von wo es ausgefüllt wurde.

### `privacy_policy` - AGB und Tracking-Einverständnis abfragen

Stellt auf Basis einer regulären Checkbox weitere Eingabe-Informationen zur Verfügung, um bspw. auf AGB oder Datenschutzerklärung hinzuweisen, wie in diesem Beispiel:

![image](https://user-images.githubusercontent.com/3855487/209686556-46de60ad-985f-4c7b-a223-83a1cadee164.png)

### `tabs` - Formular-Felder in Tabs gruppieren

Ähnlich wie bei Fieldsets können Formulare über Tab-Sets optisch strukturiert werden. Dazu wird das Tab-Value am Anfang einer Feldgruppe eingefügt. Nach der letzten Gruppe muss ein abschließendes Tab-Value gesetzt werden. 

Im Formular sind mehrere Tab-Sets möglich, die dann aber eindeutig benannt sein müssen und sich nicht überlappen dürfen.

Es müssen mindestens drei Tab-Values (derselben Gruppe) im Formular sein:
- erster Tab: beginnt einen Tab und baut das Tab-Menü über alle Tabs des Tab-Sets auf.
- innerer Tab: jeder innere Tab schließt den vorhergehenden ab und öffnet den eigenen Container
- letzter Tab: ohne eigenen Eintrag im Tab-Menü, schließt den vorhergehenden Container und die Gruppe

Wenn in einem Tab ein Feld mit Fehlermeldung steckt, wird der Tab optisch markiert
und aktiviert.

Wurde das Formulat mit "Übernehmen" gespeichert, wird der zuletzt aktive Tab bei der
Wiederanzeige aktiv gesetzt. Ausnahme: in einem anderen Tab ist ein Feld mit Fehlermeldung.

Ein Formular kann mehrere Tab-Sets enthalten, allerdings nicht geschachtelt. In dem Fall müssel alle zu einem Tab-Set gehörenden Tab-Value denselben Gruppennamen bekommen.

## Einstellungen

Es sind keine weiteren Einstellungen vorhanden.

## Tipps und Tricks

### `attach`-Action

Die Aktion `attach` muss vor der Aktion für den E-Mail-Versand notiert werden - logisch, sonst wird erst die Mail versendet und dann der Anhang beigefügt. 

Szenario für Bewerberformulare: Durch geschickte Kombination und Reihenfolge lässt sich zunächst eine Bestätigungs-Mail an eine*n Bewerber*in ohne Anhang versenden, anschließend wird die Action eingetragen und zum Schluss eine weitere Mail-Aktion an das Unternehmen - diese ist dann mit Anhang.

### Weitere Tipps und Tricks 

Siehe auch: https://github.com/alexplusde/yform_field/issues



## Lizenz

MIT Lizenz, siehe [LICENSE.md](https://github.com/alexplusde/speed_up/blob/master/LICENSE.md)  

## Autoren

**Alexander Walther**  
https://www.alexplus.de
https://github.com/alexplusde

**Projekt-Lead**  
[Alexander Walther](https://github.com/alxndr-w)

## Credits

