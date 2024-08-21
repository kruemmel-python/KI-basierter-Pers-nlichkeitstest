# KI-basierter Persönlichkeitstest

Hier ist eine Beispiel-README.md für dein Projekt, die die wichtigsten Informationen, Funktionen und Anweisungen enthält. Diese README-Datei bietet eine umfassende Einführung in das Projekt und dessen Verwendung.

```markdown
# Persönlichkeitsanalyse Quiz

Dieses Projekt implementiert ein Persönlichkeitsanalyse-Quiz mithilfe von maschinellem Lernen. Es nutzt verschiedene Klassifikationsalgorithmen, um die Antworten der Benutzer zu analysieren und ihnen eine passende Persönlichkeitskategorie zuzuteilen.

## Inhaltsverzeichnis

- [Einführung](#einführung)
- [Installation](#installation)
- [Daten](#daten)
- [Verwendete Algorithmen](#verwendete-algorithmen)
- [Modelltraining](#modelltraining)
- [Benutzung](#benutzung)
- [Ergebnisse und Auswertung](#ergebnisse-und-auswertung)
- [Lizenz](#lizenz)

## Einführung

Das Ziel dieses Projekts ist es, ein interaktives Quiz zu erstellen, das die Benutzer anhand ihrer Antworten einer bestimmten Persönlichkeitskategorie zuordnet. Die Kategorien sind: Empath, Extravertiert, Hochsensibel, Introvertiert, Narzisst und Soziopath. Die Algorithmen, die für die Klassifizierung verwendet werden, umfassen Random Forest, Gradient Boosting und Ridge Regression.

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

- `Frage`: Die Fragen, die den Benutzern gestellt werden.
- `Antwort`: Mögliche Antworten zu den Fragen.
- `Kategorie`: Die Kategorie, die mit der Frage verbunden ist.
- `Gewichtung`: Eine Gewichtung, die den Einfluss der Antwort auf die endgültige Kategorisierung angibt.

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

### Beispielcode für das Training:

```python
# Daten einlesen
df = pd.read_csv('P_Daten.csv')

# Aufteilen in Trainings- und Testdaten
X_train, X_test, y_train_category, y_test_category, y_train_weight, y_test_weight = train_test_split(
    X, y_category, y_weight, test_size=0.2, random_state=42
)

# Pipeline für Random Forest
pipeline_category_rf = Pipeline([...])

# Training für Random Forest
random_search_rf.fit(X_train, y_train_category)

# Ensemble-Modell
voting_clf.fit(X_train, y_train_category)
```

## Benutzung

Um das Quiz zu starten, führe das folgende Skript aus:

```bash
python quiz.py
```

Das Skript wird die Benutzer auffordern, Fragen zu beantworten und die Vorhersagen basierend auf den eingegebenen Antworten zurückgeben. Nach Beendigung des Quiz wird die entsprechende Kategorie zusammen mit einer Beschreibung angezeigt.

## Ergebnisse und Auswertung

Nach dem Training der Modelle wird eine Klassifikationsauswertung durchgeführt. Die Ergebnisse umfassen:

- **Klassifikationsberichte**: Zeigen die Präzision, den Recall und die F1-Score für jede Kategorie.
- **Konfusionsmatrix**: Bietet eine visuelle Darstellung der Vorhersagen im Vergleich zu den tatsächlichen Werten.

### Beispiel für eine Konfusionsmatrix:

```python
conf_matrix = confusion_matrix(y_test_category, y_pred_category_ensemble)
print(conf_matrix)
```

## Lizenz

Dieses Projekt ist unter der MIT-Lizenz lizenziert. Sie können die Lizenzdetails in der `LICENSE`-Datei einsehen.

---

Für weitere Informationen oder Anfragen wenden Sie sich bitte an den Autor des Projekts.
```

### Hinweise zur README.md
1. **Einführung**: Erläutert den Zweck des Projekts.
2. **Installation**: Anweisungen zur Installation der erforderlichen Abhängigkeiten.
3. **Daten**: Informationen zur Struktur der Eingabedaten.
4. **Verwendete Algorithmen**: Eine kurze Beschreibung der Algorithmen, die in diesem Projekt verwendet werden.
5. **Modelltraining**: Eine Zusammenfassung des Prozesses des Modelltrainings mit Beispielcode.
6. **Benutzung**: Schritte zum Starten des Quiz.
7. **Ergebnisse und Auswertung**: Informationen zur Auswertung der Modelle und zur Anzeige der Ergebnisse.
8. **Lizenz**: Informationen zur Lizenzierung des Projekts.
