# Analyse von Immobilienpreisen

### Projektmitglieder
•⁠  ⁠Helena Gigler
•⁠  ⁠Clara Haller
•⁠  ⁠Elena Jovic
•⁠  ⁠Franka Jahn
•⁠  ⁠Lena Krejci
•⁠  ⁠Katharina Legat

---

## Projektbeschreibung
Im Rahmen dieses Projekts haben wir einen Datensatz zu Immobilienpreisen in Taiwan analysiert und verschiedene Schritte aus dem Bereich Data Science durchgeführt. Ziel des Projekts war es, die Daten aufzubereiten, wichtige Einflussfaktoren auf den Immobilienpreis zu identifizieren und anschließend ein Machine-Learning-Modell zur Vorhersage von Immobilienpreisen zu entwickeln und zu bewerten.

## Datenaufbereitung
Zu Beginn haben wir den Datensatz eingelesen und die Spaltennamen übersichtlich umbenannt. Anschließend wurden fehlerhafte Einträge und fehlende Werte überprüft. Dabei haben wir einen fehlerhaften Datensatz entdeckt, bei dem die ID als Textwert („fourhundredthirteen“) gespeichert war. Dieser Fehler wurde korrigiert und die ID anschließend in einen numerischen Wert umgewandelt. 

Außerdem wurden Datensätze mit fehlenden Werten entfernt. Nach der Bereinigung enthielt der Datensatz noch 409 vollständige Datensätze und konnte für die weitere Analyse und Modellierung verwendet werden.

## Explorative Datenanalyse
Im nächsten Schritt wurde der Datensatz genauer untersucht. Dafür wurden statistische Kennzahlen wie Mittelwert, Standardabweichung sowie Minimum- und Maximalwerte berechnet.

Zusätzlich haben wir verschiedene Diagramme erstellt, um die Daten besser zu verstehen:
•⁠  ⁠Histogramm der Immobilienpreise
•⁠  ⁠Boxplot zur Erkennung von Ausreißern
•⁠  ⁠Korrelationsmatrix (Heatmap)
•⁠  ⁠Pairplot wichtiger Merkmale

Durch den Boxplot konnten wir erkennen, dass bei der Entfernung zu öffentlichen Verkehrsmitteln einige sehr große Werte vorhanden sind. Diese wurden als mögliche Ausreißer betrachtet und näher untersucht.

Die Korrelationsanalyse lieferte mehrere interessante Ergebnisse:
•⁠  ⁠*Entfernung zu öffentlichen Verkehrsmitteln:* Steht in einem deutlich negativen Zusammenhang mit dem Immobilienpreis. Je weiter eine Immobilie von einer Haltestelle entfernt liegt, desto niedriger ist in der Regel ihr Preis.
•⁠  ⁠*Convenience Stores:* Die Anzahl der Supermärkte in der Umgebung wirkt sich positiv auf den Preis aus.
•⁠  ⁠*Geografische Lage:* Auch die geografische Lage (Latitude und Longitude) zeigt einen deutlichen Zusammenhang mit dem Immobilienpreis.
•⁠  ⁠*Alter der Immobilie:* Das Gebäudealter hat einen leicht negativen Einfluss auf den Preis.

Diese Ergebnisse erscheinen plausibel, da gut erreichbare und zentral gelegene Immobilien häufig gefragter und damit teurer sind als abgelegene Objekte. Gleichzeitig zeigen die Zusammenhänge, dass die ausgewählten Merkmale grundsätzlich geeignet sind, den Immobilienpreis zu erklären und später vorherzusagen.

## Vorbereitung Machine Learning Modell
Für die Vorhersage der Immobilienpreise wurden die Daten in Trainings- und Testdaten aufgeteilt:
•⁠  ⁠*Trainingsdaten:* 327 Datensätze (80 %)
•⁠  ⁠*Testdaten:* 82 Datensätze (20 %)

Anschließend wurden die Eingabedaten mithilfe eines ⁠ StandardScaler ⁠ skaliert, damit alle Merkmale in einem vergleichbaren Wertebereich liegen. Danach wurden zwei Regressionsmodelle trainiert und verglichen:
1.⁠ ⁠Lineare Regression
2.⁠ ⁠Decision Tree Regression

