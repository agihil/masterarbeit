# masterarbeit

Das Repository enthält Daten und Code, die ich im Rahmen meiner Masterarbeit 2022 erzeugt habe. Ziel der Arbeit war, in deutschsprachigen Romanen, die zwischen 1760 und 1920 erschienen sind die Entwicklung der relativen Häufigkeiten konkreter und abstrakter Wortfelder zu untersuchen.

Für einen kurzen Abriss von Fragestellung, Methodik, Korpus und Ergebnissen s. das folgende, auf der DHD2023 präsentierte Poster:
https://zenodo.org/record/7711478#.ZB7UHS9XZAd

## Daten

Das verwendete Korpus enthält 1147 Romane. Es basiert auf den Sammlungen des Projekts Gutenberg und TextGrid. Die Datei "data/metadaten.csv" enthält Metadaten zu den untersuchten Romanen. Der Ordner "figures/corpus_info_plots" enthält Grafiken, die die Zusammensetzung des Korpus zeigen. Die 34 Listen von Wörtern wurden auf Basis von Germanet erstellt und mit einem Fasttext-Modell erweitert. Diese Daten können hier nicht zur Verfügung gestellt werden. Die Datei "data/wortfelder.csv" enthält lediglich eine Liste der berücksichtigten Wortfelder. 

Die ermittelten Werte liegen jedoch in folgenden Dateien bereit:

- eine csv-Datei, die die Anteile der Wörter der untersuchten Wortfelder pro Roman anzeigt ("data/roman_corpus_word_frequencies.csv", )
- eine csv-Datei, die die auf Basis des Datensatzes von Sabine Schulte im Walde und Maximilian Köper errechneten Konkretheitswerte für jeden Roman enthält ("data/roman_corpus_AbstConc.csv")
- eine csv-Datei, die Wortfeld-Anteile und Konkretheitswerte unter Berücksichtigung des Redewiedergabe-Typs enthält ("data/roman_korpus_word_frequencies_redewiedergabe.csv").

## Figures

Der Ordner "figures" und seine Unterordner enthalten die in den Notebooks "visualisierung.ipynb" und "corpus_info.ipynb" erzeugten Grafiken.

Folgende Grundtypen gibt es:

- Scatterplots, in denen jeder Punkt einen Roman repräsentiert. In der Regel zeigt die x-Achse hier das Erscheinungsjahr des Romans (außer in den beiden Grafiken, in denen die Anteile abstrakter gegen die Anteile konkreter Wörter geplottet werden ("abstrakt_vs_konkret")). Die y-Achse zeigt die Anteile der untersuchten konkreten bzw. abstrakten Wörter an den Wörtern des jeweiligen Romans. In den Plots, die mit dem Zusatz "col_gender" versehen sind, sind die Punkte nach dem Geschlecht des Autors bzw. der Autorin eingefärbt. Im Unterordner "figures/colored_autoren" finden sich Scatterplots, die wiederum die Anteile konkreter Wörter visualisieren, dabei aber die Romane einiger bekannter Autor:innen farblich hervorheben.
- Scatterplots, in denen jeder Punkt einen Roman repräsentiert. Die x-Achse zeigt die Anteile konkreter Werte, die y-Achse die Anteile abstrakter Wörter am jeweiligen Roman. Die Scatterplots sind einmal nach Erscheinungsjahr, einmal nach Autor:innen-Geschlecht eingefärbt ("scatterplot_anteil_abstrakt_vs_konkret_col_year.png", "scatterplot_anteil_abstrakt_vs_konkret_col_gender.png")
- Lineplots, die die Durchschnittswerte der jeweiligen Wortfeld-Anteile zeigen. Die graue Kurve im Hintergrund zeigt die tatsächliche Kurve, die farbige Kurve im Vordergrund ist geglättet. Im Hauptordner finden sich Abbildungen, die die Anteile konkreter und abstrakter Wörter insgesamt zeigen, sowie Abbildungen, in denen die Kurven der Anteile verschiedener Wortfelder übereinanderliegen. Im Unterordner "figures/lineplots_einzelne_wortfelder" finden sich die Abbildungen zu allen einzelnen untersuchten Wortfeldern.
- im Unterordner "figures/redewiedergabe" finden sich weitere Grafiken derselben Typen, die sich jeodch nicht auf den Romantext insgesamt beziehen, sondern die mit dem Redewiedergabe-Tagger annotierten Redewiedergabe-Typen berücksichtigen. 
- Die Abbildung "scatterplot_konkretheitswerte.png" zeigt die auf Basis des Datensatzes von Köper/Schulte im Walde berechneten Konkretheitswerte (s. count_concreteness_scores.ipynb)
- Der Unterordner "figures/corpus_info" enthält Histogramme, die die Zusammensetzung des Korpus’ zeigen sollen.

## Notebooks

### corpus_info.ipynb

