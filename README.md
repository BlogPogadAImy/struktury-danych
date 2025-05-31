# Podstawowe struktury danych w Pythonie – listy, słowniki i zestawy

**Cel artykułu:** W ciągu kilkunastu minut zrozumiesz trzy kluczowe struktury danych Pythona – listy, słowniki i zestawy, tak by następnie móc z nimi pracować i wywołać na nich podstawowe metody.

## Wstęp
Jeśli kiedykolwiek korzystałeś z Javy, C++ lub JavaScript, prawdopodobnie spotkałeś się z konstrukcjami takimi jak `ArrayList`, `HashMap` czy `HashSet`. W Pythonie ich odpowiednikami są kolejno:

- **listy** (`list`)
- **słowniki** (`dict`)
- **zestawy** (`set`)

Gdyby porównać programistów do szefów kuchni, te struktury danych byłyby jak trzy podstawowe noże: każdy służy do innego zadania, ale razem stanowią niezbędne wyposażenie.

## 1. Listy (`list`)

### 1.1 Definicja
Lista to uporządkowana, mutowalna kolekcja elementów tego samego lub różnego typu danych.

### 1.2 Cechy listy
- **Uporządkowana**: Listy zachowują kolejność dodawania elementów.
- **Mutowalna**: Można dodawać (`append()`), usuwać (`remove()`, `pop()`), modyfikować lub zmieniać kolejność elementów.
- **Dowolny typ danych**: Listy mogą zawierać liczby, napisy, inne listy, krotki, słowniki itp.
- **Indeksowanie**: Elementy indeksowane są od `0`.
- **Slicing**: Można pobierać fragmenty listy.
- **Tworzenie**: Nawiasy kwadratowe: `[]`.
- **Pusta lista**: `[]`.

### 1.3 Podstawowe metody

| Metoda                | Opis                                                          | Mutuje oryginał? | Zwraca            |
| --------------------- | ------------------------------------------------------------- | ---------------- | ----------------- |
| `append(x)`           | Dokleja element `x` na koniec                                 | ✔️               | `None`            |
| `extend(iter)`        | Rozszerza listę o elementy z iterowalnego                     | ✔️               | `None`            |
| `insert(i, x)`        | Wstawia `x` na pozycję `i`                                    | ✔️               | `None`            |
| `pop([i])`            | Usuwa i zwraca element pod `i` (domyślnie ostatni)            | ✔️               | Usunięty element  |
| `remove(x)`           | Usuwa pierwsze wystąpienie `x`                                | ✔️               | `None`            |
| `clear()`             | Czyści listę                                                  | ✔️               | `None`            |
| `sort()`              | Sortuje listę in place                                        | ✔️               | `None`            |
| `sorted(list)`        | Wbudowana funkcja – zwraca nową posortowaną listę             | ❌               | Nowa lista        |
| `copy()` lub `list(a)`| Płytka kopia                                                  | ❌               | Kopia listy       |

### 1.4 Kiedy stosować?
- **Gdy kolejność ma znaczenie**, a chcesz łatwo doklejać na koniec: `append()` jest amortyzacyjnie O(1).
- **Szybki odczyt przez indeks**: indeksowanie O(1).
- **Tworzenie bufora lub wyniku z pętli**: list comprehensions są czytelne i zwięzłe.

## 2. Słowniki (`dict`)

### 2.1 Definicja
Słownik to uporządkowana kolekcja par `klucz: wartość`, gdzie klucze są unikalne i niemutowalne, a wartości mogą być dowolnymi obiektami.

### 2.2 Cechy słownika
- **Klucz**: element identyfikujący wartość (np. liczba, ciąg znaków, krotka).
- **Wartość**: dowolny obiekt powiązany z kluczem.
- **Iterowanie**: `keys()`, `values()`, `items()`.
- Od Pythona 3.7 słowniki zachowują kolejność dodawania.
- **Słowniki vs. listy**: słowniki szybkie do odwołań po kluczu, listy do indeksów.
- **Słowniki vs. zestawy**: zestawy przechowują tylko unikalne elementy bez wartości.

