# KI-basierter Persönlichkeitstest

Dieses Projekt implementiert einen KI-basierten Persönlichkeitstest, der basierend auf benutzerdefinierten Fragen und Antworten Kategorien wie "Empath", "Soziopath", "Extravertiert" usw. vorhersagt. Die Vorhersage basiert auf maschinellen Lernmodellen, die aus den bereitgestellten Textdaten trainiert wurden.

## Inhalt

- [Überblick](#überblick)
- [Funktionen](#funktionen)
- [Installation](#installation)
- [Verwendung](#verwendung)
- [Datenformat](#datenformat)
- [Trainingsprozess](#trainingsprozess)
- [Spielprozess](#spielprozess)
- [Beitragende](#beitragende)
- [Lizenz](#lizenz)

## Überblick

Dieses Projekt nutzt zwei maschinelle Lernmodelle:
1. **Kategorisierung**: Ein Klassifikationsmodell, das basierend auf einer Kombination aus Frage und Antwort eine Kategorie vorhersagt.
2. **Gewichtungsbestimmung**: Ein Regressionsmodell, das eine Gewichtung vorhersagt, die angibt, wie stark die Antwort mit der vorhergesagten Kategorie verbunden ist.

## Funktionen

- **Zufällige Frageauswahl**: Bei jedem Start des Spiels werden zufällige Fragen aus einer CSV-Datei ausgewählt.
- **Benutzereingabe**: Der Benutzer kann Antworten aus einer Auswahl von möglichen Antworten für jede Frage wählen.
- **Kategorievorhersage**: Die Modelle sagen eine Kategorie basierend auf der Eingabe des Benutzers voraus.
- **Gewichtungsbewertung**: Die Gewichtung jeder Antwort wird berechnet und summiert, um die finale Kategorie des Benutzers zu bestimmen.

## Installation

1. Klone das Repository:

   ```bash
   git clone https://github.com/kruemmel-python/KI-basierter-Pers-nlichkeitstest.git
   cd dein-repo
