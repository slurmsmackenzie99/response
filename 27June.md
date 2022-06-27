# SOLID Principles
## S - Single Responsibility Principle

TLDR: Funkcja ma mieć jasno określony cel działania 

Klasa i funkcja powinny być tworzone tylko w jednym określonym celu oraz w myśl zasady "high cohesion and low coupling". To czy "cohesion" jest wysokie czy niskie jest determinowane przez to czy funkcja odpowiada za wiele czy mało. Funkcja, która pełni tylko ściśle określone zadanie ma "high cohesion", a ta która ma szeroki oraz rozproszony zakres ma "low cohesion". "Coupling" opisuje jak łatwo jest ponownie używać klas i modułów. Moduł, który jest wielokrotnie powielany w kodzie jest "low coupling". 

## O - Open / Closed Principle

The code should be open for extension, but closed for modification.

Tą zasadę zrozumiałem na praktycznym przykładzie problemu jaki może się pojawić po stworzeniu API. Załóżmy, że mamy system księgowości zbudowany w Symfony, a jego API jest używane do pobierania faktur przez księgowych. Endpoint ("GET /faktura/{id}/print”) wyświetla fakturę jako JSON. Pewnego dnia klient wymaga aby faktury były również dostępne do pobrania w formacie .csv, tworzę więc nowy endpoint ("GET /faktura/{id}/{format}”) gdzie format to pdf albo csv. Teraz wszyscy używający mojego API do pobierania faktur zmuszeni są wprowadzić zmiany aby korzystać z jego funkcjonalności.

Aby respektować tą zasadę trzeba mieć wiedzę jaka potrzeba rozszerzenia funkcjonalności programu może pewnego dnia nastąpić i poprawnie zaplanować konstrukcję swojego programu.

## L - Liskov Substitution Principle (LSP)

Klasa potomna powinna zachować funkcjonalność klasy macierzystej.

## I - Interface segregation principle (ISP)

Lepiej mieć większą ilość pomniejszych interfejsów z których każdy jest wyspecjalizowany (wywołuje tylko wyspecjalizowane metody), niż jeden generalny interfejs (wywołujący zbędne metody).

## D - Dependecy Inversion Principle

Moduły wysokieko poziomu nie powinny zależeć od modułów niskiego poziomu. Zasada ta zachęca do wydzielania klas.

# Transakcje 

Transakcja to seria operacji wykonywanych jako jedna jednostka na bazie danych. Każda transakcja powinna mieć cztery cechy, określane akronimem ACID.
- (A) Atomic - operacja zostaje wykonana w całości, albo wcale
- (C) Consistency - operacja nie naruszy integralności systemu (dane będą spójne)
- (I) Isolation - operacja, która podczas transakcji w tym samym casie odczytuje i wykonuje komendy na tych samych danych (tych samych tabelach) działa tak samo jak gdyby transakcje były wykonane jedna po drugiej
- (D) Durability - efekt operacji, która została wykonana będzie widoczny nawet podczas krytycznego błędu (np. awarii zasilania)

# Closures
Domknięcia to mechanizm jaki pozwala JavaScriptowi uzyskiwać dostęp do zmiennych funkcji poza jej leksykalnym zakresem.