Ziel war es zu untersuchen, wie gut sich die Immobilienpreise anhand der vorhandenen Merkmale vorhersagen lassen.

## Machine Learning Modell und Ergebnisse
Die Modelle wurden auf dem festgelegten 80/20-Datensplit bewertet:

•⁠  ⁠*Bestimmtheitsmaß ($R^2$):* Beide Modelle erzielten ähnliche Ergebnisse mit einem $R^2$-Wert von etwa 0.61–0.62. Das bedeutet, dass rund 62 % der Unterschiede in den Immobilienpreisen durch die vorhandenen Merkmale erklärt werden können. Für einen Datensatz mit nur wenigen Merkmalen ist dies ein solides Ergebnis, zeigt jedoch auch, dass weitere Einflussfaktoren eine wichtige Rolle spielen.
•⁠  ⁠*Vorhersagefehler (MAE):* Der MAE liegt bei etwa 6. Da die Preise in Zehntausend NT$ angegeben sind, entspricht dies einem durchschnittlichen Vorhersagefehler von ungefähr 60.000 NT$. Im Vergleich zum durchschnittlichen Immobilienpreis von etwa 38 ergibt sich ein Fehler von ca. 15–16 %. Die Modelle liefern somit brauchbare Vorhersagen, sind jedoch nicht präzise genug, um den tatsächlichen Marktwert einer Immobilie exakt zu bestimmen.
•⁠  ⁠*Wichtigstes Merkmal:* Das wichtigste Feature für die Preisvorhersage ist die Distanz zur nächstgelegenen Haltestelle öffentlicher Verkehrsmittel. Das bestätigen die Ergebnisse der Korrelationsanalyse sowie die Gewichtungen innerhalb der Modelle. Somit wird gezeigt, dass die Lage einer Immobilie einen entscheidenden Einfluss auf ihren Marktwert hat.
•⁠  ⁠*Modellvergleich:* Interessant ist außerdem, dass der Decision Tree keine deutlich besseren Ergebnisse als die lineare Regression erzielt. Das bedeutet, dass die Zusammenhänge zwischen den vorhandenen Merkmalen und dem Immobilienpreis überwiegend linear sind. 

Insgesamt konnte das ursprüngliche Ziel des Projekts somit erreicht werden. Die Modelle sind in der Lage, Immobilienpreise mit einer soliden Genauigkeit vorherzusagen. Die Ergebnisse zeigen jedoch auch, dass zusätzliche Informationen wie Wohnfläche, Zustand, Ausstattung oder besonders gute Lage die Vorhersagegenauigkeit wahrscheinlich weiter verbessern würden.

## Fazit
Im Verlauf des Projekts konnten die Daten erfolgreich bereinigt, analysiert und für Machine Learning aufbereitet werden. Die Untersuchung zeigte, dass insbesondere die Lage einer Immobilie einen großen Einfluss auf ihren Preis hat. 

Die entwickelten Modelle konnten einen wesentlichen Teil der Preisunterschiede erklären und lieferten insgesamt solide Vorhersagen. Gleichzeitig wurde deutlich, dass die Genauigkeit durch zusätzliche Merkmale weiter verbessert werden könnte. Das Projekt verdeutlicht, wie wichtig eine sorgfältige Datenaufbereitung und explorative Analyse sind, um aussagekräftige Machine-Learning-Modelle zu entwickeln und Immobilienpreise möglichst zuverlässig vorherzusagen.

## Verwendete Hilfsmittel & Technologien
•⁠  ⁠*Infrastruktur & IDE:* GitHub, Visual Studio / VS Code
•⁠  ⁠*Programmiersprache:* Python
•⁠  ⁠*Bibliotheken:* Pandas, NumPy, Matplotlib, Seaborn, Scikit-Learn
•⁠  ⁠*Sonstiges:* KI-Unterstützung zur Überprüfung von Codeabschnitten, Fehleridentifikation und sprachlichen Optimierung der Projektdokumentation.
