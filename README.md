# masterarbeit

Das Repository enthält Daten und Code, die ich im Rahmen meiner Masterarbeit 2022 erzeugt habe. Ziel der Arbeit war, einen bei Heuser/Le-Khac 2012 und Underwood 2017 beschriebenen Trend für deutschsprachige Romane zu untersuchen.

Grundsätzlich geht es darum, die Entwicklung von Worthäufigkeiten verschiedener Wortfelder in deutschsprachigen Romanen, die zwischen 1760 und 1920 erschienen sind, zu ermitteln.
Für einen kurzen Abriss von Fragestellung, Methodik, Korpus und Ergebnissen s. das folgende, auf der DHD2023 präsentierte Poster:
https://zenodo.org/record/7711478#.ZB7UHS9XZAd

## Daten

Das verwendete Korpus enthält 1147 Romane. Es basiert auf den Sammlungen des Projekts Gutenberg und TextGrid. Die Datei "metadata.csv" enthält Metadaten zu den untersuchten Romanen. Der Ordner "corpus_info_plots" enthält Grafiken, die die Zusammensetzung des Korpus zeigen. Die 34 Listen von Wörtern wurden auf Basis von Germanet erstellt und mit einem Fasttext-Modell erweitert. Diese Daten können hier nicht zur Verfügung gestellt werden. Die ermittelten Worthäufigkeiten und die Metadaten liegen jedoch in der Datei "xyz" bereit.

## Notebooks

### corpus_info.ipynb

Das Notebook "corpus_info.ipynb" erstellt auf Basis der metadaten Grafiken, die über die Zusammensetzung des Korpus informieren sollen. Die dabei erzeugten Grafiken finden sich im Ordner "corpus_info_plots".

### count_word_frequencies.ipynb

[Da das lemmatisierte Korpus und die Wortlisten hier nicht zur Verfügung steht, ist das Notebook so nicht ausführbar. Um transparent zu machen, wie die Worthäufigkeiten gezählt wurden steht es trotzdem hier bereit.]

Das Notebook "count_word_frequencies.ipynb" liest das im preprocessing mit spacy lemmatisierte Roman-Korpus sowie die zuvor erstellten Listen von Wörtern verschiedener Wortfelder ein.

1.) Für jeden Roman wird der  Anteil der Wörter jedes Wortfeldes berechnet. Zudem werden für eine kleine Gruppe von "Grundwörtern", z.B. die Grundfarben "rot", "blau", "grün", deren Anteile an den Romanen berechnet.

2.) In einem zweiten Schritt werden Informationen zur Redewiedergabe berücksichtigt. In fiktionalen Erzähltexten spricht nicht nur der Erzähler, sondern auch die Figuren. Mithilfe des Redewiedergabe-Taggers (https://github.com/redewiedergabe/tagger) lassen sich vier verschiedene Redewiedergabe-Typen in Romanen annotieren. Die hier untersuchten Romane wurden mit dem Redewiedergabe-Tagger getaggt. Der Romantext, der nicht in eine der Redewiedergabe-Kategorien fällt wurde als Erzählertext gewertet. Anschließend wurden die Wortfelder zu den Kategorien "konkret" und "abstrakt" zusammengefasst und für beide Gruppen der Anteil am jeweiligen Redewiedergabe-Typ pro Roman berechnet. 

3.) Um Kandidaten zu identifizieren, die sich für ein an die quantitative Analyse anschließendes Close Reading eignen, wurden die Romane mit den höchsten bzw. niedrigsten Werten bei konkreten und abstrakten Wörtern ausgegeben.

### count_concreteness_scores.ipynb

### visualisierung.ipynb

### mannkendall.ipynb

## Results

Der Ordner "results" enthält:

- eine csv-Datei, die die Anteile der Wörter der untersuchten Wortfelder pro Roman anzeigt
- eine csv-Datei, die die auf Basis des Datensatzes von Sabine Schulte im Walde und Maximilian Köper errechneten Konkretheitswerte für jeden Roman enthält
- eine csv-Datei, die Wortfeld-Anteile und Konkretheitswerte unter Berücksichtigung des Redewiedergabe-Typs enthält.


# Pakete

Folgende Pakete wurden zum Ausführen der Notebooks in der angegebenen Version verwendet:

- pandas==1.5.2
- tqdm==4.64.1
- re==2.2.1
- plotly==5.9.0
- glob
- collections
- pathlib
- pymannkendall



