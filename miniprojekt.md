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
 (Erste Phase auf der Folie "Ein vereinfachtes Schema der KI Projekte") 
 
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

 - Um die Datentransformation auf einem einfachen Beispiel zu demonstrieren, nehmen wir an, dass wir im vorigen Schritt beide Spalten mit Temperaturwerten ausgewählt haben, aber wir entscheiden uns dafür, ein solches neuronales Netzwerk zu entwerfen, das nur einen Temperaturwert als Eingabe annimmt. Deswegen werden wir den Durchschnitt der beiden Temperaturwerte in eine neue Spalte berechnen. 
 - Wir nehmen an, dass wir jene Spalte, welche die Intensität des Verkehrs ("low", "normal", "high") enthält, auch ausgewählt haben. Wir wandeln diese Spalte in eine numerische Spalte um, dabei beachten wir, dass die resultierenden Zahlen mit dem Verbrauch korrelieren (d.h. wir führen eine *ordinale Variable* ein).

**Normalisierung der Daten**
(Man kann diesen Schritt auch zu "Datentransformation" zählen.)

- Wenn man neuronale Netzwerke trainiert, ist es oft eine gute Idee, die Eingaben zu normalisieren. Normalisieren Sie die Daten mit den Durschschnitten und Standardabweichungen der einzelnen Spalten!

# Training des Models
(Zweite Phase auf der Folie "Ein vereinfachtes Schema der KI Projekte")

**Variante 1: schnelle Variante**

- Definieren Sie ein Feed-Forward Neuronales Netzwerk mit einer verstecken Schicht mit 5 Neuronen und ReLU Aktivierungsfunktion! Schreiben Sie den Code der entsprechenden pytorch Klasse, welche die Architektur des Netzwerks angibt!
- Schreiben Sie den Code der Trainingsschleife und trainieren Sie das Netzwerk auf den vorbereiteten Daten!

**Variante 2: Experimentelle Evaluation mehrerer Modelle**

- Definieren Sie unterschiedliche Neuronale Netwerke: Geben Sie den Code der entsprechenden pytorch Klassen, welche die Architekturen der Netzwerke enthält, an! (Hinweis: Wenn Sie komplizierte Modelle wählen, könnte die Integration in der letzten Phase aufwendig sein.) 
- Trainieren und evaluieren Sie die Netzwerke mit 10-facher Kreuzvalidierung!
- Trainieren Sie das beste Netzwerk auf allen Daten!
- Ist die Genauigkeit, welche Sie während der 10-fach Kreuzvalidierung im Falle des besten Netzwerks gemessen haben, eine statistisch unverzerrte Schätzung der tatsächlichen Genauigkeit dieses Netzwerks? 

# Inbetiebnahme (Deployment)
(Dritte Phase auf der Folie "Ein vereinfachtes Schema der KI Projekte")

Unser illustratives Anwendungssystem ist in diesem Miniprojekt eine HTML Seite. Natürlich kann man auch in der "Wirklichkeit" das neuronale Netzwerk in eine Webanwendung integrieren, aber man kann sich auch andere Anwendungssysteme vorstellen, z.B. ein Auto (wenn man ein neuronales Netzwerk für die Erkennung von Verkehrsschilder trainiert).

FCE.html:

```
<html>
<head>
<title>
  Fuel consumption estimation
</title>
</head>

<script type="text/javascript">
  function estimate_cons() {
    /* we will insert the code here that will reproduce the calculations that
       the neural network does */
    window.alert("Not implemented yet.")
  }
</script>

<body>
<h1>Fuel consumption estimation<h1>
<form name="input_data">
<table>
<tr>
  <td>Starttemp:</td>
  <td><input type="text" name="temp1" size=3></td>
</tr>
<tr>
  <td>Endtemp:</td>
  <td><input type="text" name="temp2" size=3></td>
</tr>
<tr>
  <td>Average speed:</td>
  <td><input type="text" name="speed" size=3></td>
</tr>
<tr>
  <td></td>
  <td><input type="button" onclick="estimate_cons()" value="Calculate"></td>
</tr>
</table>
</form>
</body>
</html>

```

