# Dziennik eksperymentów

## Wpis: DummyClassifier

* Data: 2026-11-12
* Zadanie: 2
* Poziom: A (trivial baseline)
* Cel albo hipoteza: Punkt odniesienia ignorujący treść nazw produktów.
* Reprezentacja i preprocessing: Brak.
* Model i hiperparametry: `DummyClassifier(strategy="most_frequent")`.
* Co jest zamrożone, a co trenowane: Podział danych jest stały. Model ustala najczęstszą klasę na train.
* Sposób wyboru hiperparametrów: Brak strojenia.
* Seed: 42.
* Wynik na validation: macro-F1 = 0.0273, accuracy = 0.1581, weighted-F1 = 0.0432.
* Koszt: Trening 0.0111 s, CPU (Mac).
* Pliki z wynikami w `results/`: `validation/dummy_metrics.json`, `validation/dummy_predictions.csv`.
* Commit: Wersja oznaczona tagiem `task-2`.
* Wnioski: Przewidywanie najczęstszej klasy daje bardzo niski macro-F1.

## Wpis: TF-IDF + Logistic Regression

* Data: 2026-11-12
* Zadanie: 2
* Poziom: A
* Cel albo hipoteza: Sprawdzenie, jak dobrze klasyczny model rozpoznaje kategorie na podstawie nazw produktów.
* Reprezentacja i preprocessing: TF-IDF z n-gramami słów (1, 2), min_df=2. Bez usuwania stop words i liczb. Dopasowanie tylko na train.
* Model i hiperparametry: `LogisticRegression(max_iter=1000, random_state=42)`, pozostałe parametry domyślne. Całość w `Pipeline`.
* Co jest zamrożone, a co trenowane: Stały podział danych; TF-IDF i Logistic Regression dopasowane tylko na train.
* Sposób wyboru hiperparametrów: Bez strojenia hiperparametrów.
* Seed: 42.
* Wynik na validation: macro-F1 = 0.9627, accuracy = 0.9623, weighted-F1 = 0.9623.
* Koszt: Trening 1.1664 s, CPU (Mac).
* Pliki z wynikami w `results/`: `validation/tfidf_lr_metrics.json`, `validation/tfidf_lr_predictions.csv`, `validation/tfidf_lr_confusion_matrix.csv`, `validation/tfidf_lr_confusion_matrix.png`, `validation/tfidf_lr_errors.csv`.
* Commit: Wersja oznaczona tagiem `task-2`.
* Wnioski: Model uzyskał znacznie lepszy wynik niż DummyClassifier. Popełnił 131 błędów na 3479 przykładach validation. W analizowanych przypadkach błędy mogły wynikać z nazw zawierających głównie markę i kod produktu zamiast opisu urządzenia.

## Wpis: MiniLM + Logistic Regression

* Data: 2026-11-12
* Zadanie: 3
* Poziom: B
* Cel albo hipoteza: Porównanie embeddingów MiniLM z reprezentacją TF-IDF.
* Reprezentacja i preprocessing: Embeddingi MiniLM o 384 wymiarach, mean pooling i normalizacja wektorów.
* Model i hiperparametry: `sentence-transformers/all-MiniLM-L6-v2`, `LogisticRegression(max_iter=1000, random_state=42)`.
* Co jest zamrożone, a co trenowane: Encoder MiniLM jest zamrożony. Logistic Regression jest trenowana wyłącznie na train.
* Sposób wyboru hiperparametrów: Bez strojenia hiperparametrów.
* Seed: 42.
* Wynik na validation: macro-F1 = 0.9695, accuracy = 0.9695, weighted-F1 = 0.9695.
* Koszt: Wczytanie modelu 19.89 s, obliczenie embeddingów train 18.35 s i validation 2.21 s, trening Logistic Regression 0.47 s. CPU (Mac). Szczyt zużycia RAM procesu: 883.2 MB.
* Pliki z wynikami w `results/`: `validation/minilm_lr_metrics.json`, `validation/minilm_lr_predictions.csv`, `validation/minilm_lr_comparison_examples.csv`.
* Commit: Wersja oznaczona tagiem `task-3`.
* Wnioski: MiniLM uzyskał nieco wyższy macro-F1 niż TF-IDF (0.9695 względem 0.9627), ale wymagał więcej czasu obliczeniowego. Poprawił 65 błędów TF-IDF, lecz popełnił też 40 nowych błędów.
