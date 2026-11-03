# Miniprojekt: Entwurf eines neuronalen Netzwerk zur Schätzung von Kraftstoffverbrauch

In diesem Miniprojekt werden ein neuronales Netzwerk zur Schätzung von Kraftstoffverbrauch entwerfen und in ein illustratives "Anwendungssystem" (konkret auf eine HTML Seite) integrieren. 
Dadurch wird demonstriert, was für Phasen ein KI-Projekt hat.

# Geschäftsverständnis (business understanding)

- Warum ist dieses Thema überhaupt wichtig?
- Wer sind unsere Kunden?
- Was beeinflusst den Kraftstoffverbrauch?

# Datenverständnis

- Daten: http://www.biointelligence.hu/mi/fuel_data_with_errors.txt
- Infrastruktur: https://colab.research.google.com/
- Laden wir die Daten in ein Pandas Dataframe!
- Explorative Datenanalyse: berechnen wir einige grundlegende Statistiken (z.B. durchschnittlicher Verbrauch, Minimum, Maximum, Median der Spalten, Häufigkeit der einzelnen Werte) bzw. malen wir einige grundlegende Plots (z.B. Histogramme, Boxplots).

 # Datenvorverarbeitung 
 (Das ist "Phase 1" nach dem vereinfachten Schema aus der ersten Vorlesung) 
 
 **Fehlende Werte (missing values) behandeln**
 
 - Wieviele fehlende Werte gibt es in den einzelnen Spalten?
 - Was können wir mit denen machen? Ersetzen mit dem Durchschnitt oder dem häufigsten Wert? Oder können wir etwas Besseres machen?
 - Was kann man machen, wenn viele Werte fehlen?

 **Entfernen von Duplikaten** 

 - In diesem Miniprojekt reicht es aus, wenn wir die exakten Duplikate entfernen.
 - Was könnte man machen, wenn man auch "approximate Duplikate" (z.B. "Klemens" vs. "Clemens") hätte?

 **Inkonsistente Werte behandeln**

 - Ein einfacher Fall der Inkonsistenz ist, wenn eine Spalte "nicht erlaubte" Werte enthält. Überprüfen Sie die Spalte "air conditioner" und ersetzen Sie die "falschen" Werte mit den "richtigen" Werten!

 **Outlier (Ausreißer) erkennen und eliminieren**

 - Gibt es Outlier im Datensatz? (Hiweis: betrachten wir die Werbrauchswerte)
 - Können Outlier immer basierend auf die Werte in *einer* Spalte erkannt werden?

 **Wir laden die bereinigten Daten**

 - In der Wirklichkeit haben die "bereinigten" Daten natürlich erst als Resultat der obigen Bereinigungsschritte, jetzt können wir aber die bereinigten Daten von dieser URL laden: http://www.biointelligence.hu/mi/fuel_data.txt .

 **Auswahl der Daten**

 - Welche Informationen sind aus der Sicht des Kraftstoffverbrauchs relevant? Wählen Sie 3-5 relevante Spalten aus!

 **Datentransformation**

 - Um die Datentransformation auf einem einfachen Beispiel zu demonstrieren, nehmen wir an, dass wir im vorigen Schritt beide Spalten mit Temperaturwerten ausgewählt haben, aber wir haben uns dafür entschieden,
   ein solches neuronales Netzwerk zu entwerfen, das nur einen Temperaturwert als Eingabe annimmt. Deswegen werden wir den Durchschnitt der beiden Temperaturwerte in eine neue Spalte berechnen. 
 -  

