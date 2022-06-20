## Ogólne
Jakie pliki powinny znaleźć się w repozytorium, a jakie zawsze wrzucamy do .gitignore?

W przypadku Laravela najważniejsze pliki jakie zwykle wrzuca się do .gitignore to:
- .env
- node_modules/ - dla paczek od npm
- vendor - folder który zawiera dependencies Composera
- storage/app/logs - folder z logami  

Zwykle są też ustalone foldery które wrzuca się do .gitignore specyficzne dla danej wersji frameworka projektu (np. dla Laravel 5: Homestead.json i Homestead.yaml)

Oraz jeśli IDE to PHPStorm lub VSCode należy również dodać:
- .idea
- .vscode

Laravel generuje domyślny plik .gitignore podczas tworzenia projektu.

## Backend
Czym jest UUID? jakie ma wady/zalety względem zwykłych autoincremental IDków?

UUID to identifier który do generowania id używa timestamp or adresu sieci użytego podczas kreacji. Wielkość tego id to 128 bit, czyli jest spory. Zaletą używania UUID jest to że można go użyć do identyfikacji np. rzędu w bazie danych i mieć pewność że będzie unikalny. Jego unikalność jest tak duża że UUID używane przez różne, niepowiązane firmy mogą być złączone (np. w projekcie) bez obawy o konfilkt/duplikację.

### Wady, zalety UUID w porównaniu z AI ID
> Standardowe formaty używane do tworzenia id to integers (autoincremental) lub slugs (new_orders_status). Używalibyśmy UUID zamiast id gdybyśmy potrzebowali upewnić się że id użyte  jest unique i nie powtórzy się gdy np. inny projekt który dołączamy do aktualnego ma referencje do tej samej bazy danych (unique across applications). Minusem jest większe zużycie > pamięci, aczkolwiek nie jest to znaczący factor w aktualnych projektach webowych. Wydaje mi się też że problemem mogłaby być czytelność UUID podczas debugowania w porównaniu z czytelniejszym, tradycyjnym ID.