Das Notebook "corpus_info.ipynb" erstellt auf Basis der metadaten Grafiken, die über die Zusammensetzung des Korpus informieren sollen. Die dabei erzeugten Grafiken finden sich im Ordner "figures/corpus_info_plots".

### count_word_frequencies.ipynb

[Da das lemmatisierte Korpus und die Wortlisten hier nicht zur Verfügung gestellt werden, ist das Notebook so nicht ausführbar. Es soll lediglich zeigen, wie die Worthäufigkeiten ermittelt wurden.]

Das Notebook "count_word_frequencies.ipynb" liest das im preprocessing mit spacy lemmatisierte Roman-Korpus sowie die zuvor erstellten Listen von Wörtern verschiedener Wortfelder ein.

1.) Für jeden Roman wird der  Anteil der Wörter jedes Wortfeldes berechnet. Zudem werden für eine kleine Gruppe von "Grundwörtern" (z.B. die Grundfarben "rot", "blau", "grün") deren Anteile an den Romanen berechnet.

2.) In einem zweiten Schritt werden Informationen zur Redewiedergabe berücksichtigt. In fiktionalen Erzähltexten spricht nicht nur der Erzähler, sondern auch die Figuren. Mithilfe des Redewiedergabe-Taggers (https://github.com/redewiedergabe/tagger) lassen sich vier verschiedene Redewiedergabe-Typen in Romanen annotieren. Die hier untersuchten Romane wurden mit dem Redewiedergabe-Tagger getaggt. Der Romantext, der nicht in eine der Redewiedergabe-Kategorien fällt, wurde als Erzählertext gewertet. Anschließend wurden die Wortfelder zu den Kategorien "konkret" und "abstrakt" zusammengefasst und für beide Gruppen der Anteil am jeweiligen Redewiedergabe-Typ pro Roman berechnet. 

### count_concreteness_scores.ipynb

Für dieses Notebook wurde ein Datensatz verwendet, den Sabine Schulte im Walde und Maximilian Köper erstellt haben: Für 350.000 deutsche Lemmata ermittelten sie automatisiert einen "Concreteness"-Wert. Als konkrete Wörter werden dabei solche verstanden, die etwas referenzieren, was man mit den Sinnen wahrnehmen kann.

Der Datensatz kann hier heruntergeladen werden: https://www.ims.uni-stuttgart.de/en/research/resources/experiment-data/affective-norms/ 

Das Notebook liest den zuvor heruntergeladenen Datensatz sowie das zuvor mit spacy lemmatisierte Romankorpus ein. Für jeden Roman wird über dessen Lemmata iteriert, für jedes Lemma wird überprüft, ob es im Datensatz vorhanden ist. Falls es vorhanden ist, wird der dort angegebene Konkretheitswert zu allen vorherigen Konkretheitswerten des Romans addiert. Schließlich wird der Konkretheitswert normalisiert, indem er durch die Anzahl der Wörter des jeweiligen Romans geteilt wird. Die Konkretheits-Werte, die sich daraus ergeben haben, liegen in der Datei "data/roman_corpus_AbstConc.csv"

### visualisierung.ipynb

Das Notebook "visualisierung.ipynb" dient dazu, die in den Notebooks "count_concreteness_scores.ipynb" und "count_word_frequencies.ipynb" errechneten Werte zu visualisieren. Die erzeugten Grafiken werden jeweils im Ordner "figures" bzw. dessen Unterordnern abgelegt.

### mannkendall.ipynb

Das Notebook "mannkendall.ipynb" führt für die in den Notebooks "count_concreteness_scores.ipynb" und "count_word_frequencies.ipynb" errechneten Werte einen statistischen Signifikanztest für Zeitreihen durch. Dafür wird die Implementierung des Python-Mann-Kendall-Tests des Pakets "pymannkendall" benutzt. Die Ergebnisse sind direkt im Notebook einsehbar.

### annotate_texts.ipynb

Das Notebook "annotate_texts.ipynb" ermöglicht es, die bei der Analyse berücksichtigten Wörter in einzelnen Romanen zu annotieren, sodass diese bei einem Close Reading besonders beachtet werden können.

Zunächst werden die Wortlisten eingelesen. Die Funktion "annotate_novel" benötigt drei Argumente: zwei Listen von Wörtern und den Pfad zu einer txt-Datei. Die txt-Datei mit dem Roman wird eingelesen, die Wörter der beiden Wortlisten werden mit markup-Versehen. Ausgegeben wird eine xml-Datei, in der der Text liegt, wobei die Wörter der ersten Wortliste durch Fettung, die der zweiten durch Kursivierung hervorgehoben sind.

## Pakete

Folgende Pakete wurden zum Ausführen der Notebooks in der angegebenen Version verwendet:

- pandas==1.5.2
- tqdm==4.64.1
- re==2.2.1
- plotly==5.9.0
- glob
- collections
- pathlib
- pymannkendall



