# Routen & Endpunkte 

## Normaler Ablauf 

1. Adressen hochladen <http://domain/fernsteuerung/add_and_update_adresse>
2. Adressen prüfen wenn ohne Koordinaten hochgeladen http://domain/fernsteuerung/check_geocode?upload_id=ID-des-Uploads
3. Planung anlegen http://domain/fernsteuerung/planung/add_and_update
4. Aufträge an Adresse spielen und Planung zuweisen http://domain/fernsteuerung/auftrag
5. Flotte anlegen http://domain/fernsteuerung/flotte
6. Tourberechnung starten http://domain/fernsteuerung/tour/berechnen
7. Prüfen ob Tourberechnung fertig http://domain/fernsteuerung/touren?limit=1&planung=Name-der-Planung
8. Tour abfragen http://domain/fernsteuerung/tour/ID-der-Tour

## Authentifizierung 

Die Authentifizierung findet mittels mittels Basic Auth (http://username:password@domain/) statt. 

`domain` steht dabei für die Domain unter der Sie auf MultiRoute Tour! zugreifen. Für die SaaS lautet die Domain [https://tour.multiroute.de](https://tour.multiroute.de). 

Sie können Ihren Account auch einer Konfigurationsdatei für einen schnelleren und sicheren Login hinterlegen.

## 1 Adressen

### Abrufen

<http://domain/fernsteuerung/adresse>

Parameter (optional):

|                |                                                                                                                                                                     |
|----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| limit          | Limit                                                                                                                                                               |
| offset         | Offset                                                                                                                                                              |
| koordinaten    | Gibt Koordinaten mit aus (optional default false)                                                                                                                   |
| kommentar      | Gibt Kommentar mit aus (optional default false)                                                                                                                     |
| alle\_ausgaben | Gibt nur zugeordnete Adressen aus (Bezirk und Ausgabe werden als Array ausgegeben (Adresse kann in verschiedenen Ausgaben sein) (optional default false)            |
| starthaus      | Gibt nur Adressen die Starthaus sind aus (Bezirk und Ausgabe werden als Array ausgegeben (Adresse kann in verschiedenen Ausgaben sein) (optional default false)     |
| zustellerhaus  | Gibt nur Adressen die Zustellerhaus sind aus (Bezirk und Ausgabe werden als Array ausgegeben (Adresse kann in verschiedenen Ausgaben sein) (optional default false) |
| endhaus        | Gibt nur Adressen die Endhaus sind aus (Bezirk und Ausgabe werden als Array ausgegeben (Adresse kann in verschiedenen Ausgaben sein) (optional default false)       |
| depot          | Gibt nur Adressen die Depot sind aus (Bezirk und Ausgabe werden als Array ausgegeben (Adresse kann in verschiedenen Ausgaben sein) (optional default false)         |
| ausgabe        | Name der Ausgabe (funktioniert nur mit \[alle\_ausgaben,starthaus,zustellerhaus,endhaus,depot\])                                                                    |

Optionale Filter Parameter:

|                    |                                                                                                      |
|--------------------|------------------------------------------------------------------------------------------------------|
| oi                 | Gebäude ids                                                                                          |
| plz                | Postleitzahl                                                                                         |
| ort                | Ort                                                                                                  |
| ort\_zusatz        | Ortsteil                                                                                             |
| strasse            | Strasse                                                                                              |
| hausnummer         | Hausnummer                                                                                           |
| hausnummer\_zusatz | Hausnummer Zusatz                                                                                    |
| street\_oi         | Straßenabschnitts-ID                                                                                 |
| manuell            | true (Gibt nur durch Kartenklick erfasste Adressen aus (GBC Nummer))                                 |
| ohne\_koordinaten  | true (Adressen ohne Koordinaten)                                                                     |
| upload\_id         | Gibt nur die Adressen zurück die mit dieser id übermittelt wurden (Rückgabewert Adressen hinzufügen) |

Rückgabe:  

    [{
        "oi": "OOI1411",
        "plz": "10115",
        "ort": "Berlin",
        "ort_zusatz": null,
        "strasse": "Ackerstraße",
        "hausnummer": "172",
        "hausnummer_zusatz": "",
        "is_active": true,
        "privathaushalte": 1,
        "gewerbebetriebe": 2
    }, {
        "oi": "OOI1412",
        "plz": "10115",
        "ort": "Berlin",
        "ort_zusatz": null,
        "strasse": "Ackerstraße",
        "hausnummer": "173",
        "hausnummer_zusatz": "",
        "is_active": true,
        "privathaushalte": null,
        "gewerbebetriebe": null
    }, {
        "oi": "OOI1413",
        "plz": "10115",
        "ort": "Berlin",
        "ort_zusatz": null,
        "strasse": "Ackerstraße",
        "hausnummer": "174",
        "hausnummer_zusatz": "",
        "is_active": true,
        "privathaushalte": null,
        "gewerbebetriebe": null
    }]

Rückgabe mit alle\_ausgaben:  

    [{
        "oi": "12760120275582",
        "plz": "35075",
        "ort": "Gladenbach",
        "ortsteil": "",
        "ort_zusatz": null,
        "strasse": "Adolf-Theis-Straße",
        "hausnummer": "12",
        "hausnummer_zusatz": "",
        "is_active": true,
        "notice": null,
        "street_oi": "0000386499",
        "privathaushalte": 2,
        "gewerbebetriebe": 0,
        "werbeverweigerer": null,
        "ausgabe_bezirk": [{
            "nr": "B201015Z",
            "ausgabe": "Freitag" 
        }, {
            "nr": "B201015Z",
            "ausgabe": "Montag" 
        }, {
            "nr": "B201015Z",
            "ausgabe": "Dienstag" 
        }, {
            "nr": "B201015V",
            "ausgabe": "Vollverteilung" 
        }, {
            "nr": "B201015Z",
            "ausgabe": "Vollverteilung" 
        }, {
            "nr": "B201015Z",
            "ausgabe": "Donnerstag" 
        }, {
            "nr": "B201015Z",
            "ausgabe": "Test Meier Abo 24.03.17" 
        }, {
            "nr": "B201015Z",
            "ausgabe": "Samstag" 
        }, {
            "nr": "B201015Z",
            "ausgabe": "Sonntag" 
        }, {
            "nr": "T201055",
            "ausgabe": "Test Meier Abo 24.03.17" 
        }, {
            "nr": "T201055",
            "ausgabe": "Test" 
        }]
    }, {
        "oi": "12760120388646",
        "plz": "35075",
        "ort": "Gladenbach",
        "ortsteil": "",
        "ort_zusatz": null,
        "strasse": "Adolf-Theis-Straße",
        "hausnummer": "13",
        "hausnummer_zusatz": "",
        "is_active": true,
        "notice": null,
        "street_oi": "0000386499",
        "privathaushalte": 2,
        "gewerbebetriebe": 0,
        "werbeverweigerer": null,
        "ausgabe_bezirk": [{
            "nr": "T201055",
            "ausgabe": "Test" 
        }, {
            "nr": "B201015Z",
            "ausgabe": "Montag" 
        }, {
            "nr": "B201015Z",
            "ausgabe": "Dienstag" 
        }, {
            "nr": "B201015Z",
            "ausgabe": "Donnerstag" 
        }, {
            "nr": "B201015V",
            "ausgabe": "Vollverteilung" 
        }, {
            "nr": "B201015Z",
            "ausgabe": "Vollverteilung" 
        }, {
            "nr": "B201015Z",
            "ausgabe": "Freitag" 
        }, {
            "nr": "B201015Z",
            "ausgabe": "Test Meier Abo 24.03.17" 
        }, {
            "nr": "B201015Z",
            "ausgabe": "Samstag" 
        }, {
            "nr": "T201055",
            "ausgabe": "Test Meier Abo 24.03.17" 
        }]
    }, {
        "oi": "12760120264124",
        "plz": "35075",
        "ort": "Gladenbach",
        "ortsteil": "",
        "ort_zusatz": null,
        "strasse": "Adolf-Theis-Straße",
        "hausnummer": "14",
        "hausnummer_zusatz": "",
        "is_active": true,
        "notice": null,
        "street_oi": "0000386499",
        "privathaushalte": 1,
        "gewerbebetriebe": 0,
        "werbeverweigerer": null,
        "ausgabe_bezirk": [{
            "nr": "T201055",
            "ausgabe": "Test" 
        }, {
            "nr": "B201015V",
            "ausgabe": "Vollverteilung" 
        }, {
            "nr": "B201015Z",
            "ausgabe": "Sonntag" 
        }, {
            "nr": "T201055",
            "ausgabe": "Test Meier Abo 24.03.17" 
        }, {
            "nr": "B201015Z",
            "ausgabe": "Donnerstag" 
        }, {
            "nr": "B201015Z",
            "ausgabe": "Vollverteilung" 
        }, {
            "nr": "B201015Z",
            "ausgabe": "Test Meier Abo 24.03.17" 
        }, {
            "nr": "B201015Z",
            "ausgabe": "Freitag" 
        }, {
            "nr": "B201015Z",
            "ausgabe": "Dienstag" 
        }, {
            "nr": "B201015Z",
            "ausgabe": "Montag" 
        }, {
            "nr": "B201015Z",
            "ausgabe": "Samstag" 
        }]
    }]

### Geokodierung prüfen

<http://domain/fernsteuerung/check_geocode?upload_id=upload_id>

Parameter:

|               |                                                                |
|---------------|----------------------------------------------------------------|
| upload\_id    | Id welche man erhält, wenn man Adressen hinzugefügt hat        |
| status        | null oder "Geokodierung gestartet" bzw. "Geokodierung beendet" |
| geocoded      | Anzahl Adressen mit Koordinaten                                |
| not\_geocoded | Anzahl Adressen ohne Koordinaten                               |

    {
      "upload_id":60,
      "status":"Geokodierung beendet",
      "geocoded":4,
      "not_geocoded":0
    }

### Adressen hinzufügen/updaten

<http://domain/fernsteuerung/add_and_update_adresse>

Parameter:

|         |                                                                |
|---------|----------------------------------------------------------------|
| adresse | Adresse Parameter                                              |
| insert  | true(default) oder false. Nur neue Adressen werden hinzugefügt |
| update  | true(default) oder false. Bestehende Adressen werden geupdated |

Adresse Parameter:

|                    |                                   |
|--------------------|-----------------------------------|
| oi                 | Gebäude ID (required)             |
| street\_oi         | Straßen ID                        |
| longitude          | Längengrad (required)             |
| latitude           | Breitengrad (required)            |
| plz                | Postleitzahl                      |
| ort                | Ort                               |
| ort\_zusatz        | Ort Zusatz                        |
| ortsteil           | Ortsteil                          |
| strasse            | Strasse                           |
| hausnummer         | Hausnummer                        |
| hausnummer\_zusatz | Hausnummer Zusatz                 |
| is\_active         | Haus ist aktiv (required)         |
| privathaushalte    | Anzahl Werbeverweigerer (integer) |
| gewerbebetriebe    | Anzahl Werbeverweigerer (integer) |
| werbeverweigerer   | Anzahl Werbeverweigerer (integer) |

Rückgabe:

|            |                                            |
|------------|--------------------------------------------|
| upload\_id | Upload Id (siehe Filter adressen abfragen) |
| text       |                                            |
| added      | Anzahl hinzugefügte Adresssen              |
| updated    | Anzahl aktualisiete Adresssen              |

    {
    "update": true,
    "insert": true, 
    "adresse": [{
        "oi": "GBC93385",
        "plz": "10119",
        "ort": "Berlin",
        "ort_zusatz": null,
        "strasse": "Schwedter Straße",
        "hausnummer": "22",
        "hausnummer_zusatz": "",
        "is_active": true,
        "notice": null,
        "privathaushalte": 0,
        "gewerbebetriebe": 0,
        "werbeverweigerer": 0,
        "longitude": 52.5347133208835,
        "latitude": 13.4075689315796
    }, {
        "oi": "GBC360693",
        "plz": "84030",
        "ort": "Ergolding",
        "ort_zusatz": null,
        "strasse": "Schinderstraßl",
        "hausnummer": "5",
        "hausnummer_zusatz": "D",
        "is_active": true,
        "notice": null,
        "privathaushalte": 0,
        "gewerbebetriebe": 0,
        "werbeverweigerer": null,
        "longitude": 12.1660333871841,
        "latitude": 48.5649005287186
    }]
     }

    {"upload_id":51,"text":"1 Adressen hinzugefügt, 0 Adressen geupdated ","added":1,"updated":0}

### Löschen

<http://domain/fernsteuerung/delete_adresse>

|     |            |
|-----|------------|
| oi  | Adresse ID |

    {
    "oi": ["3353880","2739684","DEBYv00099005586","DEBYv00099000331","DEBYv00099029356","DEBYv00099001121","DEBYv00099000328"]
    }

## 2 Aufträge

Aufträge werden im Tour! Modul bearbeitet anstelle der Abonnenten aus
dem Go! Modul.  
Der Zugriff auf das Auftrags-Modell erfolgt über eine
REST-Schnittstelle.  
**Wichtig!** Auch wenn Aufträge Referenzen zur Adresse und zur Planung
besitzen, müssen weiterhin Planungs-Definitionen eingerichtet werden
damit die Aufträge in der Optimierung berücksichtigt werden.  
Diese Planungs-Definitionen werden bei einem PUT oder POST Request
standardmäßig erstellt.  
Wenn das genannte Standardverhalten verhindert werden soll, dann fügt
man den Request-Parametern das folgende KeyValue-Paar hinzu:
{"set\_active": "false"}.

### Externer Identifier in Aufträgen

Sie können alternativ zum gestellten 'id'-Attribut auch einen Identifier
"ext\_id" mitgeben, womit Sie auf ihre Aufträge referenzieren und
zugreifen können -  
vorausgesetzt, Sie liefern einen solchen externen Identifier 'ext\_id'
mit beim Anlegen der Aufträge.  
Die Schnittstelle überprüft, dass beim Anlegen eines Auftrags die
'ext\_id' einzigartig ist.  
Der externe Identifier kann bei bestehenden Aufträgen nicht nachträglich
per PUT-Request bearbeitet werden.

### Parameter für POST und PUT Requests

Verwenden Sie POST-Requests zum hinzufügen von neuen Aufträgen:  
POST <http://domain/fernsteuerung/auftrag>

POST-Requests können keine bestehenden Aufträge überschreiben!  
Verwenden Sie stattdessen PUT-Requests, um Aufträge zu bearbeiten:  
PUT <http://domain/fernsteuerung/auftrag>

Liefern Sie dem Request ein Array mit dem Namen 'auftraege'.  
Jeder Eintrag im 'auftraege'-Array repräsentiert genau einen Auftrag mit
den folgenden Attributen:

Referenz-Parameter:

| **Attribut** | **Beschreibung**       | **im POST-Request**                            | **im PUT-Request**                              |
|--------------|------------------------|------------------------------------------------|-------------------------------------------------|
| id           | interner Identifier    | ignoriert                                      | Pflichtfeld, wenn keine 'ext\_id' angegeben ist |
| ext\_id      | externer Identifier    | optional                                       | Pflichtfeld, wenn keine 'id' angegeben ist      |
| adresse\_id  | interne ID der Adresse | Pflichtfeld, wenn keine adresse\_oid angegeben | optional                                        |
| adresse\_oid | Objekt-ID der Adresse  | Pflichtfeld, wenn keine adresse\_id angegeben  | optional; ignoriert, wenn adresse\_id angegeben |
| planung\_id  | interne ID der Planung | Pflichtfeld, wenn keine planung\_nr angegeben  | optional                                        |
| planung\_nr  | Nr der Planung         | Pflichtfeld, wenn keine planung\_id angegeben  | optional; ignoriert, wenn planung\_id angegeben |

Optionale Parameter:

| **Attribut**           | **Beschreibung**                             | **default-Wert**    |
|------------------------|----------------------------------------------|---------------------|
| name                   | Bezeichnung des Auftrags                     | "Kein Auftragsname" |
| capacity               | für den Auftrag benötigte Kapazität\*        | 0                   |
| servicetime            | individuelle Servicezeit des Auftrags        | 0                   |
| timewindows            | Zeitfenster des Auftrags im HHMMD-Format\*\* | "\[\]"              |
| servicetime\_per\_job  | Parameter für die Servicezeit-Ermittlung\*\* | true                |
| servicetime\_per\_unit | Parameter für die Servicezeit-Ermittlung\*\* | true                |
| servicetime\_per\_indi | Parameter für die Servicezeit-Ermittlung\*\* | true                |
| priority               | Priorität                                    | 0                   |
| description            | Notizen für Fahrer                           | null                |
| driver\_numbers        | Streckenzuordnung                            | null                |
| skills                 | Skills                                       | null                |

\\\* Falls im System die Gewichtseinheit "kg" eingestellt ist: Geben sie
die Kapazität in **Gramm** an.  
\\\*\* Erklärung zum HHMMD-Format und der Servicezeit-Ermittlung folgen
in den nächsten Kapiteln.

Request:  

    {
      "auftraege": [{
        "ext_id": "1209e8e98fuweq9f8dh" 
        "adresse_oid": "0007",
        "planung_nr": "Montag",
        "name": "Herr Mohn",
        "timewindows": "[08:00,12:00];[14:00,18:00]",
        "capacity": "2000" 
      }]
    }

  
Response:  

    {
      "status": 200,
      "text": "Aufträge erfolgreich angelegt.",
      "auftraege": [
        {
          "ext_id": 1209e8e98fuweq9f8dh,
          "id": 1967
        }
      ]
    }

### Parameter für GET- und DELETE-Requests

Verwenden Sie GET-Requests, um einzelne Aufträge abzurufen:  
GET <http://domain/fernsteuerung/auftrag/auftragsid>
GET <http://domain/fernsteuerung/auftrag/ext/externe_id>

Verwenden Sie DELETE-Requests, um einzelne Aufträge zu löschen:  
DELETE <http://domain/fernsteuerung/auftrag/auftragsid>  
DELETE <http://domain/fernsteuerung/auftrag/ext/externe_id>

Sie können auch mehrere Aufträge gleichzeitig abrufen bzw. löschen und
zuvor filtern:

GET <http://domain/fernsteuerung/auftrag/>  
DELETE <http://domain/fernsteuerung/auftrag/>

| **Referenz-Attribut** | **Beschreibung**        |
|-----------------------|-------------------------|
| id                    | interne ID des Auftrags |
| ext\_id               | externe ID des Auftrags |

| **Filter-Attribut** | **Beschreibung**                            |
|---------------------|---------------------------------------------|
| adresse\_id         | interne ID der Adresse                      |
| adresse\_oid        | Objekt-ID der Adresse                       |
| planung\_id         | interne ID der Planung                      |
| planung\_nr         | Nr der Planung                              |
| offset              | Zeige ab dem n-ten Eintrag                  |
| limit               | Zeige die n-ersten Einträge (default: 1000) |

Zur eigenen Sicherheit kann man mehrere Aufträge nur löschen, wenn
mindestens ein Filter-Attribut vorhanden ist.

Beispiel-JSON für einen GET-/Delete-Request:  

    {
      "adresse_oid": "0007" 
    }

Beispiel-Rückgabe für den obigen GET-Request:  

    {
      "status": 200,
      "count": 1,
      "auftraege": [
        {
          "id": 1967,
          "ext_id": "1209e8e98fuweq9f8dh",
          "name": "Herr Mohn",
          "kg": 2.0,
          "adresse_id": 113726,
          "adresse_oid": "0007",
          "planung_id": 49,
          "planung_nr": "Montag",
          "timewindows": "[08:00,12:00];[14:00,18:00]",
          "servicetime": 0,
          "servicetime_per_job": true,
          "servicetime_per_unit": true,
          "servicetime_per_indi": true
        }
      ]
    }

### HHMMD-Format für Multi-Zeitfenster

Das HHMMD-Format ist eine intern verwendete String-Formatierung zur
Serialisierung von Multi-Zeitfenstern.  
Die Intention hinter dem Format war, dass sich die Zeitfenster nicht mit
einem Datum auf absolut fixierte Zeitpunkte beziehen (so etwas wie
"03-05-2020:08:00:00"),  
sondern einen relativen Bezug besitzen zum Starttag, an dem die Tour
beginnen soll.

Die Angabe eines Zeitfensters erfolgt in zweiteiligen Tupel -
umschlossen in eckigen Klammern.  

    [Startzeitpunkt,Endzeitpunkt]

  
Jeder Zeitpunkt wird dann mit der gewünschten Uhrzeit befüllt im
24h-Format.  

    [08:00,12:00] 

  
Mehrere Zeitfenster-Tupel werden anhand Semikolons von einander
getrennt.  

    [08:00,12:00];[14:00,18:30]

  
Die Zeitfenster ohne Angaben zum Tag beziehen sich auf den Tag 0.  
Möchte man zB. ein weiteres Zeitfenster am nächsten Tag hinzufügen,
ergänzt man zur Uhrzeit den Tag als Suffix.  

    [08:00(+1),12:00(+1)]

  
Auch Datumsüberhänge sind realisierbar in einem Zeitfenster  

    [22:00,05:00(+1)]

  
Im HHMMD-Format gibt es keine Escape-Sequenzen und keine
Schleifen-Konventionen.  
Man muss deshalb wiederholende Zeitfenster ausschreiben, die über
mehrere Tage identisch sind.  
Das technische Limit der relativen Zeitspanne liegt im Moment bei 39
Tagen.  
Man kann mit dem Service somit theoretisch 5-Wochen-Planungen
modellieren und berechnen lassen.

Aufträge, bei denen ein Zeitfenster nicht berücksichtigt werden soll,
erhalten ein leeres Tupel.  

    []

### Servicezeit-Berechnung

MultiRoute Tour! versucht es den Nutzern zu ermöglichen, die Servicezeit
eines Auftrages so präzise wie möglich zu modellieren.  
Die Bereitstellung von 6 Variablen (2 pro Planung und 4 pro Auftrag)
sollten dafür die meisten Fälle abdecken.  
Die Servicezeit für einen Auftrag errechnet sich durch folgende
Formel:  

    x = servicetime_per_job + servicetime_per_indi + (servicetime_per_unit * auftrag_capacity)

  
Die 'servicetime\_per\_job' ist ein konstanter Zeitwert aus der Planung,
der allen Aufträgen der Planung angerechnet wird.  
Die 'servicetime\_per\_indi' ist ein individueller Zeitwert
'servicetime' vom Auftrag, der auch nur dem spezifischen Auftrag
angerechnet wird.  
Die 'servicetime\_per\_unit' ist ein Faktor aus der Planung, der mit der
Kapazität des Auftrages multipliziert wird, und somit für einen
variablen Zeitwert zur Modellierung bietet.

Alle Summanden aus der Formel lassen sich außerdem für jeden Auftrag
abschalten - individuell anhand der gleichnamigen, boolschen Variablen.

## 3 Flotten

Flotten werden im Tour! Modul für die Berechnung von Touren verwendet,
um möglichst präzise die Arbeitsbedingungen der Fahrer repräsentieren zu
können.  
Der Zugriff auf das Flotten-Modell erfolgt über eine REST-Schnittstelle.

### JSON-Repräsentation

Die JSON-Repräsentation einer Flotte besitzt einen Namen
(keyword:"name") und ein Array von Fahrzeugen (keyword:"vehicles").

| **Fahrzeug-Attribut** | **Beschreibung**                              | **Plichtfeld/optional** | **default-Wert** |
|-----------------------|-----------------------------------------------|-------------------------|------------------|
| name                  | Bezeichnung des Fahrzeugtyps                  | Plichtfeld              | \-               |
| number                | Fahrzeugnummer                                | Pflichtfeld             | \-               |
| amount                | Anzahl der Fahrzeuge                          | optional                | 1                |
| start                 | JSON-Objekt der Start-Adresse                 | Pflichtfeld             | \-               |
| end                   | JSON-Objekt der End-Adresse                   | Pflichtfeld             | \-               |
| capacity              | Fahrzeugkapazität                             | optional                | 100              |
| driving               | Zeitlicher Rahmen für die Tour (HHMMD-Format) | Pflichtfeld             | \-               |
| break                 | JSON-Object der Pause                         | optional                | {}               |
| skills                | Schlüsselfertigkeiten des Fahrzeugs/Fahrers   | optional                | \[\]             |

Die JSON-Objekte der Start- und Endadressen besitzen einen Typus
(keyword:"type"). Bei der Startadresse kann der Typus folgende Werte besitzen: 

- "depot", wenn das Fahrzeug vom Depot aus startet, welche in der
Planung definiert ist.  
- "start", wenn das Fahrzeug von einer anderen Adresse starten soll.  
Bei der Endadresse kann der Typus folgende Werte besitzen.  
- "depot", wenn das Fahrzeug zum Depot zurückkehren soll, welches in der
Planung definiert ist.  
- "round", wenn das Fahrzeug zur Startadresse zurückkehren soll.  
- "open", wenn die Tour für das Fahrzeug beim letzten Auftrag enden
soll.  
- "end", wenn das Fahrzeug zu einer Zieladresse fahren soll.  
Für Typus "start" und "end" muss zusätzlich noch die Objekt-ID der
Adresse mit angegeben werden (keyword:"oid").

Beispiel:  

    "start": {
      "type": "start",
      "oid": "GBC1412031",
    },
    "end": {
      "type": "open" 
    }

Das JSON-Objekt der Pause benötigt neben dem Pausenzeitfenster
(keyword:"timewindows") im HHMMD-Format, eine Angabe zur Länge der Pause
(keyword:"duration") in ganzen Minuten.  
Beispiel:  

    "break": {
      "timewindows": "[08:00,12:00]",
      "duration": 30
    }

Das JSON-Schema, welches zur Validierung des Inputs verwendet wird,
finden Sie hier:  
<https://domain/fleet/schema>

### Parameter für POST- und PUT-Requests

Verwenden Sie POST-Requests zum anlegen von neuen Flotten:  
POST <http://domain/fernsteuerung/flotte>

POST-Requests können keine bestehenden Flotten überschreiben!  
Verwenden Sie stattdessen PUT-Requests, um Flotten zu bearbeiten:  
PUT <http://domain/fernsteuerung/flotte/flottenid>

Sowohl POST- als auch PUT-Request benötigen immer eine vollständige
JSON-Repräsentation der Flotte (keyword:"fleet"). Es kann nur eine
Flotte pro Request hinzugefügt bzw. bearbeitet werden.

Request:  

    {
      "fleet": {
        "name": "Standardflotte",
        "vehicles": [
          {
            "name": "Fahrzeug",
            "number": 1,
            "amount": 1,
            "start": {
              "type": "depot" 
            },
            "end": {
              "type": "depot" 
            },
            "capacity": 5000,
            "driving": "[09:00,13:00]",
            "break": {
              "timewindows": "[11:00,12:00]",
              "duration": 30
            },
            "skills": [
              "blau" 
            ]
          }
        ]
      }
    }

Response:  

    {
      "status": 200,
      "fleet_id": 20
    }

Man beachte, dass die ID der Flotte sich ändert nach einem PUT-Request,
wenn bereits berechnete Touren Referenzen besitzen auf die zu
überschreibende Flotte. Dadurch wird die bestehende Flotte versteckt
(hidden=&gt;true) und stattdessen eine neue Flotte angelegt.

### Parameter für GET-Request

Verwenden Sie den GET-Request, um eine Liste der zur Verfügung stehenden
Flotten zu erhalten:  
GET <http://domain/fernsteuerung/flotte>

| **Filter-Attribut** | **Beschreibung**                            |
|---------------------|---------------------------------------------|
| show\_hidden        | Zeige auch unsichtbare Flotten              |
| offset              | Zeige ab dem n-ten Eintrag                  |
| limit               | Zeige die n-ersten Einträge (default: 1000) |

Als Ergebnis erhalten Sie ein "fleets" Array zurück.

Response:  

    {
      "status": 200,
      "count": 2,
      "fleets": [
        {
          "id": 4,
          "name": "Peters Flotte",
          "immutable": false,
          "hidden": false,
          "vehicle_count": 8,
          "vehicle_types": 1,
          "capacity": 80000,
          "skills": [],
          "timewindows": "[08:00,12:00];[14:00,18:00]" 
        },
        {
          "id": 12,
          "name": "Lolik & Bolik",
          "immutable": true,
          "hidden": false,
          "vehicle_count": 2,
          "vehicle_types": 2,
          "capacity": 35000,
          "skills": ["weiss","blau"],
          "timewindows": "[08:00,12:00]" 
        }
      ]
    }

| **Ausgabe-Attribut** | **Beschreibung**                                               |
|----------------------|----------------------------------------------------------------|
| id                   | ID der Flotten-Instanz                                         |
| name                 | Bezeichnung der Flotte                                         |
| immutable            | Zustand, ob die Flotte bearbeitet werden kann                  |
| hidden               | Zustand, ob die Flotte in der GUI angezeigt wird               |
| vehicle\_count       | Anzahl der Fahrzeuge                                           |
| vehicle\_type        | Anzahl der verschiedenen Fahrzeugtypen                         |
| capacity             | Logistische Gesamtkapazität der Flotte in (Gramm/Stück/Person) |
| skill                | Liste der Skills, die in der Flotte existieren                 |
| timewindows          | Kombiniertes Zeitfenster von allen Fahrzeugen                  |

Durch das Hinzufügen der Flotten-ID erhalten Sie die vollständige
JSON-Repräsentation der Flotten-Instanz.  
GET <http://domain/fernsteuerung/flotte/flottenid>

Response:  

    {
      "status": 200,
      "fleet": {
        "name": "Lolik & Bolik",
        "vehicles": [
          {
            "name": "Bolik",
            "number": 2,
            "amount": 1,
            "start": {
              "type": "depot" 
            },
            "end": {
              "type": "open" 
            },
            "capacity": 30000,
            "driving": "[08:00,12:00]",
            "break": {
              "timewindows": "[09:00,11:00]",
              "duration": 60
            },
            "skills": ["weiss"]
          },
          {
            "name": "Lolik",
            "number": 1,
            "amount": 1,
            "start": {
              "type": "depot" 
            },
            "end": {
              "type": "depot" 
            },
            "capacity": 5000,
            "driving": "[08:00,12:00]",
            "break": {
              "timewindows": "[08:00,12:00]",
              "duration": 30
            },
            "skills": ["blau"]
          }
        ]
      }
    }

### Parameter für DELETE-Request

Verwenden Sie DELETE-Requests, um Flotten-Instanzen zu löschen.  
DELETE <http://domain/fernsteuerung/flotte/flottenid>

Flotten können nur einzeln gelöscht werden.
Wenn eine Flotte den 'immutable'-Zustand besitzt, dann wird diese nicht gelöscht,
sondern nur versteckt ('hidden' => true),
weil berechnete Touren noch Referenzen auf die 'immutable' Flotten besitzen.
Wenn sowohl Flotte als auch die Touren nicht mehr gebraucht werden,
dann kann man mit dem Parameter {"cascade" = true} alles entfernen.

Response:  

    {
      "status": 200
    }

## 4 Touren

### Touren-Status

Informationen zu allen Touren (einer Ausgabe)  
Es werden entweder alle angezeigt, oder nur die mit dem jeweiligen
Status.

<http://domain/fernsteuerung/touren>  
<http://domain/fernsteuerung/touren/error>  
<http://domain/fernsteuerung/touren/pending>  
<http://domain/fernsteuerung/touren/unknown>  
<http://domain/fernsteuerung/touren/success>

Optionale Parameter:

|         |                          |
|---------|--------------------------|
| limit   | (default 100)            |
| offset  | (default 0)              |
| ausgabe | (default die vom User)   |
| planung | (Planungs-Nummer (Name)) |

<http://domain/fernsteuerung/touren?limit=10&offset=0>

Rückgabewert ist ein JSON Array:  

    [
    {"id":88,"planung":"tour_test","status":"success"},
    {"id":87,"planung":"tour_test","status":"success"},
    {"id":86,"planung":"tour_test","status":"error"},
    {"id":85,"planung":"tour_test","status":"error"},
    {"id":84,"planung":"tour_test","status":"success"},
    {"id":83,"planung":"tour_test","status":"success"},
    {"id":82,"planung":"tour_test","status":"success"},
    {"id":81,"planung":"tour_test","status":"success"},
    {"id":80,"planung":"tour_test","status":"success"},
    {"id":79,"planung":"tour_test","status":"success"}
    ]

<http://domain/fernsteuerung/tour/tour-id>

Rückgabewert ist ein JSON Object:

|                  |                                           |
|------------------|-------------------------------------------|
| touren           | Touren Array                              |
| meta             | Meta Objekt (Information für alle Touren) |
| depot            | Depot Objekt                              |
| unassigned\_jobs | Keiner Tour zugeordneten Aufträge         |
| flotte           | Flotte Objekt (Gegebene Fahrzeugflotte)   |
| diff\_flotte     | Flotte Objekt (Überzählige Fahrzeuge)     |

Einzelne Fahrzeugstrecken Array Objekt:

|               |           |
|---------------|-----------|
| vehicle\_name | Fahrzeug  |
| vehicle\_id   |           |
| start\_time   | Startzeit |
| finish\_time  | Endzeit   |
| open\_end     |           |
| destination   |           |

|                         |                                     |
|-------------------------|-------------------------------------|
| fahrzeugstrecke\_id     | Id der Fahrzeugstrecke              |
| nr                      | Nummer der Fahrzeugstrecke          |
| index                   | Index der Fahrzeugstrecke           |
| strecke                 | Entfernung in Meter                 |
| dauer                   | Fahrzeit in Sekunden                |
| entladedauer            | Entladedauer                        |
| gesamtdauer             | Entladedauer + Fahrzeit in Sekunden |
| wartezeit               | Wartezeit                           |
| gewicht                 | Wert Kapazität                      |
| gewicht\_text           |                                     |
| fahrzeug\_gewicht       | Wert Kapazität Fahrzeug             |
| fahrzeug\_gewicht\_text |                                     |
| abladestellen           | Abladestellen Array                 |
| rueckweg\_zum\_depot    | Rückweg zum Depot                   |
| google\_maps\_url       | Navigationsformat Google Maps       |
| apple\_maps\_url        | Navigationsformat Apple Maps        |

Einzelne Fahrzeugstrecken Array Objekt:

|                         |                                     |
|-------------------------|-------------------------------------|
|sort | Laufende Nummer |
|oi | Gebäude id |
|plz | Postleitzahl |
|ort | Ort |
|ort_zusatz | Ortsteil |
|strasse | Strasse |
|hausnummer | Hausnummer |
|hausnummer_zusatz | Hausnummer Zusatz |
|gewicht | Kapazität (kg, Stück, Personen) integer |
|gewicht_text | Einheit Kapazität (kg, Stück, Personen(bzw. Person) |
|strecke | Entfernung in Meter |
|dauer | Fahrzeit in Sekunden |
|name | Bezeichnung |
|description | Notizen |
|timewindows | Zeitfenster |
|arrival_time | Ankunftszeit |
|action_time | Aktionstart |
|departure_time | Abfahrtszeit |
|service_sum | Servicezeit |
|service_base | Servicezeit Basiswert |
|service_unit | Servicezeit Kapazitätsprodukt |
|service_indi | Servicezeit Individueller Wert |
|tour_break | Pause (true/false) |
|destination | Endpunkt (true/false) |

Rückweg Objekt:

|         |                      |
|---------|----------------------|
| strecke | Entfernung in Meter  |
| dauer   | Fahrzeit in Sekunden |

Meta Objekt:

|                        |                                                             |
|------------------------|-------------------------------------------------------------|
| id                     | Id der Tour                                                 |
| datenstand\_osm        | Osm Datenstand                                              |
| success                | Erfolgreich (true, null, false)                             |
| anz\_fahrzeuge         | Anzahl Fahrzeugstrecken                                     |
| abladestellen          | Zugewiesene Aufträge                                        |
| unassigned\_jobs       | Nicht zugewiesene Aufträge                                  |
| error\_message         | Fehlermeldung (default null)                                |
| horizont               | Maximale Tourdauer (Stunden)                                |
| deploy\_time           | Entladedauer pro Einheit (Sekunden)                         |
| flat\_deploy\_time     | Entladezeit pro Auftrag (Sekunden)                          |
| max\_deliver\_time     | Maximale Tourdauer vom Depot bis letzter Kunde/Abladestelle |
| planung                | Nummer des Planung                                          |
| fleet fleet            | Name der Flotte                                             |
| fleet\_id fleet        | Id der Flotte                                               |
| zeit\_distanz          | Optimiert nach Zeit oder Distanz (Zeit oder Distanz)        |
| gewicht                | Wert Kapazität                                              |
| gewicht\_text          | Einheit Kapazität (kg, Stück, Personen(bzw. Person)         |
| strecke                | Entfernung in Meter                                         |
| dauer                  | Fahrzeit in Sekunden                                        |
| entladedauer           | Entladedauer                                                |
| gesamtdauer            | Entladedauer + Fahrzeit in Sekunden                         |
| berechnet\_am          | Berechnet am                                                |
| depot\_departure\_time | Erster Abfahrtszeitpunkt                                    |

Depot Objekt:

|                    |                   |
|--------------------|-------------------|
| oi                 | Gebäude id        |
| plz                | Postleitzahl      |
| ort                | Ort               |
| ort\_zusatz        | Ortsteil          |
| strasse            | Strasse           |
| hausnummer         | Hausnummer        |
| hausnummer\_zusatz | Hausnummer Zusatz |

Keiner Tour zugeordneten Aufträge Array Objekt:

|                         |                                     |
|-------------------------|-------------------------------------|
|nr | Laufende Nummer |
|oi | Gebäude id |
|plz | Postleitzahl |
|ort | Ort |
|ort_zusatz | Ortsteil |
|strasse | Strasse |
|hausnummer | Hausnummer |
|hausnummer_zusatz | Hausnummer Zusatz |
|name | Bezeichnung |
|description | Notizen |
|timewindows | Zeitfenster |
|service_sum | Servicezeit |
|service_base | Servicezeit Basiswert |
|service_unit | Servicezeit Kapazitätsprodukt |
|service_indi | Servicezeit Individueller Wert |

Flotte Objekt:

|               |                                                     |
|---------------|-----------------------------------------------------|
| anzahl        | Anzahl Fahrzeuge                                    |
| name          | Name                                                |
| start\_time   | Startzeit                                           |
| end\_time     | Endzeit                                             |
| gewicht       | Wert Kapazität                                      |
| gewicht\_text | Einheit Kapazität (kg, Stück, Personen(bzw. Person) |

Bsp:  

    {
        "touren": [{
            "vehicle_name": "Fahrzeugtyp 1",
            "vehicle_id": 2,
            "start_time": "08:00",
            "finish_time": "09:57",
            "open_end": false,
            "destination": false,
            "fahrzeugstrecke_id": 34,
            "nr": 1,
            "index": 0,
            "strecke": 97654,
            "dauer": 6522,
            "wartezeit": 0,
            "entladedauer": 530.0,
            "gesamtdauer": 7052.0,
            "gewicht": 100.0,
            "gewicht_text": "kg",
            "fahrzeug_gewicht": 100.0,
            "fahrzeug_gewicht_text": "kg",
            "abladestellen": [{
                "sort": 1,
                "oi": "25040886",
                "plz": "35630",
                "ort": "Ehringshausen",
                "strasse": "Bahnhofstraße",
                "hausnummer": "16",
                "hausnummer_zusatz": "",
                "notice": null,
                "street_oi": null,
                "gewicht": 10.0,
                "gewicht_text": "kg",
                "strecke": 326,
                "dauer": 34,
                "name": "N16",
                "description": "POST",
                "timewindows": "ohne",
                "arrival_time": "08:00",
                "action_time": "08:00",
                "departure_time": "08:01",
                "service_sum": "0h 0' 53\"",
                "service_base": "0h 0' 4\"",
                "service_unit": "0h 0' 49\"",
                "service_indi": "0h 0' 0\"",
                "tour_break": false,
                "destination": false
            }, {
                "sort": 2,
                "oi": "20078306",
                "plz": "35614",
                "ort": "Aßlar",
                "strasse": "Berliner Straße",
                "hausnummer": "8",
                "hausnummer_zusatz": "",
                "notice": null,
                "street_oi": null,
                "gewicht": 10.0,
                "gewicht_text": "kg",
                "strecke": 7109,
                "dauer": 539,
                "name": "N15",
                "description": "POST",
                "timewindows": "ohne",
                "arrival_time": "08:10",
                "action_time": "08:10",
                "departure_time": "08:11",
                "service_sum": "0h 0' 53\"",
                "service_base": "0h 0' 4\"",
                "service_unit": "0h 0' 49\"",
                "service_indi": "0h 0' 0\"",
                "tour_break": false,
                "destination": false
            }, {
                "sort": 3,
                "oi": "19321189",
                "plz": "35578",
                "ort": "Wetzlar",
                "strasse": "Elsa-Brandström-Straße",
                "hausnummer": "18",
                "hausnummer_zusatz": "",
                "notice": null,
                "street_oi": null,
                "gewicht": 10.0,
                "gewicht_text": "kg",
                "strecke": 8879,
                "dauer": 761,
                "name": "N14",
                "description": "POST",
                "timewindows": "ohne",
                "arrival_time": "08:24",
                "action_time": "08:24",
                "departure_time": "08:24",
                "service_sum": "0h 0' 53\"",
                "service_base": "0h 0' 4\"",
                "service_unit": "0h 0' 49\"",
                "service_indi": "0h 0' 0\"",
                "tour_break": false,
                "destination": false
            }, {
                "sort": 4,
                "oi": "27336905",
                "plz": "35075",
                "ort": "Gladenbach",
                "strasse": "Bahnhofstraße",
                "hausnummer": "10",
                "hausnummer_zusatz": "",
                "notice": null,
                "street_oi": null,
                "gewicht": 10.0,
                "gewicht_text": "kg",
                "strecke": 41020,
                "dauer": 2320,
                "name": "N13",
                "description": "POST",
                "timewindows": "ohne",
                "arrival_time": "09:03",
                "action_time": "09:03",
                "departure_time": "09:04",
                "service_sum": "0h 0' 53\"",
                "service_base": "0h 0' 4\"",
                "service_unit": "0h 0' 49\"",
                "service_indi": "0h 0' 0\"",
                "tour_break": false,
                "destination": false
            }, {
                "sort": 5,
                "oi": "GBC2409542",
                "plz": "35075",
                "ort": "Gladenbach",
                "strasse": "Marktplatz",
                "hausnummer": "5",
                "hausnummer_zusatz": "BK",
                "notice": null,
                "street_oi": null,
                "gewicht": 10.0,
                "gewicht_text": "kg",
                "strecke": 313,
                "dauer": 41,
                "name": "N12",
                "description": "POST",
                "timewindows": "ohne",
                "arrival_time": "09:05",
                "action_time": "09:05",
                "departure_time": "09:06",
                "service_sum": "0h 0' 53\"",
                "service_base": "0h 0' 4\"",
                "service_unit": "0h 0' 49\"",
                "service_indi": "0h 0' 0\"",
                "tour_break": false,
                "destination": false
            }, {
                "sort": 6,
                "oi": "22536131",
                "plz": "35080",
                "ort": "Bad Endbach",
                "strasse": "Am Briel",
                "hausnummer": "3",
                "hausnummer_zusatz": "",
                "notice": null,
                "street_oi": null,
                "gewicht": 10.0,
                "gewicht_text": "kg",
                "strecke": 7430,
                "dauer": 552,
                "name": "N11",
                "description": "POST",
                "timewindows": "ohne",
                "arrival_time": "09:15",
                "action_time": "09:15",
                "departure_time": "09:16",
                "service_sum": "0h 0' 53\"",
                "service_base": "0h 0' 4\"",
                "service_unit": "0h 0' 49\"",
                "service_indi": "0h 0' 0\"",
                "tour_break": false,
                "destination": false
            }, {
                "sort": 7,
                "oi": "10061877",
                "plz": "35080",
                "ort": "Bad Endbach",
                "strasse": "Schlierbacher Straße",
                "hausnummer": "33",
                "hausnummer_zusatz": "",
                "notice": null,
                "street_oi": null,
                "gewicht": 10.0,
                "gewicht_text": "kg",
                "strecke": 3885,
                "dauer": 325,
                "name": "N10",
                "description": "POST",
                "timewindows": "ohne",
                "arrival_time": "09:21",
                "action_time": "09:21",
                "departure_time": "09:22",
                "service_sum": "0h 0' 53\"",
                "service_base": "0h 0' 4\"",
                "service_unit": "0h 0' 49\"",
                "service_indi": "0h 0' 0\"",
                "tour_break": false,
                "destination": false
            }, {
                "sort": 8,
                "oi": "19151841",
                "plz": "35756",
                "ort": "Mittenaar",
                "strasse": "Aarstraße",
                "hausnummer": "6",
                "hausnummer_zusatz": "",
                "notice": null,
                "street_oi": null,
                "gewicht": 10.0,
                "gewicht_text": "kg",
                "strecke": 11998,
                "dauer": 824,
                "name": "N9",
                "description": "POST",
                "timewindows": "ohne",
                "arrival_time": "09:36",
                "action_time": "09:36",
                "departure_time": "09:37",
                "service_sum": "0h 0' 53\"",
                "service_base": "0h 0' 4\"",
                "service_unit": "0h 0' 49\"",
                "service_indi": "0h 0' 0\"",
                "tour_break": false,
                "destination": false
            }, {
                "sort": 9,
                "oi": "24621170",
                "plz": "35630",
                "ort": "Ehringshausen",
                "strasse": "Stegwiese",
                "hausnummer": "27",
                "hausnummer_zusatz": "",
                "notice": null,
                "street_oi": null,
                "gewicht": 10.0,
                "gewicht_text": "kg",
                "strecke": 16176,
                "dauer": 1056,
                "name": "N8",
                "description": "POST",
                "timewindows": "ohne",
                "arrival_time": "09:54",
                "action_time": "09:54",
                "departure_time": "09:55",
                "service_sum": "0h 0' 53\"",
                "service_base": "0h 0' 4\"",
                "service_unit": "0h 0' 49\"",
                "service_indi": "0h 0' 0\"",
                "tour_break": false,
                "destination": false
            }, {
                "sort": 10,
                "oi": "24621170",
                "plz": "35630",
                "ort": "Ehringshausen",
                "strasse": "Stegwiese",
                "hausnummer": "27",
                "hausnummer_zusatz": "",
                "notice": null,
                "street_oi": null,
                "gewicht": 10.0,
                "gewicht_text": "kg",
                "strecke": 0,
                "dauer": 0,
                "name": "N7",
                "description": "POST",
                "timewindows": "ohne",
                "arrival_time": "09:55",
                "action_time": "09:55",
                "departure_time": "09:56",
                "service_sum": "0h 0' 53\"",
                "service_base": "0h 0' 4\"",
                "service_unit": "0h 0' 49\"",
                "service_indi": "0h 0' 0\"",
                "tour_break": false,
                "destination": false
            }],
            "rueckweg_zum_depot": {
                "strecke": 518,
                "dauer": 70
            },
            "token": "E4F910BE37BF010ACxxx46A57613E35C261354EFB0DEB6BBDA04",
            "google_maps_url": "http://localhost:3000/google_maps?token=E4F910BE37BF0xxxD818508178BE0F340BFC571D839446A57613E35C261354EFB0DEB6BBDA04",
            "apple_maps_url": "http://localhost:3000/apple_maps?token=E4F910BE37BF010xx575D818508178BE0F340BFC571D839446A57613E35C261354EFB0DEB6BBDA04" 
        }, {
            "vehicle_name": "Fahrzeugtyp 1",
            "vehicle_id": 2,
            "start_time": "08:00",
            "finish_time": "09:21",
            "open_end": false,
            "destination": false,
            "fahrzeugstrecke_id": 33,
            "nr": 2,
            "index": 1,
            "strecke": 72561,
            "dauer": 4633,
            "wartezeit": 0,
            "entladedauer": 269.0049,
            "gesamtdauer": 4902.0049,
            "gewicht": 50.001,
            "gewicht_text": "kg",
            "fahrzeug_gewicht": 100.0,
            "fahrzeug_gewicht_text": "kg",
            "abladestellen": [{
                "sort": 1,
                "oi": "17806131",
                "plz": "35745",
                "ort": "Herborn",
                "strasse": "Austraße",
                "hausnummer": "63",
                "hausnummer_zusatz": "",
                "notice": null,
                "street_oi": null,
                "gewicht": 10.0,
                "gewicht_text": "kg",
                "strecke": 12279,
                "dauer": 812,
                "name": "N6",
                "description": "POST",
                "timewindows": "ohne",
                "arrival_time": "08:13",
                "action_time": "08:13",
                "departure_time": "08:14",
                "service_sum": "0h 0' 53\"",
                "service_base": "0h 0' 4\"",
                "service_unit": "0h 0' 49\"",
                "service_indi": "0h 0' 0\"",
                "tour_break": false,
                "destination": false
            }, {
                "sort": 2,
                "oi": "13933646",
                "plz": "35745",
                "ort": "Herborn",
                "strasse": "Hauptstraße",
                "hausnummer": "90",
                "hausnummer_zusatz": "",
                "notice": null,
                "street_oi": null,
                "gewicht": 10.0,
                "gewicht_text": "kg",
                "strecke": 1129,
                "dauer": 133,
                "name": "N5",
                "description": "POST",
                "timewindows": "ohne",
                "arrival_time": "08:16",
                "action_time": "08:16",
                "departure_time": "08:17",
                "service_sum": "0h 0' 53\"",
                "service_base": "0h 0' 4\"",
                "service_unit": "0h 0' 49\"",
                "service_indi": "0h 0' 0\"",
                "tour_break": false,
                "destination": false
            }, {
                "sort": 3,
                "oi": "21171259",
                "plz": "35683",
                "ort": "Dillenburg",
                "strasse": "Am Forstdenkmal",
                "hausnummer": "7",
                "hausnummer_zusatz": "",
                "notice": null,
                "street_oi": null,
                "gewicht": 10.0,
                "gewicht_text": "kg",
                "strecke": 8184,
                "dauer": 538,
                "name": "N4",
                "description": "POST",
                "timewindows": "ohne",
                "arrival_time": "08:26",
                "action_time": "08:26",
                "departure_time": "08:27",
                "service_sum": "0h 0' 53\"",
                "service_base": "0h 0' 4\"",
                "service_unit": "0h 0' 49\"",
                "service_indi": "0h 0' 0\"",
                "tour_break": false,
                "destination": false
            }, {
                "sort": 4,
                "oi": "22435649",
                "plz": "35685",
                "ort": "Dillenburg",
                "strasse": "Am Nebelsberg",
                "hausnummer": "11",
                "hausnummer_zusatz": "",
                "notice": null,
                "street_oi": null,
                "gewicht": 10.0,
                "gewicht_text": "kg",
                "strecke": 4611,
                "dauer": 439,
                "name": "N3",
                "description": "POST",
                "timewindows": "ohne",
                "arrival_time": "08:34",
                "action_time": "08:34",
                "departure_time": "08:35",
                "service_sum": "0h 0' 53\"",
                "service_base": "0h 0' 4\"",
                "service_unit": "0h 0' 49\"",
                "service_indi": "0h 0' 0\"",
                "tour_break": false,
                "destination": false
            }, {
                "sort": 5,
                "oi": "22264516",
                "plz": "35683",
                "ort": "Dillenburg",
                "strasse": "Nassaustraße",
                "hausnummer": "19",
                "hausnummer_zusatz": "",
                "notice": null,
                "street_oi": null,
                "gewicht": 0.001,
                "gewicht_text": "kg",
                "strecke": 2244,
                "dauer": 225,
                "name": "N2",
                "description": "",
                "timewindows": "ohne",
                "arrival_time": "08:39",
                "action_time": "08:39",
                "departure_time": "08:39",
                "service_sum": "0h 0' 4\"",
                "service_base": "0h 0' 4\"",
                "service_unit": "0h 0' 0\"",
                "service_indi": "0h 0' 0\"",
                "tour_break": false,
                "destination": false
            }, {
                "sort": 6,
                "oi": "25800112",
                "plz": "35759",
                "ort": "Driedorf",
                "strasse": "Wilhelmstraße",
                "hausnummer": "51",
                "hausnummer_zusatz": "",
                "notice": null,
                "street_oi": null,
                "gewicht": 10.0,
                "gewicht_text": "kg",
                "strecke": 23391,
                "dauer": 1213,
                "name": "N1",
                "description": "POST",
                "timewindows": "ohne",
                "arrival_time": "08:59",
                "action_time": "08:59",
                "departure_time": "09:00",
                "service_sum": "0h 0' 53\"",
                "service_base": "0h 0' 4\"",
                "service_unit": "0h 0' 49\"",
                "service_indi": "0h 0' 0\"",
                "tour_break": false,
                "destination": false
            }],
            "rueckweg_zum_depot": {
                "strecke": 20723,
                "dauer": 1273
            },
            "token": "E4F910BE37BF010AC5CD26Cxxx5D14C0F370657C97B1C7",
            "google_maps_url": "http://localhost:3000/google_maps?token=E4F910xxx70657C97B1C7",
            "apple_maps_url": "http://localhost:3000/apple_maps?token=E4F910BExxxF370657C97B1C7" 
        }],
        "meta": {
            "id": 19,
            "datenstand_osm": "04.05.2020",
            "success": true,
            "anz_fahrzeuge": 2,
            "abladestellen": 16,
            "error_message": null,
            "horizont": null,
            "deploy_time": 4.9,
            "flat_deploy_time": "4",
            "max_deliver_time": null,
            "unassigned_jobs": "0",
            "planung": "P1",
            "fleet": "_Neue_Flotte_",
            "fleet_id": 1,
            "zeit_distanz": "Zeit",
            "gewicht": 150.0,
            "gewicht_text": "kg",
            "strecke": 170215.0,
            "dauer": 11155.0,
            "entladedauer": 735.0,
            "gesamtdauer": 11890.0,
            "berechnet_am": "10.08.2020 11:38",
            "depot_departure_time": "08:00" 
        },
        "depot": {
            "oi": "18144667",
            "plz": "35630",
            "ort": "Ehringshausen",
            "strasse": "Wetzlarer Straße",
            "hausnummer": "1",
            "hausnummer_zusatz": "",
            "notice": null,
            "street_oi": null,
            "departure_time": "08:00" 
        },
        "flotte": [{
            "anzahl": 2,
            "gewicht": 100.0,
            "gewicht_text": "kg",
            "name": "Fahrzeugtyp 1",
            "number": 1,
            "timewindow": "[08:00,12:00]",
            "start_time": "08:00",
            "end_time": "12:00" 
        }],
        "diff_flotte": [{
            "anzahl": 18,
            "gewicht": 100.0,
            "gewicht_text": "kg",
            "name": "Fahrzeugtyp 1",
            "number": 1,
            "timewindow": "[08:00,12:00]",
            "start_time": "08:00",
            "end_time": "12:00" 
        }]
    }

### Tour entfernen

Verwenden Sie DELETE-Requests, um Touren zu entfernen.  
DELETE <http://domain/fernsteuerung/tour/tour-id>

Touren können nur einzeln gelöscht werden.

Response:

    {
       status: '200', 
       tour_id: XY, 
       error: "Tour Nr. XY wurde erfolgreich entfernt." 
    }

### Touren berechnen

<http://domain/fernsteuerung/tour/berechnen>

Parameter:

|             |                                      |
|-------------|--------------------------------------|
| planung     | Nummer des Planung                   |
| fleet\_name | Name der gespeicherten Flotte (oder) |
| fleet\_id   | Id der gespeicherten Flotte          |
| tour        | Tour-Parameter                       |
| ausgabe     | optional (default die vom User)      |

Tour-Parameter:

|                               |                                              |
|-------------------------------|----------------------------------------------|
| zeit\_distanz                 | Fahrzeugroutingprofil                        |
| flat\_deploy\_time            | Entladezeit pro Auftrag (Sek.)               |
| deploy\_time                  | Entladezeit pro Einheit (Sek.)               |
| maximum\_jobs\_per\_vehicle   | Maximale Anzahl Aufträge pro Fahrzeugstrecke |
|ignore_capacity_constraints|(Bool) Kapazitäten für die Optimierung ignorieren.|
|ignore_skill_constraints|(Bool) Skills für die Optimierung ignorieren.|
|ignore_vehicle_number_constraints|(Bool) Fahrzeugzuweisungen für die Optimierung ignorieren.|
|tempo_modifier|Relativer Geschwindigkeits-Regler (default: 100) zur prozentualen Anpassung der Fahrzeuggeschwindigkeiten|


Gültige Fahrzeugroutingprofile für Tour-Parameter "zeit\_distanz".  
Falls ein Profil nicht unterstützt wird, werden die gültigen Profile im
Error-Response gelistet.

|          |                          |
|----------|--------------------------|
| zeit     | PKW (schnellste Strecke) |
| distanz  | PKW (kürzeste Strecke)   |
| hgv\_28  | LKW (2,8 Tonnen)         |
| hgv\_35  | LKW (3,5 Tonnen)         |
| hgv\_75  | LKW (7,5 Tonnen)         |
| hgv\_120 | LKW (12,0 Tonnen)        |

Bsp:

    {
      "planung": "tour_test",
      "fleet_name": "Test Flotte 1",
      "tour": {
        "zeit_distanz": "zeit",
        "flat_deploy_time": 5.0,
        "deploy_time": 0.1,
        "maximum_jobs_per_vehicle": 100,
        "ignore_capacity_constraints": false
      }
    }


## 5 Planung

### Planung-abrufen

<http://domain/fernsteuerung/planung/>

Parameter (optional):

|         |                                                           |
|---------|-----------------------------------------------------------|
| nr      | Nummer(n) der Planung                                     |
| limit   | Limit                                                     |
| offset  | Offset                                                    |
| ausgabe | Name der Ausgabe (default=Aktuelle Ausgabe des Benutzers) |

Rückgabe:

|          |                       |
|----------|-----------------------|
| nr       | Nummer(n) der Planung |
| name     | Name des              |
| depot    | oi depot              |
| kg       | Kapazität in kg       |
| stueck   | Kapazität in Stück    |
| personen | Kapazität in Personen |

**Kapazität abhängig von Kunden Einstellungen**

    [{
        "nr": "1200",
        "name": "",
        "depot": "3",
        "kg": 123.8
    }]

### Planung hinzufügen/updaten

<http://domain/fernsteuerung/planung/add_and_update>

Parameter:

|         |                                                                     |
|---------|---------------------------------------------------------------------|
| planung | Planung Parameter                                                   |
| insert  | true(default) oder false. Nur neue Planungen werden hinzugefügt     |
| update  | true(default) oder false. Bestehende Planungen werden geupdated     |
| ausgabe | Name der Ausgabe (optional: default=Aktuelle Ausgabe des Benutzers) |

Planung Parameter (Achtung: beim Einfügen von mehreren Planungen muss
immer die gleiche Anzahl der Parameter angegeben werden):

|       |                         |
|-------|-------------------------|
| nr    | Planungsnummer          |
| name  | Planungsname (optional) |
| depot | oi Depot (optional)     |

Beispiel:

    {
    "update": true,
    "insert": true, 
    "planung": [{
        "nr": "Planung 1",
        "name": "",
        "depot": "CS3" 
    }, {
        "nr": "Planung 2",
        "name": "",
        "depot": null
    }]
     }

### Planung löschen

<http://domain/fernsteuerung/planung/delete>

Parameter:

|         |                                                                     |
|---------|---------------------------------------------------------------------|
| nr      | Nummer der Planung/Nummern der Planungen                            |
| ausgabe | Name der Ausgabe (optional: default=Aktuelle Ausgabe des Benutzers) |
| cascade |	Optionale boolsche Flag, wenn alle dazugehörige Touren ebenfalls gelöscht werden sollen. |


    {
      nr: ["1","2"]
    }

### Planungsdefinition

<http://domain/fernsteuerung/planung/definition>

Parameter (optional):

|         |                                                           |
|---------|-----------------------------------------------------------|
| gebiet  | Nummer(n) der Gebiete                                     |
| limit   | Limit                                                     |
| offset  | Offset                                                    |
| ausgabe | Name der Ausgabe (default=Aktuelle Ausgabe des Benutzers) |

Rückgabe:

    [{"planung":"Planung 1","oi":["12760053311732","CS3","CS4","12760054446917"],"ausgabe":"Tour"}]

### Planungsdefinition hinzufügen/löschen

<http://domain/fernsteuerung/planung/add_definition>  
<http://domain/fernsteuerung/planung/delete_definition>

Parameter:

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>oi</td>
<td>Adresse ID</td>
</tr>
<tr class="even">
<td>planung</td>
<td>Nummer der Planung</td>
</tr>
<tr class="odd">
<td>ausgabe</td>
<td>Name der Ausgabe (optional default=Aktuelle Ausgabe des Benutzers)</td>
</tr>
<tr class="even">
<td>geom</td>
<td>Geometrien neu zeichnen (optional default=false); ACHTUNG: Bitte nur verwenden wenn die Geometrien vom System erzeugt wurden.</td>
</tr>
<tr class="odd">
<td>append</td>
<td>Modus beim Hinzufügen (optional default=true); Alle Änderungen werden nur innerhalb der Ausgabe angewandt.<br />
true: Zuordnung wird einfach hinzugefügt (Überlappungen mit anderen Planungen sind möglich)<br />
false: die gesamte alte Zuordnung des Gebietes wird als erstes gelöscht. Dann wird die neue Zuordnung geladen. (Überlappungen mit anderen Planungen sind möglich)<br />
replace: Alle Zuordnungen der Adressen werden gelöscht. Dann wird die neue Zuordnung geladen. (Überlappungen mit anderen Planungen sind nicht möglich)<br />
delete_replace: Die gesamte alte Zuordnung des Gebietes wird als erstes gelöscht. Alle Zuordnungen der Adressen zu anderen Planungen werden gelöscht. Dann wird die neue Zuordnung geladen. (Überlappungen mit anderen Planungen sind nicht möglich)</td>
</tr>
<tr class="even">
<td>all</td>
<td>Modus beim Löschen (optional default=false); Die Zuordnung wird gelöscht</td>
</tr>
</tbody>
</table>

    {
      "oi": ["12760053311732","CS3","CS4","12760054446917"],
      "planung": "11",
    }

Bekannte Fehlermeldungen:

    {"text":"Ausgabe nicht gefunden","status":500}
    {"text":"Keine Planung übergeben","status":500}
    {"text":"Keine Adresse übergeben","status":500}
    {"text":"Daten wurden nicht übernommen","status":500}

### Planungsdefinition hinzufügen mit Straßen-ID

<http://domain/fernsteuerung/planung/add_definition_with_street_oi>

Parameter:

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>adresse</td>
<td>Adresse Params</td>
</tr>
<tr class="even">
<td>planung</td>
<td>Nummer der Planung</td>
</tr>
<tr class="odd">
<td>ausgabe</td>
<td>Name der Ausgabe (optional default=Aktuelle Ausgabe des Benutzers)</td>
</tr>
<tr class="even">
<td>append</td>
<td>Modus beim Hinzufügen (optional default=true); Alle Änderungen werden nur innerhalb der Ausgabe angewandt.<br />
true: Zuordnung wird einfach hinzugefügt (Überlappungen mit anderen Planungen sind möglich)<br />
false: die gesamte alte Zuordnung des Gebietes wird als erstes gelöscht. Dann wird die neue Zuordnung geladen. (Überlappungen mit anderen Planungen sind möglich)<br />
replace: Alle Zuordnungen der Adressen werden gelöscht. Dann wird die neue Zuordnung geladen. (Überlappungen mit anderen Planungen sind nicht möglich)<br />
delete_replace: Die gesamte alte Zuordnung des Gebietes wird als erstes gelöscht. Alle Zuordnungen der Adressen zu anderen Planungen werden gelöscht. Dann wird die neue Zuordnung geladen. (Überlappungen mit anderen Planungen sind nicht möglich)</td>
</tr>
<tr class="odd">
<td>geom</td>
<td>Geometrien neu zeichnen (optional default=false); ACHTUNG: Bitte nur verwenden wenn die Geometrien vom System erzeugt wurden.</td>
</tr>
</tbody>
</table>

Adresse Params:

|            |                |
|------------|----------------|
| street\_oi | Straßen ID     |
| nr\_von    | von Hausnummer |
| nr\_bis    | Bis Hausnummer |

Optionale Adresse Params:

|               |                       |
|---------------|-----------------------|
| nrzusatz\_von | von Hausnummer Zusatz |
| nrzusatz\_bis | Bis Hausnummer Zusatz |

|       |                                                                                              |
|-------|----------------------------------------------------------------------------------------------|
| kennz | Kennzahl A: Alle, G:Nur gerade Hausnummern, U: Nur ungerade Hausnummern. optional(default A) |

    {
      "adresse": [{"street_oi":"1234", "nr_von": "2","nr_bis":"998","kennz":"G"},{"street_oi":"4567", "nr_von": "1","nr_bis":"999","kennz":"A"}],
      "planung": "Planung 1",
    }

    gegeben Hausnummer 20, 20A, 20B, 21, 21A, 21B, 22, 22A,22B

    {  "adresse": [{"street_oi": "x11", "nr_von": "20",  "nr_bis": "20" }]} => 20, 20A, 20B
    {  "adresse": [{"street_oi": "x11", "nr_von": "20",  "nr_bis": "22" }]} => 20, 20A, 20B, 21, 21A, 21B, 22, 22A,22B
    {  "adresse": [{"street_oi": "x11", "nr_von": "20",  "nr_bis": "20", "nrzusatz_von": "", "nrzusatz_bis": "" }]} => 20
    {  "adresse": [{"street_oi": "x11", "nr_von": "20",  "nr_bis": "20", "nrzusatz_von": "A", "nrzusatz_bis": "B" }]} => 20A, 20B
    {  "adresse": [{"street_oi": "x11", "nr_von": "20",  "nr_bis": "20", "nrzusatz_von": "", "nrzusatz_bis": "A" }]} => 20, 20A
    {  "adresse": [{"street_oi": "x11", "nr_von": "20",  "nr_bis": "20", "nrzusatz_bis": "" }]} => 20 (wenn nrzusatz_von leerer String ist kann man ihn auch weglassen.)
    {  "adresse": [{"street_oi": "x11", "nr_von": "20",  "nr_bis": "22", "nrzusatz_von": "B", "nrzusatz_bis": "" }]} => 20B, 21, 21A, 21B, 22
    {  "adresse": [{"street_oi": "x11", "nr_von": "20",  "nr_bis": "22", "nrzusatz_von": "B", "nrzusatz_bis": "A" }]} => 20B, 21, 21A, 21B, 22, 22A
    {  "adresse": [{"street_oi": "x11", "nr_von": "20",  "nr_bis": "22", "nrzusatz_von": "B" }]} => 20B, 21, 21A, 21B, 22, 22A,22B
    Reihenfolge wenn nr_von = nr_bis
    {  "adresse": [{"street_oi": "x11", "nr_von": "20",  "nr_bis": "20", "nrzusatz_von": "B", "nrzusatz_bis": "" }]} => x (keine Zuordnung)


### Planungsdaten kg/Stück/Personen abrufen

<http://domain/fernsteuerung/planung/data>

Parameter (optional):

|         |                                                           |
|---------|-----------------------------------------------------------|
| limit   | Limit                                                     |
| offset  | Offset                                                    |
| ausgabe | Name der Ausgabe (default=Aktuelle Ausgabe des Benutzers) |

Rückgabe:

|          |                       |
|----------|-----------------------|
| oi       | OI Gebäude            |
| kg       | Kapazität in kg       |
| stueck   | Kapazität in Stück    |
| personen | Kapazität in Personen |

**Kapazität abhängig von Kunden-Einstellungen**

    [{"oi":"CS4","kg":10},{"oi":"12760053311732","kg":7},{"oi":"12760054446917","kg":1}]

### Planungsdaten kg/Stück/Personen hinzufügen/updaten

<http://domain/fernsteuerung/planung/add_and_update_data> (Planungs
Ausgabe)

Parameters

|         |                                                                    |
|---------|--------------------------------------------------------------------|
| data    | Data Parameters                                                    |
| insert  | true(default) oder false. Nur neue Gebiete werden hinzugefügt      |
| update  | true(default) oder false. Bestehende Gebiete werden geupdated      |
| ausgabe | Name der Ausgabe (optional: defaul=Aktuelle Ausgabe des Benutzers) |

Data Parameters

|            |                 |
|------------|-----------------|
| oi         | Gebäude ID      |
| abonnenten | Anzahl Abonnent |

Data Parameters mit Straßen ID

|                    |                                                                                       |
|--------------------|---------------------------------------------------------------------------------------|
| street\_oi         | Straßen ID                                                                            |
| hausnummer         | Hausnummer                                                                            |
| hausnummer\_zusatz | Hausnummer Zusatz (optional, der Zusatz kann auch bei der Hausnummer mit dabei sein.) |
| abonnenten         | Anzahl Abonnent                                                                       |

    {
    "update": true,
    "insert": true, 
    "data": [{"oi":"CS4","kg":10},{"oi":"12760053311732","kg":7},{"oi":"12760054446917","kg":1}]
     }

    {
    "update": true,
    "insert": true, 
    "data": [{"street_oi":"1234", "hausnummer": "2","kg":3},{"street_oi":"4567", "hausnummer": "12","kg":3},{"street_oi":"4567", "hausnummer": "21","kg":3}]
     }

### Planungsdaten kg/Stück/Personen löschen

<http://domain/fernsteuerung/planung/delete_data> (Gebiets Ausgabe)

|         |                                                           |
|---------|-----------------------------------------------------------|
| oi      | Adresse ID                                                |
| ausgabe | Name der Ausgabe (defaul=Aktuelle Ausgabe des Benutzers)  |
| all     | (optional) true , alle Daten der Ausgabe werden gelöscht. |

    {
    "oi": ["CS4","12760053311732","12760054446917"]
    }
