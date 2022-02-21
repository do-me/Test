# Schneeräumung

![!](assets/snow.jpg)

<div style="font-size: 11px">
Photo by <a href="https://unsplash.com/@photoripey?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Ibrahim Rifath</a> on <a href="https://unsplash.com/s/photos/snow-street?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Unsplash</a></div>

## Szenario

Unsere Schneeräumdienste haben die wichtige Aufgabe Straßen, Gehwege und Innenhöfe von Eis und Schnee zu befreien.<br>
Hierbei kommen verschiedene Räumfahrzeuge zum Einsatz: große **Schneeschiebe-SUVs**, die eine ganze Fahrbahn von Schnee befreien und kleine wendige **Traktoren**, die auch enge Gehwege befahren können. 

## Lösung mit MultiRoute Tour!

Hier ist es wichtig, dass die einzelnen Objekte (Adressen) entsprechend gekennzeichnet werden. Welcher Kunde hat nur den Gehweg gebucht? Wer möchte auch die Straße oder beides räumen? <br>
Der Schlüssel zu einer erfolgreichen Tourenoptimierung sind hier unsere sogenannten **Skills** mithilfe derer sich diese Anforderungen darstellen lassen. Für dieses Beispiel könnte man also folgende Skills benutzen: 

|Skill | Bedeutung |
|---|---|
|SUV| großer Schneeschieber, ganze Fahrbahn räumen |
|Traktor| Gehweg räumen |

Diese Skills müssen nun bei jedem Auftrag in Ihrer Exceltabelle hinterlegt sein. Diese könnte bspw. so aussehen: 

|...|Straße Hausnummer|PLZ| Ort | Skill | Räumzeit in Sekunden |
|---|---|---|---|---|---|
|...|Hauptstraße 10| 21614 | Buxtehude |SUV| 30 |
|...|Bahnhofsweg 11| 21614 | Buxtehude |Traktor| 60 |
|...|Amselgasse 20| 21614 | Buxtehude |SUV| 30 |
|...|...| ... | ... |...| ... |

Die Räumzeit kann **individuell** mit hochgeladen oder **pauschal** für alle Aufträge gleich festgelegt werden.<br>

Werden an einer Adresse Gehweg und Straße geräumt, müssen hieraus zwei Zeilen erstellt werden, weil diese auch von zwei unterschiedlichen Fahrzeugen bedient werden.

|...|Straße Hausnummer|PLZ| Ort | Skill | Räumzeit in Sekunden |
|---|---|---|---|---|---|
|...|Hauptstraße 10| 21614 | Buxtehude |SUV| 30 |
|...|Hauptstraße 10| 21614 | Buxtehude |Traktor| 60 |
|...|...| ... | ... |...| ... |

In Ihrer Flotte geben Sie nun die Anzahl Ihrer Traktoren und SUVs an und können sofort die Touren berechnen!

Die Fahrer erhalten jeweils den [Google-Maps-Export](/tour/#tour-exportieren) und können mit Ihrem Handy losnavigieren.