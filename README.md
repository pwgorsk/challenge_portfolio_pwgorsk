# TASK 6
### Subtask 1
#### 11. Popełniłam błąd wpisując nazwisko Ani Miler – wpisałam Muler. Znajdź i zastosuj funkcję, która poprawi mój karkołomny błąd

UPDATE customers SET surname='Miler' WHERE customer_id='3'

![image](https://user-images.githubusercontent.com/121874446/220212832-d337f83a-0068-4cff-82fe-d0cb0c8ec0b8.png)

#### 12. Pobrałam za dużo pieniędzy od klienta, który kupił w ostatnim czasie film o id 4. Korzystając z funkcji join sprawdź, jak ma na imię klient i jakiego ma maila.

SELECT * FROM `sale` JOIN customers WHERE movie_id=4;

![image](https://user-images.githubusercontent.com/121874446/220454534-7afed0b8-ff4d-48f7-a78d-0a62bb654ea9.png)

#### 13. Na pewno zauważył_ś, że sprzedawca zapomniał wpisać emaila klientce Patrycji. Uzupełnij ten brak wpisując: pati@mail.com

UPDATE customers SET email='pati@mail.com' WHERE customer_id='4';

![image](https://user-images.githubusercontent.com/121874446/220454901-8b486e0d-3540-42eb-8e59-ec42300ead66.png)

#### 14. Dla każdego zakupu wyświetl, imię i nazwisko klienta, który dokonał wypożyczenia oraz tytuł wypożyczonego filmu.

SELECT * FROM `sale` INNER JOIN customers, movies;

![image](https://user-images.githubusercontent.com/121874446/220455209-ae178860-1d60-4b17-980c-ffa6c88acc84.png)

#### 15. W celu anonimizacji danych, chcesz stworzyć pseudonimy swoich klientów. - Dodaj kolumnę o nazwie ‘pseudonym’ do tabeli customer,- Wypełnij kolumnę w taki sposób, aby pseudonim stworzył się z dwóch pierwszych liter imienia i ostatniej litery nazwiska.

UPDATE customers SET pseudonim = concat(LEFT(name,2),RIGHT(surname,1));

#### 16. Wyświetl tytuły filmów, które zostały zakupione, wyświetl tabelę w taki sposób, aby tytuły się nie powtarzały. 

SELECT DISTINCT title FROM movies JOIN sale ON movies.movie_id = sale.movie_id

![image](https://user-images.githubusercontent.com/121874446/220769358-a0e4a659-130a-4e06-84eb-7ef652c2525a.png)


#### 17. Wyświetl wspólną listę imion wszystkich aktorów i klientów, a wynik uporządkuj alfabetycznie. 

SELECT name FROM `actors` UNION SELECT name FROM customers order by name;

![image](https://user-images.githubusercontent.com/121874446/220767795-396ef362-8347-4e81-8a40-e67a35428ca7.png)

#### 18. Polskę opanowała inflacja i nasz sklepik z filmami również dotknął ten problem. Podnieś cenę wszystkich filmów wyprodukowanych po 2000 roku o 2,5 $

UPDATE movies SET price = price + 2.5 WHERE year_of_production >= 2000;

![image](https://user-images.githubusercontent.com/121874446/220768510-8de946c6-fe0a-4ff1-bf43-028cba1947df.png)

#### 19. Wyświetl imię i nazwisko aktora o id 4 i tytuł filmu, w którym zagrał

SELECT name,surname,title from actors JOIN cast ON actors.actor_id = cast.actor_id JOIN movies ON cast.movie_id = movies.movie_id WHERE actors.actor_id = 4;

![image](https://user-images.githubusercontent.com/121874446/220769213-095ba429-2a25-43ba-99ba-dfc6d1956aca.png)

#### 20.  A gdzie nasza HONIA!? Dodaj do tabeli customers nową krotkę, gdzie customer_id = 7, name = Honia, surname = Stuczka-Kucharska, email = honia@mail.com oraz pseudonym = Hoa

INSERT INTO customers VALUES ('7','Honia','Stuczka-Kucharska','honia@mail.com','Hoa');

![image](https://user-images.githubusercontent.com/121874446/220770332-02a9022d-4f7b-4555-8a7b-6786d64c2e43.png)


### SUBTASK 2

![image](https://user-images.githubusercontent.com/121874446/220773429-58f4470b-ca1b-4152-b069-ae28957e0800.png)





# TASK 5
### Subtask 3 
#### 1. Wyświetl tabelę actors w kolejności alfabetycznej sortując po kolumnie surname.
SELECT * FROM actors ORDER BY surname ASC

![image](https://user-images.githubusercontent.com/121874446/219007547-23a5d0f9-77c0-46d3-8f6f-3c1cf0ad5593.png)


#### 2. Wyświetl film, który powstał w 2019 roku.
SELECT * FROM movies WHERE year_of_production = 2019

![image](https://user-images.githubusercontent.com/121874446/219007686-4dc6d6df-2857-4e56-950a-3b9bb85a4d81.png)


#### 3. Wyświetl wszystkie filmy, które powstały między 1900, a 1999 rokiem.
SELECT * FROM movies WHERE year_of_production BETWEEN 1900 AND 1999

![image](https://user-images.githubusercontent.com/121874446/219008032-67ceaec4-7580-48d2-886d-8d6b9eeaa205.png)


#### 4. Wyświetl JEDYNIE tytuł i cenę filmów, które kosztują poniżej 7$
SELECT title, price FROM `movies` WHERE PRICE BETWEEN 0 AND 6.99;

![image](https://user-images.githubusercontent.com/121874446/219008141-632ca7e2-3a63-4fc9-8216-435e01b2c223.png)


#### 5. Użyj operatora logicznego AND, aby wyświetlić aktorów o actor_id pomiędzy 4-7 (4 i 7 powinny się wyświetlać). NIE UŻYWAJ operatora BETWEEN.
SELECT * FROM actors WHERE actor_id > 3 and actor_id <8;

![image](https://user-images.githubusercontent.com/121874446/219008231-c1442417-184b-49c8-a68b-12d616732b0e.png)


#### 6. Wyświetl klientów o id 2,4,6 wykorzystaj do tego warunek logiczny.
SELECT * FROM `customers` WHERE customer_id IN (2, 4, 6)

![image](https://user-images.githubusercontent.com/121874446/219008341-fbf39668-f1e1-4663-92e5-1b25760a5d50.png)


#### 7. Wyświetl klientów o id 1,3,5 wykorzystaj do tego operator IN.
SELECT * FROM `customers` WHERE customer_id IN (1, 3, 5)

![image](https://user-images.githubusercontent.com/121874446/219008436-726e10ff-5c47-4fa7-969f-bae03c92c635.png)

#### 8. Wyświetl dane wszystkich osób z tabeli ‘actors’, których imię zaczyna się od ciągu “An”.
SELECT * FROM `actors` WHERE name LIKE 'An%'

![image](https://user-images.githubusercontent.com/121874446/219008524-0520e307-d981-4c96-a1ad-ddf331b38e48.png)

#### 9. Wyświetl dane klienta, który nie ma podanego adresu email.
SELECT * FROM `customers` where email IS NULL;

![image](https://user-images.githubusercontent.com/121874446/219008601-b54ca49f-2f4f-4e2d-bb77-7af1d67b4231.png)

#### 10. Wyświetl wszystkie filmy, których cena wynosi powyżej 9$ oraz ich ID mieści się pomiędzy 2 i 8 movie_id.
SELECT * FROM `movies` WHERE price >9 AND movie_id BETWEEN 2 and 8

![image](https://user-images.githubusercontent.com/121874446/219008696-997e839e-f6d4-4108-b8da-565a6eab05d5.png)


# TASK 4
### Subtask 1 i 2

[link do dysku google](https://docs.google.com/spreadsheets/d/1SZvqOmj_44TFptxB59WusmoCOqz6dBQIO5-nncD-aDI/edit?usp=sharing)

### Subtask 3
#### Do czego służy ta aplikacja? Jaki jest cel tej aplikacji?
do łączenia osób, które mają coś do zaoferowania, z osobami które czegoś szukają 
#### Kto ma być użytkownikiem końcowym aplikacji?
każda osoba korzystająca z internetu 
#### Czy według Ciebie aplikacja jest user friendly?
tak, jest zaprojektowana intuicyjnie, nie wymaga doświadczenia w korzystaniu z apliakcji i charakteryzuje się dużą łatwością w znalezieniu czego szuka użytkownik_
#### Jak byś usprawnił aplikację? Co byś w niej poprawił. Czy masz jakiś pomysł na dodatkową funkcjonalność?
poprawiłbym sekcję wprowadzania informacji o użytkowniku w sekcji "SZUKAM PRACY", gdzie znalazłem kilka błędów, które opisałem w Subtasku 2 
#### Jakie dostrzegasz różnice pomiędzy testowaniem aplikacji internetowej, a natywnej?
testowanie aplikacji internetowej za pomocą przeglądarki pozwala na więcej możliwości ze względu na narzędzia dla programistów, możliwość sprawdzenia elementów kodu czy np. na możliwość sprawdzenie wersji mobilnej w przeglądarce internetowej, jest mi też łatwiej zapisywać znalezione błędy


===

# TASK 3 
### Subtask 1, Subtask 2, Subtask 3

[link do dysku google](https://drive.google.com/drive/u/1/folders/1722j7Bi5YRtN_7tYAAQVVONHKxvDc8z1)

===

# TASK 2
## Subtask 1 i Subtask 2
[link do dysku google](https://drive.google.com/drive/folders/12LkkA6V8y1uiDD9lDpnKcIwNv79WONsj?usp=sharing)

## Subtask 3
Po co piszemy test case'y? Żeby lepiej ułożyć sobie pracę przy sprawdzaniu czy funkcje działają zgodnie z założeniami, i żeby podczas testowania nie umknął nam żaden szczegół. 


===

# TASK 1

## Subtask 1
9/10

## Subtask 3
witam Was jestem Przemek i chcę nauczyć się czegoś nowego 

## Subtask 4
### Na czym polega ta aplikacja? Do czego służy?

Aplikacja pozwala na wyszukiwanie piłkarzy z bazy danych oraz dodawanie informacji o graczach. 

### Jakie funkcjonalności znajdują się w aplikacji? Do czego służą. Czy są intuicyjne, czy może byś coś zmienił_a? (Nie bój się wyrażać opinię!)

Umożliwia wyszukanie zawodnika po określonych parametrach jak pozycja na boisku, wiek, warunki fizyczne, regionu zamieszkania, klub, poziom rozgrywek na jakim występuje, a później sprawdzenia ich postawy w poszczególnych meczach. 
Badana strona umożliwia też samodzielne dodawanie nowych zawodników oraz raportów o meczach, w których brali udział. 

Rzuca się w oczy przede wszystkim niezrozumiale zaprojektowana strona główna z bardzo dużą ilością niezagospodarowanego miejsca. 
Nie rozumiem też osobny sekcji „Mecze” i „Raporty”, które mogłyby zostać połączone w jeden moduł, skoro obie sekcje dotyczą relacji z przebiegu meczu i postawy danego zawodnika. Pracę użytkowników strony może utrudniać brak możliwości filtrowania wyników wyszkiwania na podstawie daty meczu/raportu czy drużyny przeciwnika. 
Niedopracowana jest sekcja wyszukiwania piłkarzy – rzuca się w oczy brak filtrowania zawodników po dacie dodania do aplikacji. 
Brak możliwości dodania nowego zawodnika w sekcji „Gracze”, jedynie możliwość wprowadzenia poprzez stronę główną.
Również rzuca się w oczy brak możliwości usunięcia danego gracza i raportu z bazy, można jedynie edytować istniejące dodane pozycje.

### Oceń interfejs aplikacji (wygląd) – czy Ci się podoba, czy nie?

Strona nie zachwyca, jest niedopracowana, mało wyróżniająca się i wygląda na będącą ciągle w budowie głównie przez niezagospodarowane miejsce na stronie.
Kolorystyka aplikacji jest monotonna, a również subiektywnie, brakuje mi charakterystycznych elementów wskazujących, że mamy do czynienia z aplikacją piłkarską, typu piłki, buty, boisko itd.

### Czy aplikacja jest intuicyjna? (Intuicyjna, czyli np. nie masz problemu ze zrozumieniem, co należy kliknąć, żeby wejść do formularza dodawania nowego zawodnika piłki nożnej do systemu).

Poruszanie się po aplikacji nie sprawia problemów.

### Czy zauważasz jakieś błędy? Albo coś wydaje Ci się błędem? Zapisz swoje przemyślenia w pliku. Tutaj masz na to miejsce, czas i przestrzeń! ;)
 
Moduł edycji gracza jest, lekko mówiąc, niedopracowany i zostawia dużo pola dla różnych żartownisiów :) 
W polach „imię”, „nazwisko”, „poziom rozgrywek”, „główna pozycja”, „pozycja alternatywna”  i „osiągnięcia” można wpisać cokolwiek, od liczb, przez znaki interpunkcyjne, po emotikony bez limitu znaków, przez co nie da się efektywnie korzystać z wyszukiwania bazy danych.

Można wpisać datę urodzenia zawodnika w przyszłości lub dalekiej przeszłości, wagę mniejszą niż 0. W polu wzrost wprawdzie nie ma możliwości wpisania go mniejszego niż 0, natomiast jest możliwość wprowadzenia formuły „9e+23” czy liczby „700000000 cm”.

Załączniki:


https://user-images.githubusercontent.com/121874446/213018011-7e378ce8-cdeb-4c27-bf22-a57e580f8313.mp4

![ronal Bez tytułu](https://user-images.githubusercontent.com/121874446/213018044-06cdbf30-f485-4a9f-8184-4566e91a1728.png)

![wqielk](https://user-images.githubusercontent.com/121874446/213018133-f6ad3163-067c-48f8-9ef9-99ac9377639d.png)


Podobnie sytuacja wygląda w oknach „Mecze” i „Raporty”, można wpisać każdą wartość w pola nazwy drużyn zawodnika i przeciwnika oraz nazwy ligi. 
W raporcie meczu można wyklikać nieograniczoną liczba połów danego meczu


https://user-images.githubusercontent.com/121874446/213017779-e2194b14-2d4b-4453-bfea-8c5e4b03bc3c.mp4

https://user-images.githubusercontent.com/121874446/213017784-b4f9cc95-2b85-486b-a856-80bbc922117c.mp4


Sekcje "Mecze" i "Raporty" są niedostosowane do urządzeń mobilnych, przykłady:


https://user-images.githubusercontent.com/121874446/213022131-fceb2790-fb70-47ee-af0e-6166b8114674.mp4

https://user-images.githubusercontent.com/121874446/213022147-5d864856-866b-498a-a3eb-f86db72c8372.mp4

