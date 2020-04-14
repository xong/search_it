# Search it – Ein Addon zur Volltextsuche für REDAXO 5

Search it indexiert Artikel, Medien, Dateien, PDF-Inhalte und Datenbank-Felder und gibt diese als Suchergebnisse aus. Suchanfragen können außerdem in einer Cache-Tabelle gespeichert werden. Das spart Serverrechenleistung und führt zur schnelleren Anzeige von Suchergebnissen.

## Systemvoraussetzungen

* `PHP >= 7.0`
* `REDAXO >= 5.5`
* `pdftotext` [optional für das Durchsuchen von pdf-Inhalten, [Link](https://www.xpdfreader.com/pdftotext-man.html)]

## Features

* Volltextsuche für Artikel und beliebige Datenbankspalten mehrsprachenfähig
* Umfassende technische Dokumentation
* Suche im Originaltext, im Plaintext oder in beiden möglich
* Suchmodi:
  * OR (mindestens ein Suchwort muss enthalten sein)
  * AND (alle Suchworte müssen enthalten sein)
* Suche mit `LIKE` oder `MATCH AGAINST`
* Verschiedene Möglichkeiten Suchwörter hervorzuheben
* Einstellen einer maximalen Trefferanzahl
* Einstellen der maximalen Zeichenanzahl für den Teaser-Text
* automatisches (De)Indexieren von Artikeln und Spalten soweit möglich Caching von Suchanfragen
* Eingabe von Blacklistwörtern
* Ausschluss von Artikeln oder Kategorien möglich
* Ähnliche Wörter werden von der Suche automatisch vorgeschlagen
* Suchbegriffe können mit Anführungszeichen (") umschlossen werden
* Suchbegriffe können mit einer beliebigen Anzahl von vorangestellten Pluszeichen (+) höher gewichtet werden (wirkt sich auf die Reihenfolge der Ergebnisse aus)
* zwei verschieden Arten, um den Suchindex zu erneuern (wenn es Probleme mit der max_execution_time gibt)
* für Entwickler interessant: über die Methoden der search_it-Klasse kann die Suche verfeinert bzw. für mehrere Module unterschiedlich angepasst werden, außerdem ist z. B. eine Pagination von Suchergebnissen möglich
* Angabe von Kategorien, Artikeln und DB-Spalten, in denen gesucht werden soll
* Durchsuchen von beliebigen Ordnern mit beliebigen Dateien möglich
* einfache Konfiguration im Backend
* einstellbar, wer das AddOn konfigurieren darf.

## Plugins

* `Statistik`: Liefert Informationen zur Search it-Datenbank und zu den häufigsten Suchanfragen.
* `Plaintext`: Erlaubt es zu bestimmen, was in den Index aufgenommen wird

## Erste Schritte

### Hinweise zur Installation

Die Installation erfolgt über den REDAXO 5 Installer, alternativ gibt es die aktuellste Beta-Version auf [GitHub](https://github.com/friendsofredaxo/search_it).

Bei der Installation werden fünf Datenbanktabellen angelegt:
* `rex_tmp_search_it_index` für die Indexierung von Artikeln und DB-Spalten
* `rex_tmp_search_it_keywords` für die Ähnlichkeitssuche
* `rex_tmp_search_it_cache` und `rex_tmp_search_it_cacheindex_ids` für den Suchcache
* `rex_tmp_search_it_stats_searchterms` für die Statistik

Die Tabellen werden nicht in die Datenbank-Sicherung des backup-Addons miteinbezogen.

Nach der Installation sollten zunächst die Einstellungen vorgenommen werden und anschließend der Index vollständig generiert werden.

### Installationsschritte

1. Installation des aktuellen Release über GitHub oder den REDAXO-Installer
2. `Search it`-AddOn und Plugins aktivieren
3. Einstellungen von `Search it` festlegen
4. Indexierung starten
5. Suchergebnis-Artikel anlegen
6. Suchfeld-Modul / Suchfeld-Template hinzufügen
7. Suchergebnis-Modul hinzufügen

## Support

### Wo finde ich weitere Hilfe?

Search it verfügt über eine umfangreiche Dokumentation im Backend, die auch Beispielcode für das Suchformular und die Suchergebnis-Ausgabe enthält.

Die aktuelle Search it-Version wird in [FriendsOfREDAXO](https://github.com/friendsofredaxo/search_it) gepflegt. Dort können Fragen gestellt und Bugs gemeldet werden (Issues).

Fragen können auch im [REDAXO-Channel auf Slack](https://friendsofredaxo.slack.com/messages/redaxo/) gestellt werden.

### Häufige Fehler

* bleibt die Indextabelle leer, könnte ein .htaccess Zugriffsschutz die Indexierung verhindern.
* bleibt die Indextabelle leer, ist eventuell ein "Minifier" im Einsatz, der HTML-Kommentare aus dem Quellcode entfernt.
`Search it` benötigt HTML-Kommentare, um die zu indexierenden Inhalte zu markieren. Man kann auf den URL-Parameter 'search_it_build_index' prüfen, z.B. durch `rex_request('search_it_build_index', 'int', false)` - wenn er gesetzt ist, ist es ein Aufruf von `Search it`
* Findet sich im syslog die Meldung `Warning: You should not use non-secure socket connections while connecting to "my-domain.tld"` so liegt dies daran, das die eigene Domain in den Einstellungen unter System (oder bei Verwendung von des Addons `YRewrite` in den Einstellungen dort) ohne `https://` eingetragen wurde.

## Lizenz
MIT Lizenz, siehe [LICENSE.md](https://github.com/FriendsOfREDAXO/search_it/blob/master/LICENSE.md) 

## Autor
**Friends Of REDAXO** 
http://www.redaxo.org 
https://github.com/FriendsOfREDAXO 
**Projekt-Lead** 
[Norbert Micheel](https://github.com/tyrant88)

## Credits
Search it basiert auf: [RexSearch (Xong) für REDAXO 4](https://github.com/xong/rexsearch) 
[Norbert Micheel](https://github.com/tyrant88/) Portierung für R5 und aktiven Entwicklung
[Alexander Walther](https://github.com/skerbis) Dokumentation und Hilfe 
[Tobias Krais](https://github.com/tobiaskrais) URL Addon (>= 2.0) Support
[und weitere Entwickler...](https://github.com/FriendsOfREDAXO/search_it/graphs/contributors)
