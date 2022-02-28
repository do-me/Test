# API-Ablauf 

## Vokabular 

In MultiRoute Tour! spielen folgende Begriffe eine entscheidende Rolle:

* **Adressen** - eine Adressinformation wie Straße, Hausnummer, PLZ, Ort **in Verbindung** mit einer geographischen Koordinate 
* **Aufträge** - eine Auftragsinformation, wie bspw. "50 Stück, zwischen 8:30 Uhr und 11 Uhr ausliefern" 
* **Planung**  - eine Art "Container" für Aufträge, bspw. "Montag, 01.01.2025" oder "Kalenderwoche 25"
* **Flotten**  - eine Zusammenstellung von Fahrzeugen, bspw. 10 PKW, 2 LKW, 1 Sattelschlepper
* **Touren**   - eine Touroptimierung erzeugt aus einer Kombination aus **Planung** und **Flotte**

## Konzept

Diese Begriffe stehen wie folgt in Zusammenhang:

In einer **Planung** sind **Auftrag**sinformationen für bestimmte **Adressen** zusammengefasst. Wenn Sie einen Gesamt-Kundenbestand von 200 Kunden haben aber von diesen an einzelnen Wochentagen nicht alle buchen, so können in der **Planung** "Montag, 01.01.2025" z.B nur 120 **Aufträge** vorhanden sein. Am "Dienstag, 02.01.2025" hingegen bestellen 150 Kunden, sodass Sie die **Tour** jeden Tag neu optimieren sollten. 

Wenn Sie nun an unterschiedlichen Tagen auch unterschiedliche Fahrzeuge im Einsatz haben, weil Sie bspw. Springe haben oder Teilzeit-beschäftigte Mitarbeiter, können Sie sich verschiedene Flotten anlegen, bspw. eine Standard**flotte** für Mo, Di, Mi, Do mit 20 Fahrzeugen und eine Freitags**flotte**, die von dieser abweicht und nur 15 Fahrzeuge enthält. 

Diese **Flotten** bleiben gespeichert und können wiederverwendet werden. 

Sie können alle **Flotten** mit allen **Planungen** kombinieren und beliebig viele **Touren** berechnen, die so lange gespeichert bleiben, bis Sie sie löschen. Sie haben dabei volle Kontrolle über Ihre Daten.

## Datenaustausch 

Der Datenaustausch ist auf **JSON** Objekte ausgelegt, weshalb der Header: "Content-Type: application/json" bei POST-Requests mit angegeben werden muss.

## Ablauf 

* Es werden zunächst Adressen hochgeladen und geokodiert, falls keine Koordinaten mit übergeben werden.
* Anschließend wird eine leere, sogenannte Planung angelegt, die als Container für die Aufträge an den Adressen dient. Diese kann bspw. dazu dienen, alle Aufträge für einen Wochentag, bspw. Montag in einer bestimmten Kalenderwoche zusammenzufassen.
* Nachdem eine Flotte definiert wurde, kann die Tour optimiert werden.

Die Routen finden Sie [hier](/routen).
