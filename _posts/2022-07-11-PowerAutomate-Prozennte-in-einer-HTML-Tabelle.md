# PowerAutomate: Prozente in einer HTML-Tabelle
Dieser Beitrag knüpft an den untenstehenden Beitrag an – Ist aber auch allein stehend verwendbar.
Hier der Link zum Artikel und dar unterstehend die Ausgangssituation:

Dieser Beitrag ist thematisch mit folgendem Beitrag, verwandt und könnte gerade im Projektmanagement öfter relevant sein.
Wir beschäftigen uns hier mit dem Problem, dass als „Prozente definierte Werte“, leider als Dezimalzahl dargestellt werden und damit wie wir dies schnell bereinigen können.

Der Flow wird einmal die Woche gestartet und liest sämtliche Elemente einer SharePoint Liste ein.
Die Elemente werden dann in einer „Create HTML table“ aufbereitet und dann per E-Mail versendet.

![bild1](/images/Prozenzthema-bild1-1.png "bild1")

Das Problem ist dann schnell erklärt:
Wenn wir einen in SharePoint als Prozentzahl definierten Wert auswählen, wird dieser wie folgt in unserer E-Mail angezeigt.

![bild2](https://blog.thinformatics.com/wp-content/uploads/2022/05/Prozenzthema-bild2.png "bild2")

Eine schnelle Recherche liefert nun folgenden Artikel
Solved: Get items then format number to remove decimal usi… – Power Platform Community (microsoft.com)

Der Artikel ist sehr gut beschrieben, aber löst nicht exakt das Problem. Trotzdem ist der Artikel für Interessierte (und expression-Enthusiasten 😉 ) zu empfehlen.

Ich vermute es liegt hier (alte Excel- und CSV-Hasen kennen es) an unserem deutschen Komma wo im englischsprachigen Raum ein Punkt zur Dezimal-Trennung zum Einsatz kommt.

Mit anderen Worten ich vermute hier ein typisch deutsches Problem, was ich dann wie folgt lösen konnte.

![bild3](https://blog.thinformatics.com/wp-content/uploads/2022/05/Prozenzthema-bild3-1-1024x619.png "bild3")

Ihr geht in das Feld und wählt Expression, dort verwende ich dann eine „einfache Multiplikation“ x100. Mit folgender formel/Expression und wähle mein Spalte aus der SharePoint-Liste (in meinem Fall AufbauProzentual)

```
mul(item()?['AufbauProzentual'],100)
```

Das %-Zeichen habe ich hinterher eingefügt, nach dem der Dynamische Content im Flow als Block anzeigt wurde.

Das Ergebnis ist dann auch hier eine ansprechende Tabelle und Prozente die man als solche erkennen kann 🙂

![bild4](https://blog.thinformatics.com/wp-content/uploads/2022/05/Prozenzthema-bild4.png "bild4")

