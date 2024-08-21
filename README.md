Hier ist eine ausführliche README.md für dein Projekt, basierend auf den Ergebnissen, die du bereitgestellt hast. Diese Datei dokumentiert das Projekt umfassend und bietet sowohl technische Details als auch Einblicke in die Ergebnisse.

```markdown
# Persönlichkeitsanalyse Quiz

## Einführung

Dieses Projekt implementiert ein interaktives Persönlichkeitsanalyse-Quiz, das mithilfe von maschinellem Lernen entwickelt wurde. Ziel ist es, basierend auf den Antworten der Benutzer eine passende Persönlichkeitskategorie zuzuordnen. Die Kategorien umfassen: **Empath**, **Extravertiert**, **Hochsensibel**, **Introvertiert**, **Narzisst** und **Soziopath**. Die Klassifizierung erfolgt durch den Einsatz mehrerer Algorithmen wie Random Forest, Gradient Boosting und Ridge Regression.

## Inhaltsverzeichnis

- [Installation](#installation)
- [Daten](#daten)
- [Verwendete Algorithmen](#verwendete-algorithmen)
- [Modelltraining](#modelltraining)
- [Benutzung](#benutzung)
- [Ergebnisse](#ergebnisse)
- [Lizenz](#lizenz)

## Installation

Um das Projekt lokal auszuführen, sind folgende Schritte erforderlich:

1. **Python 3.12** installieren (sicherstellen, dass es auf deinem System installiert ist).
2. Abhängigkeiten installieren:

   ```bash
   pip install pandas numpy scikit-learn joblib
   ```

3. Die CSV-Datei `P_Daten.csv` in das Projektverzeichnis einfügen. Diese Datei sollte die Fragen, Antworten und Kategorien enthalten.

## Daten

Die Eingabedaten werden aus einer CSV-Datei geladen, die die folgenden Spalten enthält:

- **Frage**: Die Fragen, die den Benutzern gestellt werden.
- **Antwort**: Mögliche Antworten zu den Fragen.
- **Kategorie**: Die Kategorie, die mit der Frage verbunden ist.
- **Gewichtung**: Eine Gewichtung, die den Einfluss der Antwort auf die endgültige Kategorisierung angibt.

## Verwendete Algorithmen

- **Random Forest**: Ein Ensemble-Lernalgorithmus, der mehrere Entscheidungsbäume trainiert und deren Vorhersagen aggregiert.
- **Gradient Boosting**: Ein weiterer Ensemble-Algorithmus, der sequentiell Entscheidungsbäume trainiert und dabei Fehler der vorherigen Bäume berücksichtigt.
- **Ridge Regression**: Ein Regressionsansatz, der Regularisierung zur Vermeidung von Überanpassung verwendet.

## Modelltraining

Das Modelltraining umfasst folgende Schritte:

1. **Datenaufteilung**: Die Daten werden in Trainings- und Testsets unterteilt.
2. **Pipeline-Erstellung**: Für jeden Algorithmus wird eine Pipeline erstellt, die einen TfidfVectorizer zur Merkmalsextraktion und den entsprechenden Klassifikator umfasst.
3. **Hyperparameteroptimierung**: Mit RandomizedSearchCV werden die besten Hyperparameter für jeden Klassifikator gefunden.
4. **Ensemble-Modell**: Ein VotingClassifier kombiniert die besten Modelle von Random Forest und Gradient Boosting.

### Ergebnisse des Modelltrainings

Nach dem Training wurden die Modelle evaluiert und die Ergebnisse dokumentiert. Hier sind die wichtigsten Metriken für die Kategorisierung:

#### Random Forest
```
               precision    recall  f1-score   support

       Empath       0.67      0.67      0.67         9
Extravertiert       0.60      0.82      0.69        11
 Hochsensibel       0.62      1.00      0.76         8
