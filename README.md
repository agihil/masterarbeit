# masterarbeit

Das Repository enthält Daten und Code, die ich im Rahmen meiner Masterarbeit 2022 erzeugt habe. Ziel der Arbeit war, einen bei Heuser/Le-Khac 2012 und Underwood 2017 Trend für deutschsprachige Romane zu untersuchen.

Grundsätzlich geht es darum, die Entwicklung von Worthäufigkeiten verschiedener Wortfelder in deutschsprachigen Romanen, die zwischen 1760 und 1920 erschienen sind, zu ermitteln.
Für einen kurzen Abriss von Fragestellung, Methodik, Korpus und Ergebnissen s. das folgende, auf der DHD2023 präsentierte Poster:
https://zenodo.org/record/7711478#.ZB7UHS9XZAd

## Daten

Das verwendete Korpus enthält 1147 Romane. Es basiert auf den Sammlungen des Projekts Gutenberg und TextGrid. Die 31 Listen von Wörtern wurden auf Basis von Germanet erstellt und mit einem Fasttext-Modell erweitert. Diese Daten können hier nicht zur Verfügung gestellt werden. Die ermittelten Worthäufigkeiten und die Metadaten liegen jedoch in der Datei "xyz" bereit.

## Notebooks

### count_word_frequencies

Das Notebook "count_word_frequencies" liest das im preprocessing mit spacy lemmatisierte Roman-Korpus sowie die zuvor erstellten Listen von Wörtern verschiedener Wortfelder ein.

1.) Für jeden Roman wird der  Anteil der Wörter jedes Wortfeldes berechnet. Zudem werden für eine kleine Gruppe von "Grundwörtern", z.B. die Grundfarben "rot", "blau", "grün", deren Anteile an den Romanen berechnet.

2.) In einem zweiten Schritt werden Informationen zur Redewiedergabe berücksichtigt. In fiktionalen Erzähltexten spricht nicht nur der Erzähler, sondern auch die Figuren. Mithilfe des Redewiedergabe-Taggers (https://github.com/redewiedergabe/tagger) lassen sich vier verschiedene Redewiedergabe-Typen in Romanen annotieren. Die hier untersuchten Romane wurden mit dem Redewiedergabe-Tagger getaggt. Der Romantext, der nicht in eine der Redewiedergabe-Kategorien fällt wurde als Erzählertext gewertet. Anschließend wurden die Wortfelder zu den Kategorien "konkret" und "abstrakt" zusammengefasst und für beide Gruppen der Anteil am jeweiligen Redewiedergabe-Typ pro Roman berechnet. 

3.) Um Kandidaten zu identifizieren, die sich für ein an die quantitative Analyse anschließendes Close Reading eignen, wurden die Romane mit den höchsten bzw. niedrigsten Werten bei konkreten und abstrakten Wörtern ausgegeben.

### count_concreteness_scores



