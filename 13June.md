> Storage obiektowy - np. AWS S3 - co to jest i jakie ma korzyści?

Storage obiektowy to metoda przechowywania danych znana również jako obiektowa pamięć masowa.  W tym typie dane są przechowywane w samoistnych obiektach. Obiekty te posiadają unikalny id, który służy do uzyskania dostępu do obiektu.

Inną metodą przechowywania danych, która jest alternatywą dla obiektowej pamięci i jest z nią często porównywana to blokowa pamięć masowa. W tym typie pamięci dane są dzielone (odpowiedzialna za to jest sieć SAN, Storage Area Network), przechowywane w blokach oraz umieszczane w stosunku do siebie w taki sposób, który zapewni największą wydajność.

> Jak byś wyjaśnił 6-latkowi, jak działają kolejki (queue)?

Wyjaśniłbym to na metaforze dużego sklepu z cukierkami:

Wyobraźmy sobie że stoimy w kolejce do kasy. Przed nami stoi pan który ma cały wózek cukierków i każdy z nich jest inny <<czasochłonny proces>>. Wiadomo, że skasowanie go zajmie bardzo długo. Z drugiej strony, Ty i wszystkie pozostałe osoby w kolejce mają tylko garść cukierków, które chcecie kupić. Działanie kolejki w tym przypadku polega na tym, że kasjer zauważa Pana z wózkiem, prosi współpracownika o podejście do kasy i odsyła Pana z wózkiem do nowo otwartej kasy <<sending a process to run in the background>>, aby reszta klientów mogła szybciej kupić cukierki,