### 2.3 Podstawowe metody i ich zachowanie

| Metoda                | Opis                                    | Mutuje oryginał? | Zwraca               |
| --------------------- | --------------------------------------- | ---------------- | -------------------- |
| `d[k] = v`            | Dodaje lub nadpisuje parę               | ✔️               | Wartość `v`          |
| `d.get(k, default)`   | Bezpieczny odczyt                       | ❌               | Wartość lub `default`|
| `d.pop(k[, default])` | Usuwa i zwraca wartość pod `k`          | ✔️               | Wartość lub `default`|
| `d.update(other)`     | Masowe dodanie/aktualizacja             | ✔️               | `None`               |
| `d.keys()`            | Widok kluczy                            | ❌               | Widok iterowalny     |
| `d.values()`          | Widok wartości                          | ❌               | Widok iterowalny     |
| `d.items()`           | Widok par (klucz, wartość)              | ❌               | Widok iterowalny     |
| `d.copy()`            | Płytka kopia                            | ❌               | Kopia słownika       |

### 2.4 Kiedy stosować?
- **Odwzorowanie identyfikator → dane**: dostęp w O(1).
- **Przetwarzanie JSON z API**: naturalnie mapuje się na `dict`.
- **Licznik elementów**: użyj `collections.Counter`.

## 3. Zestawy (`set`)

### 3.1 Definicja
Zestaw to nieuporządkowany, mutowalny typ danych przechowujący unikalne elementy.

### 3.2 Cechy zestawu
- **Nieuporządkowany**: brak gwarancji kolejności.
- **Unikalny**: duplikaty są ignorowane.
- **Mutowalny**: można dodawać i usuwać elementy.
- **Tworzenie**: `{1, 2, 3}` lub `set(iter)`.

### 3.3 Podstawowe metody

| Metoda             | Opis                          | Mutuje oryginał? | Zwraca        |
| ------------------ | ----------------------------- | ---------------- | ------------- |
| `s.add(x)`         | Dodaje `x`                    | ✔️               | `None`        |
| `s.update(iter)`   | Dodaje elementy z iter        | ✔️               | `None`        |
| `s.remove(x)`      | Usuwa `x`, KeyError gdy brak  | ✔️               | `None`        |
| `s.discard(x)`     | Usuwa `x`, jeśli jest         | ✔️               | `None`        |
| `s.pop()`          | Usuwa i zwraca losowy element | ✔️               | Usunięty elem.|
| `s.union(t)`       | Suma zbiorów                  | ❌               | Nowy `set`    |
| `s.intersection(t)`| Część wspólna                 | ❌               | Nowy `set`    |
| `s.difference(t)`  | Różnica (`s - t`)             | ❌               | Nowy `set`    |

### 3.4 Kiedy używać?
- **Test przynależności** (`x in s`), operacja O(1).
- **Usuwanie duplikatów** z listy: `list(set(my_list))`.
- **Analiza relacji**: wspólni obserwujący `followers_a & followers_b`.

## 4. Typowe błędy początkującego
- **Kopiowanie przez referencję**: `b = a` to nie kopia – użyj `.copy()` lub konstruktora.
- **Mutowalne wartości w `dict`**: inicjuj listy osobno lub użyj `defaultdict`.
- **Niehashowalne klucze**: lista jako klucz (`d[[1,2]]`) – użyj krotki.

## Podsumowanie
Poznałeś trzy najważniejsze struktury danych w Pythonie i podstawowe metody ich przetwarzania.

## Co dalej?
1. Wydrukuj ten plik i miej go pod ręką.
2. Przejdź do środowiska (np. Colab) i wykonaj kilka ćwiczeń.
3. Zgłębiaj pętle i instrukcje warunkowe.
