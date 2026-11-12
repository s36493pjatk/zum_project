# Analiza artykułu naukowego

## Dane bibliograficzne

* Pełny opis bibliograficzny: Kozareva, Z. (2015). Everyone Likes Shopping! Multi-class Product Categorization for e-Commerce. W: Proceedings of the 2015 Conference of the North American Chapter of the Association for Computational Linguistics: Human Language Technologies, s. 1329–1333. Association for Computational Linguistics.
* DOI albo oficjalny link: https://doi.org/10.3115/v1/N15-1147
* Miejsce publikacji (czasopismo lub konferencja) i rok: NAACL-HLT, 2015
* Źródło z listy akceptowanej automatycznie (tak albo nie): NAACL
* Jeśli nie: data akceptacji przez prowadzącą: -

## Odpowiedzi

Przy każdym twierdzeniu podaj miejsce w artykule (sekcja, tabela albo rysunek). Jeśli autorzy czegoś nie podają, napisz to wprost. Przy każdym pytaniu piszesz od dwóch do pięciu zdań.

### 1. Pytanie badawcze albo główna teza
Autorka chciała sprawdzić, czy da się poprawnie przypisywać produkty do kategorii, mając do dyspozycji tylko ich nazwy. Nie chodziło przy tym o wybór jednej ogólnej kategorii, ale o wskazanie całej ścieżki w hierarchii, która obejmowała 319 kategorii na sześciu poziomach. Sprawdzono więc, czy taki sposób klasyfikacji może działać skutecznie nawet przy krótkich i czasami niejasnych nazwach produktów.

Miejsce w artykule: sekcja 2, s. 1330

### 2. Dane
W eksperymencie wykorzystano 445 408 nazw produktów pochodzących z platformy zakupowej Yahoo!. Do każdej nazwy dwie osoby miały przypisać odpowiednią ścieżkę kategorii, a ich oznaczenia wykorzystano jako poprawne odpowiedzi do oceny modeli. Nie znalazłam jednak informacji, co robiono w sytuacji, gdy te osoby wybrały różne kategorie. To ważne, ponieważ niektóre produkty można przypisać do więcej niż jednej sensownej kategorii.

Miejsce w artykule: sekcja 5, s. 1331

### 3. Jednostka generalizacji i podział danych
Model miał rozpoznawać kategorię nowej nazwy produktu, ale autorka nie określiła dokładnie, czy różne oferty tego samego produktu traktowano jako oddzielne przypadki. Dane podzielono na 353 809 przykładów treningowych i 91 599 testowych, bez wyraźnie opisanego zbioru walidacyjnego. Nie podano też, czy podobne lub identyczne produkty mogły znaleźć się jednocześnie w obu zbiorach. Dlatego nie mogę potwierdzić, czy test był całkowicie niezależny od danych i decyzji wykorzystanych podczas przygotowania modelu.

Miejsce w artykule: sekcja 5, s. 1331

### 4. Baseline i porównanie
Jako punkt odniesienia wykorzystano proste cechy tekstowe, czyli pojedyncze słowa (unigramy) oraz pary kolejnych słów (bigramy). Porównano je z trzema innymi sposobami przedstawienia nazw produktów: słownikiem MI, tematami LDA i embeddingami słów. Każdą reprezentację sprawdzono z dwoma klasyfikatorami (OAA i ECT) na tym samym opisanym podziale danych. Nie wiadomo jednak, czy dla wszystkich metod poświęcono tyle samo pracy na dobór parametrów, co utrudnia ocenę pełnej uczciwości porównania.

Miejsce w artykule: sekcja 4, s. 1330–1331; tabela 1, s. 1332