**Anpassung der HTML Datei**

- Passen Sie die HTML Datei an, damit der Benutzer jene Daten angeben kann, welche die Eingaben Ihres Netzwerks sind.
- Őffnen Sie die Datei in einem Webbrowser und probieren Sie die aktuelle Version Ihrer HTML Seite aus!

**Integration des Netwerks in die HTML Seite**

Unser Ziel ist es, jene Berechnungen, die das trainierte Netzwerk macht, in dem Zeilsystem (auf der HTML Seite) zu reproduzieren. Wir können dazu auf die Parameter des trainierten Netzwerks so ausgeben lassen:

```
for p in net.parameters():
  print(p)
```

Die Ausgabe sieht ungefähr so aus:

```
Parameter containing:
tensor([[ 0.2509, -0.2061,  0.1073],
        [-0.2059, -0.2937, -0.1009],
        [ 0.1150,  0.2625, -0.3610],
        [ 0.6465, -0.2293,  0.4714],
        [ 0.3817,  0.4118, -0.5667],
        [-0.3119, -0.4398,  0.0307],
        [ 0.0666,  0.1040,  0.1719],
        [ 0.3125,  0.1885, -0.3690],
        [ 0.1097,  0.7307, -0.4844],
        [-0.3408, -0.2709,  0.0361]], requires_grad=True)
Parameter containing:
tensor([-0.2061,  0.4432,  0.1330, -0.2794, -0.1213, -0.1389, -0.5187,  0.2188,
        -0.4756, -0.1425], requires_grad=True)
Parameter containing:
tensor([[-0.1407, -0.0554,  0.1907,  0.1611,  0.6042,  0.1442, -0.0315,  0.3453,
          0.6535, -0.2172]], requires_grad=True)
Parameter containing:
tensor([0.3992], requires_grad=True)
```

In dem obigen Fall, hat das Netzwerk

- eine Eingabeschicht mit 3 Eingaben, 
- eine versteckte Schicht mit 10 künstlichen Neuronen, und
- eine Ausgabeschicht mit einem einzigen Neuron.

Als Beispiel betrachten wir die Gewichte des ersten Neurons in der versteckten Schicht (in der Eingabeschicht werden keine Berechnungen ausgeführt): 

```
Parameter containing:
tensor([[ 0.2509, -0.2061,  0.1073],
       ... )
Parameter containing:
tensor([-0.2061, ... ], requires_grad=True)
...
```

Das heißt, dass das erste Neuron der verstecketen Schicht diese gewichtete Summe berechnet:

```
h1 = 0.2509*input1 + (-0.2061)*input2 + 0.1073*input3 + (-0.2061)
```

Wenn wir die ReLU Aktivierungsfunktion benutzen, und wir wollen, dass h1 die Aktivierung des Neurons enthält, können wir in der HTML Datei diesen JavaScript Code benutzen:

```
    h1  =  0.2509*input1 - 0.2061*input2 + 0.1073*input3 - 0.2061;
    if (h1 < 0) { h1 = 0; }
```

Ähnlicherweise lassen sich alle Berechnung des trainierten neuronalen Netzwerks in der HTML Datei reproduzieren. Je nach dem, wie kompliziert Ihr Netzwerk ist, schreiben Sie entweder den JavaScript Code, um die Berechnungen zu reproduzieren, oder einen Python-Code, der den JavaScript Code generiert. 

**ONNX**

In industriellen Projekten würde man in diesem Schritt das trainierte neuronale Netzwerk oft nicht auf ein JavaScript Code übersetzen, sondern in ONNX Format konvertieren. Lesen Sie über ONNX z.B. hier: https://onnx.ai/
