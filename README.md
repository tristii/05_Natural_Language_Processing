# 05_Natural_Language_Processing

Binder Badge zum starten des Jupyter Notebooks (NLP_Projekt_Musterloesung.ipynb) via myBinder: [![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/tristii/05_Natural_Language_Processing/main?labpath=NLP_Projekt_Musterloesung.ipynb) 

In der Umgebung von mybinder können Sie das Übungsbeispiel ausführen lassen, eigene Lösungen codieren (bestehenden Code modifizieren), um das Übungsbeispiel mit dem erwartenden Ergebnis zu reproduzieren.

## Dokumentation zur Übungsaufgabe: 
Aufgebaut ist die Übungsaufgabe in jeweils in Beschreibungsabschnitt was explizit gemacht werden soll. Die jeweilige darunterliegende Zelle stellt den Code Bereich dar, in der dieser Aufgabenabschnitt codiert wird und ggf. den dazugehörigen Output nach der Ausführung (SHIFT + Enter) der jeweiligen Codezelle darstellt.

! Um das zu erwartendee Ergebnis (Output) der Lösung im Übungsbeispiel nicht zu verlieren bzw. zu überschreiben, können Sie nach der Beschreibung der jeweiligen Teil-Aufgabe eine Zwischenzeile(neue Zeile) einfügen, in der Sie Ihre Lösung codieren um danach Ihren Code mit dem darunter liegenden Mustercode + dessen Output vergleichen/überprüfen zu können. 

**Vorgehensweise im Übungsbeispiel:**

Fallbeispiel: In diesem NLP Projekt werden wir versuchen Yelp Reviews in 1 Stern oder 5 Sterne Kategorien zu klassifizieren. Dazu nutzen wir den Text ihrer Bewertung. Wir nutzen Yelp Review Daten von Kaggle. Jede Beobachtung in dem Datensatz ist eine bestimmte Bewertung eines bestimmten Geschäfts durch einen bestimmten Nutzer. Die "stars" Spalte beinhaltet die Anzahl der Sterne (1 bis 5) die der Bewerter dem Geschäft verliehen hat. In anderen Worten: Die Bewertung des Geschäfts durch den Autor. Die "cool" Spalte beinhaltet die Anzahl der "Cool"-Votes der Bewertung durch andere Nutzer.
Alle Bewertungen starten mit 0 "Cool"-Votes und es gibt nach oben kein Limit. Je mehr Leute die Bewertung "Cool" finden und sie so voten, desto höhere die Anzahl. Für die "useful" (dt. nützlich) und "funny" (dt. witzig) Spalten gilt das gleiche.

**1. Libraries**
* notwendige Libraries müssen importiert werden (pandas, numpy, matplotlib.pyplot, seaborn) für die Datenverarbeitung und Datenvisualisierung

**2. Rohdaten**
* Rohdaten (Yelp.csv) einlesen und DataFrame erstellen
* Deskriptive Statistiken anzeigen und analysieren mit der head(), info() und describe() Funktion
* Erstelle eine neue Spalte namens "text length", welche die Anzahl von Zeichen der "text" Spalte beinhaltet.

**3. Explorative Datenanalyse**

mittels Plots aus der Seaborn und Pandas Library können die Daten visualisiert werden, um sie besser analysieren zu können. 
* FacetGrid (von Seaborn) erstellen, um ein Grid von 5 Histogrammen zu erzeugen. Diese sollen auf den "stars" basieren
* Erstelle ein Boxplot der Textlänge "text length" für jede Stern-Kategorie 
* Erstelle ein Countplot für die Anzahl an Erscheinungen jeder Stern-Kategorie
* Gruppiere die Stern-Kategorie, um den Durchschnittswert der numerische Werte zu erhalten
* Wende die Korrelation corr() Methode auf das Groupby- DataFrame an
* Lass dir die Korrelation in einer Heatmap anzeigen (Seaborn) 


**4. NLP Klassifizierungsaufgabe**
* DataFrame erstellen, die alle Spalten aus dem Yelp Dataframe beinhaltet (aber nur für 1 und 5 Sterne) 
* Erstelle zwei Objekte X und y. X wird der "text" aus yelp_class und y wird die "stars" sein
* import CountVectorizer von sklearn.feature_extraction.text und erstelle davon ein Objekt 
* Nutze die fit_transform Methode auf das CountVectorizer Objekt und übergebe X (die "text" Spalte). Speichere dieses Ergebnis, indem du X überschreibst


**5. Train Test Split**
* import train_test_split von sklearn.model_selection
* Aufteilen der Daten in Trainings- und Testdaten (test_size = 0.3; random_state = 101)

**6. Das Modell trainieren**
* import MultinomialNB von sklearn.naive_bayes und erstelle eine Instanz davon 
* Traningsdaten darauf fitten mit der fit() Funktion 

**7. Vorhersage und Auswertung**
* predict Methode verwenden, um von nb ausgehend X_test vorherzusagen
* import classification_report,confusion_matrix von sklearn.metrics
* Klassifizierungsreport für das Modell erstellen, um die Perfomance in Bezug auf Precision und Recall Werte zu erhalten 
* Confusion Matrix erstellen, um die Leistung des Algorithmus visualisieren zu können

**8. Text Processing verwenden**
* import TfidfTransformer von sklearn.feature_extraction.text 
* import Pipeline von sklearn.pipeline
* Erstelle eine Pipeline mit den folgenden Schritten: CountVectorizer(), TfidfTransformer(), MultinominalNB()

**9. Train Test Split** 
* Aufteilen der Daten in Trainings- und Testdaten für das yelp_class object 
* Fitte die Pipeline auf die Trainingsdaten !Es können nicht dieselben Trainingsdaten wie zuvor verwendet werden, da diese bereits vektorisiert wurden. Wir benötigen nur den Text

**10. Vorhersage und Auswertung** 
* Nutze die Pipeline um die Sterne für X_test mit predict() vorherzusagen
* Klassifizierungsreport für das Modell erstellen, um die Perfomance in Bezug auf Precision und Recall Werte zu erhalten 
* Confusion Matrix erstellen, um die Leistung des Algorithmus visualisieren zu können
