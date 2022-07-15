# Ogólne
## Zwykły merge vs squash commit vs fast forward - czym się różnią? jaka jest różnica w mergowaniu brancha przez merge vs rebase?

Squash merge różni się od zwykłego merge'a tym że "squashuje" commity, tzn. łączy commity z brancha, na którym pracuje developer, w jeden commit. Jeśli historia commitów może być łatwiej zrozumiana poprzez jeden spójny commit to towinno się używać squash merge aby poprawić czytelność dla innych developerów.

Fast-forward to domyślna akcja podczas merge'a, gdy historia brancha mergującego (czyli zwykle dev albo master) nie zmieniła się w stosunku do brancha mergowanego (np. feature). Fast-forward (czyli przesunięcie pointera HEAD do przodu) wykonuje się kiedy historia gałęzi scalowanej (np. master) nie ma rozgałęzień od gałęzi scalującej (np. feature).

# Backend
## Autoloading klas - jak to działa w PHPie? jak działa najpopularniejszy autoloader wbudowany w composera? na jakiej zasadzie ładuje to klasy?

Autoloader w PHPie pozwala na używanie klasy bez obowiązku uprzedniego załadowania jej (require className / include). Zasada działania autoloadera jest prosta - jest to funkcja która bierze nazwę klasy oraz ładuje plik z jej nazwą.

Konfiguracje autoloadera z composera konfiguruje się w composer.json pod kluczem PSR-4 tak jak w poniższym przykładzie

```json
{
    "autoload": {
        "psr-4": {
            "MyAppName\\": "src/"
        }
    }
}
```