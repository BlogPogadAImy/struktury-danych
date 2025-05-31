Podstawowe struktury danych w Pythonie – listy, słowniki i zestawy
Cel artykułu: W ciągu kilkunastu minut zrozumiesz trzy kluczowe struktury danych Pythona – listy, słowniki i zestawy tak, by następnie móc z nimi pracować i wywołać na nich podstawowe metody.
Wstęp
Jeśli kiedykolwiek korzystał_aś z Javy, C++ lub JS, prawdopodobnie przewijały się tam takie konstrukcje jak ArrayList, HashMap czy HashSet. W Pythonie ich odpowiednikami są kolejno listy, słowniki i zestawy. 
Gdyby porównać programistów do szefów kuchni, to te struktury danych byłyby jak trzy podstawowe noże, których używasz każdego dnia. Jeden z nich jest to warzyw, drugi do mięsa, a trzeci do krojenia chleba – Niby nóż to nóż, ale wybierasz ten, który w danym momencie najlepiej odpowiada Twoim potrzebom.
1. Listy (list)
1.1. Definicja
W Pythonie lista (ang. list) to uporządkowana, mutowalna kolekcja elementów tego samego lub różnego typu danych.
1.2 Cechy listy
Uporządkowana: Listy zachowują kolejność, w jakiej elementy są dodawane. 
Modyfikowalna (mutowalna): Można dodawać (np. za pomocą metody append()), usuwać (np. remove(), pop()), zmieniać (przypisując nową wartość do indeksu) lub zmieniać kolejność elementów listy. 
Dowolny typ danych: Listy mogą zawierać różne typy danych, np. liczby, napisy, inne listy, krotki, słowniki, obiekty. 
Indeksowanie: Elementy listy są indeksowane, zaczynając od 0. 
Slicing: Można pobierać fragmenty listy (wycinki), używając slicingu. 
Tworzenie: Listy tworzy się używając nawiasów kwadratowych []. 
Puste listy: Pusta lista tworzy się, używając []. 
1.3. Podstawowe metody
Metoda
Opis
Mutuje oryginał?
Zwraca
append(x)
Dokleja element x na koniec
✔️
None
extend(iter)
Rozszerza listę elementami z iterowalnego
✔️
None
insert(i, x)
Wstawia x pod indeks i
✔️
None
pop([i])
Usuwa i zwraca element przed i (domyślnie ostatni)
✔️
Usunięty element
remove(x)
Usuwa pierwsze wystąpienie x
✔️
None
clear()
Czyści listę
✔️
None
sort()
Sortuje in place
✔️
None
sorted(list)
Funkcja wbudowana – zwraca nową posortowaną listę
❌
Nowa lista
copy() lub list(a)
Płytka kopia
❌
Kopia listy

1.3. Kiedy stosować?
Sytuacja
Dlaczego lista?
Kolejność ma znaczenie, a chcesz łatwo doklejać na koniec
Operacja append() jest amortyzacyjnie O(1).
Potrzebujesz szybkiego odczytu przez indeks
Indeksowanie to O(1).
Tworzysz bufor lub wynik z pętli
List comprehensions są super‑czytelne.


2. Słowniki (dict)
2.1. Definicja
W Pythonie słownik (ang. dictionary) to uporządkowana kolekcja par "klucz: wartość", gdzie klucze muszą być unikalne i niezmienne, a wartości mogą być dowolnym obiektem. Słowniki są często używane do przechowywania i odwoływania się do danych za pomocą nazw, a nie indeksów.
2.2 Cechy słownika
Klucz: To element, który służy do identyfikacji wartości. Może być to liczba, ciąg znaków, krotka, ale nie może to być lista.
Wartość: To obiekt przechowywany w słowniku, powiązany z kluczem.
Iterowanie: Można iterować po kluczach, wartościach lub parach klucz-wartość używając keys(), values() i items(). 
Od Pythona 3.7 słowniki zachowują kolejność dodawania (podobnie jak LinkedHashMap w Javie).
Słowniki vs. listy: Słowniki są bardziej efektywne w przypadku, gdy potrzebujesz odwołać się do danych za pomocą unikalnego identyfikatora (klucza), a listy są bardziej odpowiednie, gdy elementy są indeksowane numerami. 
Słowniki vs. zestawy: Zestawy (sets) przechowują tylko unikalne elementy, bez powiązanych wartości, podczas gdy słowniki przechowują pary klucz-wartość. 
2.2. Podstawowe metody i ich zachowanie
Metoda
Opis
Mutuje oryginał?
Zwraca
d[k] = v
Dodaje lub nadpisuje parę
✔️
Wartość v
d.get(k, default)
Bezpieczny odczyt
❌
Wartość lub default
d.pop(k[, default])
Usuwa i zwraca wartość pod k
✔️
Wartość lub default
d.update(other)
Masowe dodanie/aktualizacja
✔️
None
d.keys()
Widok kluczy
❌
Widok – iterowalny
d.values()
Widok wartości
❌
Widok
d.items()
Widok (klucz, wartość)
❌
Widok
d.copy()
Płytka kopia
❌
Kopia słownika