### 5. Metryki i zmienność wyników
Do oceny użyto F-score (liczonego na zbiorze testowym) przy czym przewidziana kategoria musiała dokładnie zgadzać się z całą poprawną ścieżką. Ma to sens, jeśli system ma przypisywać konkretne kategorie, ale nie uwzględnia sytuacji kiedy model pomyli się tylko na jednym poziomie hierarchii. Najlepszy wynik wyniósł 0,88 i uzyskano go dla embeddingów z klasyfikatorem OAA. Autorka nie podała z ilu uruchomień pochodzą wyniki ani odchyleń standardowych, więc trudno ocenić jak stabilne były różnice między metodami.

Miejsce w artykule: sekcje 6.1–6.2, tabela 1, s. 1332

### 6. Ryzyko metodologiczne
Moim zdaniem ważnym ryzykiem jest możliwość wycieku danych przy tworzeniu słownika MI. Autorka pisze, że do obliczania związku słów z kategoriami wykorzystała wszystkie nazwy produktów, ale nie wyjaśnia czy chodziło wyłącznie o zbiór treningowy. Gdyby do budowania słownika trafiły też etykiety ze zbioru testowego, wynik tej metody mógłby być zawyżony. Nie oznacza to, że tak się stało - po prostu nie da się tego jednoznacznie sprawdzić na podstawie opisu.

Miejsce w artykule: sekcja 4.2, s. 1330

### 7. Mocna strona metodologii
Za mocną stronę uważam to, że autorka nie pokazała tylko jednego najlepszego modelu, lecz porównała kilka reprezentacji tekstu z dwoma klasyfikatorami. Dzięki temu widać, że embeddingi osiągnęły najwyższe wyniki, a OAA wypadał lepiej niż ECT w każdym porównaniu. Ciekawy jest też spadek wyniku z 0,72 do 0,67 po dodaniu bigramów do unigramów w OAA. Pokazuje to, że bardziej rozbudowana reprezentacja nie musi automatycznie poprawiać klasyfikacji.

Miejsce w artykule: tabela 1, s. 1332

### 8. Ograniczenie
Jednym z ograniczeń jest to, że przy ocenie liczyła się tylko dokładna zgodność kategorii z etykietą przypisaną przez człowieka. W analizie błędów pokazano na przykład łóżeczko dziecięce, które model przypisał do bardziej szczegółowej kategorii niż człowiek. Taka odpowiedź została uznana za błędną, mimo że miała sens. Dlatego sam F-score nie pokazuje, jak poważne są poszczególne pomyłki ani czy przewidywanie byłoby przydatne w sklepie.

Miejsce w artykule: sekcje 6.1 i 6.3, rysunek 4, s. 1332

### 9. Czego wynik nie dowodzi
Najlepszy wynik 0,88 nie oznacza, że embeddingi sprawdzą się najlepiej w każdym systemie klasyfikacji produktów. Eksperyment przeprowadzono na danych Yahoo! i jednej konkretnej hierarchii kategorii, a nie na danych z różnych sklepów. Nie pokazano też wyników powtórzonych treningów, więc trudno ocenić czy przewaga embeddingów zawsze byłaby podobna. Można więc powiedzieć, że były najlepsze w tym eksperymencie, ale nie że są najlepszym rozwiązaniem w każdej sytuacji.

Miejsce w artykule: sekcja 5, s. 1331; tabela 1, s. 1332

### 10. Wniosek dla mojego projektu
W projekcie można przetestować słownik MI, który wskazuje słowa szczególnie związane z daną kategorią. W artykule metoda ta osiągnęła 0,85 F-score z klasyfikatorem OAA, czyli więcej niż unigramy (0,72), dlatego warto by było sprawdzić ją również w tym projekcie. Słownik powinien zostać utworzony wyłącznie na danych treningowych, żeby uniknąć wycieku informacji. Następnie wyniki można porównać z modelami TF-IDF i MiniLM na tym samym zbiorze walidacyjnym, korzystając z macro-F1 i pozostawiając zbiór testowy do końcowej oceny.

Miejsce w artykule: sekcja 4.2, s. 1330; tabela 1, s. 1332.

Liczba słów (bez danych bibliograficznych): 840
