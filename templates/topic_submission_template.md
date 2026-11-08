# Zgłoszenie tematu

Odpowiedź mieści się na jednej stronie. Projekt dotyczy nadzorowanej klasyfikacji jednolabelowej: każdy przykład ma dokładnie jedną klasę.

1. Roboczy tytuł: Klasyfikacja kategorii produktów na podstawie ich nazw z wykorzystaniem klasycznych i pretrained metod reprezentacji tekstu.
2. Modalność (tekst, obraz, audio albo dane multimodalne): Tekst.
3. Problem klasyfikacji (co jest klasą i ile jest klas): Celem projektu będzie przypisanie oferty produktu do jednej z 10 kategorii na podstawie pola Product Title. Klasa docelowa znajduje się w kolumnie Category Label. Każdy przykład należy do jednej kategorii.
4. Pytanie eksperymentalne (co chcesz sprawdzić): Czy wykorzystanie pretrained modelu do reprezentacji tekstu da lepsze wyniki klasyfikacji niż klasyczne podejście oparte na TF-IDF?
5. Źródło danych (link): https://archive.ics.uci.edu/dataset/837/product%2Bclassification%2Band%2Bclustering
6. Przybliżona wielkość zbioru: Zbiór zawiera około 35 000 ofert produktów pochodzących od 306 sprzedawców.
7. Lista klas i sposób oznaczenia etykiet: W zbiorze znajduje się 10 klas:
CPUs, Digital Cameras, Dishwashers, Fridge Freezers, Freezers, Fridges, Microwaves, Mobile Phones, TVs oraz Washing Machines. Etykiety są dostępne w kolumnie Category Label.
8. Licencja danych: Creative Commons Attribution 4.0 International (CC BY 4.0).
9. Proponowana jednostka generalizacji: Jednostką generalizacji będzie pojedyncza oferta produktu. Model będzie klasyfikował nowe oferty na podstawie ich tytułów. Przed podziałem danych zostaną sprawdzone duplikaty oraz informacje o grupowaniu produktów, aby ograniczyć ryzyko data leakage.
Aktualizacja po komentarzu prowadzącej: W Zadaniu 1 przyjęto jako jednostkę generalizacji unikalny produkt (Cluster ID), dlatego wszystkie oferty tego samego produktu pozostają w jednym zbiorze.
10. Planowany baseline: Jako baseline zostanie użyty TF-IDF do reprezentacji tekstu oraz Logistic Regression jako klasyfikator. TF-IDF będzie dopasowany tylko na danych treningowych.
11. Wstępny pomysł na model pretrained: Zostanie wykorzystany model typu Sentence Transformer do tworzenia embeddingów tekstu. Otrzymane embeddingi zostaną następnie wykorzystane jako wejście do prostego klasyfikatora, np. Logistic Regression.
12. Potencjalne ograniczenia obliczeniowe: Brak istotnych ograniczeń obliczeniowych.
13. Dane osobowe, wrażliwe albo z ograniczeniami dostępu lub redystrybucji (tak albo nie; jeśli tak, jak je przechowasz): Nie.
