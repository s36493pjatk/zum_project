# Dziennik eksperymentów

## Wpis: DummyClassifier

* Data: 2026-11-12
* Zadanie: 2
* Poziom: A — trivial baseline
* Cel albo hipoteza: Punkt odniesienia ignorujący treść nazw produktów.
* Reprezentacja i preprocessing: Brak.
* Model i hiperparametry: `DummyClassifier(strategy="most_frequent")`.
* Co jest zamrożone, a co trenowane: Podział danych jest stały. Model ustala najczęstszą klasę na train.
* Sposób wyboru hiperparametrów: Brak strojenia.
* Seed: 42 (seed eksperymentu; strategia modelu jest deterministyczna).
* Wynik na validation: macro-F1 = 0.0273, accuracy = 0.1581, weighted-F1 = 0.0432.
* Koszt: Trening 0.0111 s, CPU (Darwin arm64). Pamięci nie mierzono.
* Pliki z wynikami w `results/`: `validation/dummy_metrics.json`, `validation/dummy_predictions.csv`.
* Commit: Wersja oznaczona tagiem `task-2`.
* Wnioski: Przewidywanie najczęstszej klasy daje bardzo niski macro-F1.

## Wpis: TF-IDF + Logistic Regression

* Data: 2026-11-12
* Zadanie: 2
* Poziom: A
* Cel albo hipoteza: Sprawdzenie, jak dobrze klasyczny model rozpoznaje kategorie na podstawie nazw produktów.
* Reprezentacja i preprocessing: TF-IDF, n-gramy słów (1, 2), `min_df=2`, `lowercase=True`, tokeny jednoznakowe i dłuższe. Bez usuwania stop words i liczb. TF-IDF dopasowany wyłącznie na train.
* Model i hiperparametry: `LogisticRegression(max_iter=1000, random_state=42)`, pozostałe parametry domyślne. Całość w `Pipeline`.
* Co jest zamrożone, a co trenowane: Stały podział danych; TF-IDF i Logistic Regression dopasowane tylko na train.
* Sposób wyboru hiperparametrów: Jeden ustalony wariant, bez strojenia na validation.
* Seed: 42.
* Wynik na validation: macro-F1 = 0.9627, accuracy = 0.9623, weighted-F1 = 0.9623.
* Koszt: Trening całego pipeline'u 1.1664 s, CPU (Darwin arm64). Pamięci nie mierzono.
* Pliki z wynikami w `results/`: `validation/tfidf_lr_metrics.json`, `validation/tfidf_lr_predictions.csv`, `validation/tfidf_lr_confusion_matrix.csv`, `validation/tfidf_lr_confusion_matrix.png`, `validation/tfidf_lr_errors.csv`.
* Commit: Wersja oznaczona tagiem `task-2`.
* Wnioski: Model osiągnął znacznie lepszy wynik od DummyClassifier. Popełnił 131 błędów na 3479 przykładach validation. Problemy pojawiały się między podobnymi kategoriami i przy tytułach zawierających głównie oznaczenia modeli.
