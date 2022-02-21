# Changelog

Alle MultiRoute Tour! Revisionen sind hier mit den letzten Änderungen aufgeführt.

## v1.2601 vom 03.02.2021
- Die Anzeige der Tourenergebnisse ist bei großen Touren nun viel schneller.
- Die Richtungspfeile der Touren können optional angeschaltet werden (Default: aus).
- Bugfix: manueller Upload von HH:MM(+D)-Zeitfenstern 
- Hilfstexte werden bei der Tourberechnung unter **4. Touren** beim Hovern angezeigt.

## v1.2581M vom 20.12.2021
- Geschwindigkeitsanpassungen im Tourformular sind nun möglich. Die Standardzeiten pro Profil können nun auf bis zu 10% reduziert oder 1000% erhöht werden.

## v1.2558M vom 15.11.2021
- Erweiterte Option beim Upload die Geokodierung nur hausnummerngenau oder straßengenau vorzunehmen. Ersteres setzt Hausnummern voraus, letzteres findet auch Straßen ohne Hausnummern.
- Neue API-Option beim Löschen einer Flotte oder Planung alle damit berechneten Touren zu löschen 

## v1.2533M vom 12.10.2021
- Google-Maps-QR-Codes nun auch im PDF-Gesamt-Tourenexport (bisher nur in Einzeldokumenten)

## v1.2526M vom 21.09.2021
- Zusätzliche Auftragsparameter (Skills, Streckenzuordnung, Priorität, Fahrernotizen) in API ergänzt (via Einzelabfrage http://domain/fernsteuerung/auftrag und in Tourabfrage http://domain/fernsteuerung/tour/<tour-id>)
- Neues optionales Feature im Tourformular: Optimierungsmethode (beste, gut, normal, schnell, schnellste) für große Planungen (>1500 Aufträge). Hiermit kann die Berechnung je nach Bedarf mit evtl. Qualitätseinbußen (ggf. längere Strecke/Fahrtzeit) beschleunigt werden. Default ist immer "beste", d.h. die bestmögliche Optimierung.

## v1.2520M vom 15.09.2021
- Neues Feature im Tourformular: Die kleine Waage im Feld "Maximale Anzahl Aufträge pro Fahrzeugstrecke" kann nun mit einem Klick dazu benutzt werden, um die Aufträge gleich auf alle Fahrzeuge aufzuteilen.
- Bugfix in der API: Bei einem PUT-Request zum Ändern einer Flotte konnte es dazu kommen, dass zusätzlich eine weitere, leere Flotte angelegt wurde. 

## v1.2514M vom 19.08.2021
- Gemarkungsgrenzen Rheinland-Pfalz & Hessen nun verfügbar

## v1.2511M vom 17.08.2021
- Planungsnamen bei gelöschten Planungen beibehalten

## v1.2505M vom 10.08.2021
- Schnellerer Flotteneditor bei großen Flotten (>5 Fahrzeuge)

## v1.2499M vom 06.08.2021
- Neue Adresskorrekturfunktion siehe [hier](https://multiroute-tour.de/tipps/#adressen-korrigieren-mit-google-maps) 
- Die Nummerierung der im Google- & Apple-Maps-Export ist nun der Tourenübersicht angepasst. Start & Ende erhalten keine Nummerierung mehr, sodass der erste Auftrag die Nummer 1 erhält.

## v1.2488 vom 29.07.2021
- Klickbare Karten nun verfügbar in GUI & API 

## v1.2480 vom 21.07.2021
- Neue, zusätzliche Spalten im Excelexport der Tour: Servicezeit und Skills 
- Default im Tourenformular für "Maximale Anzahl Aufträge pro Fahrzeugstrecke" von 100 auf 10 000 gesetzt um versehentliche Einschränkungen zu verhindern

## v1.2469 vom 06.07.2021
- Bugfix für das Hochladen der Flotte über GUI 
- Vorbereitungen zur individuellen Straßenanpassung und Besonderheiten beim Routing

## v1.2459 vom 15.06.2021
- Touren löschen über API

## v1.2454 vom 31.05.2021
- Bugfix Streckenzuordnung

## v1.2448M vom 18.05.2021
- LKW-Routingprofile in der API
- QR-Code Performance
- Fahrzeugzuweisung und Skills werden besser geparst
- Mehr Infos nach dem Upload (Anzahl Adressen, Aufträge etc.)
- Im Excel-Export werden Start und End-Adresse nicht mehr nummeriert
- Workaround für falsch getaggte Einbahnstraßen in OSM und besseres Logging
- Fix für case-insensitive Hausnummerzusätze
- Höhere Limits für Flotten, Touren & Planungen
- Mehrere Accounts für einen Benutzer
- Bugfixes

## v1.2423M vom 26.04.2021
- Ankunftszeit im Excelexport
- Terminologieanpassung von Start- und Endadressen im Excelexport

## v1.2396M vom 07.04.2021
- Skills Float Parsing aus Excel- oder csv-Upload
- Entfernung von überflüssigen Semikoli aus Fahrernotizen

## v1.2415M vom 22.04.2021
- Hausnummernzusatz Fix für Klein- und Großschreibung

## v1.2391M vom 24.03.2021
- Verbesserte Performance beim Touranzeigen
- API Erweiterung für LKW-Profile