2.4. Kiedy stosować?
Sytuacja
Dlaczego słownik?
Musisz odwzorować identyfikator → dane
Dostęp w O(1) po haszu klucza.
Łapiesz dane z API JSON
Naturalnie odwzorowują się na dict.
Potrzebujesz licznika elementów
Użyj collections.Counter (specjalizacja słownika).

3. Zestawy (ang. set)
3.1. Definicja
W Pythonie zestaw (ang. set) to wbudowany typ danych, który przechowuje nieuporządkowane i unikalne elementy. 
Innymi słowy, zestaw nie pozwala na przechowywanie duplikatów wartości. Jest to jedna z czterech wbudowanych struktur danych służących do przechowywania kolekcji danych, obok list, krotek i słowników. 
3.2 Cechy zestawu
Nieuporządkowany: Elementy w zestawie nie są przechowywane w jakiejś konkretnej kolejności.
Unikalny: Każdy element w zestawie musi być unikalny. Duplikaty są ignorowane.
Zmienny: Zestawy mogą być modyfikowane, czyli można dodawać lub usuwać elementy po utworzeniu. 
Można je tworzyć na kilka sposobów: wykorzystując nawiasy okrągłe, nawiasy klamrowe, konstruktor set().
3.3. Podstawowe metody
Metoda
Opis
Mutuje oryginał?
Zwraca
s.add(x)
Dodaje x
✔️
None
s.update(iter)
Suma z iterowalnym
✔️
None
s.remove(x)
Usuwa x, KeyError gdy brak
✔️
None
s.discard(x)
Usuwa, jeśli jest
✔️
None
s.pop()
Usuwa i zwraca losowy element
✔️
Usunięty element
s.union(t)
Zwraca nowy zbiór – suma
❌
Nowy set
s.intersection(t)
Wspólne
❌
Nowy set
s.difference(t) lub s - t
Różnica
❌
Nowy set

3.4. Kiedy używać?
Sytuacja
Dlaczego zestaw?
Musisz szybko testować przynależność (x in s)
Operacja O(1).
Usuwasz duplikaty z listu
list(set(my_list)) daje unikalne elementy.
Realizujesz logikę „kto obserwuje kogo”
Wspólne obserwacje to followers_a & followers_b.


4. Typowe błędy początkującego
Kopiowanie przez referencję:
b = a to nie kopia danych – użyj a.copy() lub list(a)/dict(a)/set(a).
Mutowalne wartości w dict
Gdy wartością jest lista, inicjuj ją osobno lub użyj defaultdict(list).
Niehashowalne klucze
Lista jako klucz (d[[1,2]] = "x") → TypeError. Użyj niezmiennych typów (tuple).
Podsumowanie
Brawo! Właśnie poznałeś_aś  trzy najważniejsze struktury danych w Pythonie i oraz podstawowe metody ich przetwarzania. 
Co teraz?
Jeśli zdarza Ci się zapomnieć, co robi dana metoda i jaką strukturę wybrać w danej sytuacji, wydrukuj sobie tego PDF-a i powieś w widocznym miejscu.
Przejdź do Colaba, jeszcze przygotowany kod i zrób 3 zadania, aby utrwalić wiedzę.
Przejdź do kolejnego punktu czyli Pętli i instrukcji warunkowych.
