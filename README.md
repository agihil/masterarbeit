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