Introvertiert       1.00      0.15      0.27        13
     Narzisst       0.55      0.75      0.63         8
    Soziopath       0.90      0.82      0.86        11

     accuracy                           0.67        60
    macro avg       0.72      0.70      0.65        60
 weighted avg       0.75      0.67      0.63        60
```

#### Gradient Boosting
```
               precision    recall  f1-score   support

       Empath       0.56      0.56      0.56         9
Extravertiert       0.80      0.73      0.76        11
 Hochsensibel       0.75      0.75      0.75         8
Introvertiert       0.78      0.54      0.64        13
     Narzisst       0.58      0.88      0.70         8
    Soziopath       0.83      0.91      0.87        11

     accuracy                           0.72        60
    macro avg       0.72      0.73      0.71        60
 weighted avg       0.73      0.72      0.71        60
```

#### Ensemble-Modell
```
               precision    recall  f1-score   support

       Empath       0.56      0.56      0.56         9
Extravertiert       0.80      0.73      0.76        11
 Hochsensibel       0.75      0.75      0.75         8
Introvertiert       0.78      0.54      0.64        13
     Narzisst       0.58      0.88      0.70         8
    Soziopath       0.83      0.91      0.87        11

     accuracy                           0.72        60
    macro avg       0.72      0.73      0.71        60
 weighted avg       0.73      0.72      0.71        60
```

#### Confusion Matrix für das Ensemble-Modell
```
[[ 5  2  1  0  1  0]
 [ 0  8  1  0  2  0]
 [ 0  0  6  2  0  0]
 [ 2  0  0  7  2  2]
 [ 1  0  0  0  7  0]
 [ 1  0  0  0  0 10]]
```

#### Gewichtung
- **MSE (Mean Squared Error)**: 0.1663

### Fehlklassifikationen
Die folgenden Fragen wurden falsch klassifiziert:

| Frage                                                                 | Tatsächliche Kategorie | Vorhergesagte Kategorie |
|-----------------------------------------------------------------------|-----------------------|-------------------------|
| Wie reagierst du, wenn dir jemand im Weg steht...?                   | ...                   | Falsch                  |
| Wie fühlst du dich, wenn du eine schwierige Aufgabe erledigen musst? | ...                   | Falsch                  |
| Wie fühlst du dich, wenn du eine neue Fähigkeit erlernst?           | ...                   | Falsch                  |
| ...                                                                   | ...                   | ...                     |

## Benutzung

Um das Quiz zu starten, führe das folgende Skript aus:

```bash
python quiz.py
```

Das Skript wird die Benutzer auffordern, Fragen zu beantworten und die Vorhersagen basierend auf den eingegebenen Antworten zurückgeben. Nach Beendigung des Quiz wird die entsprechende Kategorie zusammen mit einer Beschreibung angezeigt.

## Lizenz

Dieses Projekt ist unter der MIT-Lizenz lizenziert. Sie können die Lizenzdetails in der `LICENSE`-Datei einsehen.

---

Für weitere Informationen oder Anfragen wenden Sie sich bitte an den Autor des Projekts.
```

### Hinweise zur README.md
1. **Einführung**: Erläutert den Zweck des Projekts und die verschiedenen Persönlichkeitskategorien.
2. **Installation**: Detaillierte Anweisungen zur Einrichtung des Projekts.
3. **Daten**: Informationen zur Struktur und den Inhalten der verwendeten CSV-Datei.
4. **Verwendete Algorithmen**: Erläuterungen der verwendeten Algorithmen.
5. **Modelltraining**: Beschreibung der Schritte und der Ergebnisse, einschließlich der wichtigsten Metriken für jeden Klassifikator.
6. **Ergebnisse**: Detaillierte Ergebnisse der Modelle, einschließlich Klassifikationsberichte und Fehlklassifikationen.
7. **Benutzung**: Anweisungen zum Starten des Quiz.
8. **Lizenz**: Informationen zur Lizenzierung des Projekts.

Diese README.md sollte den Benutzern helfen, das Projekt zu verstehen, es zu installieren und die Ergebnisse zu interpretieren.
