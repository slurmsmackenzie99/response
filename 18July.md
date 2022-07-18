## Ogólne: Jaka jest różnica pomiędzy uwierzytelnianiem i autoryzacją? Jakie metody uwierzytelniania API Znasz?
### Uwierzytelnianie a autoryzacja
Uwierzytelnianie to proces sprawdzania danych dostępu użytkownika lub aplikacji - czy jest tym kimś za kogo się podaje. Autoryzacja to proces sprawdzania oraz nadawania uprawnień do wykonywania działań przez użytkownika/aplikację.
### Metody uwierzytelniania API
Znam dwie metody uwierzytelniania API, obydwie korzystają z JSON Web Tokens (JWT), ale zasada ich działania oraz poziom bezpieczeństwa są różne.

- API key - metoda ta polega na wysłaniu do API requesta zawierającego tzw. bearer token, czyli zwykle długiego list of characters które po zweryfikowaniu dadzą aplikacji informację o tym że request pochodzi od aplikacji lub użytkownika, któremu został przyznany dostęp. Z [dokumentu Google'a o tym czym są i kiedy używać API Keys](https://cloud.google.com/endpoints/docs/openapi/when-why-api-key) wiemy że API Keys nie powinny być używane do:

    - Identyfikacji pojedyńczych użytkowników — API keys don't identify users, they identify projects.

    - Bezpiecznej autoryzacji.
> API Key nie jest aktualnie uważane za bezpieczny sposób autoryzacji, a osoba która przechwyci klucz ma dostęp do informacji przez cały czas ważności tokenu (a te są grantowane na indefinite time)
- OAuth 2.0 - standard autoryzacji API na dziś dzień, OAuth 2.0 uwierzytelnia użytkownika oraz przyznaje mu odpowiedni zakres dostępu korzystając z third-party services, ta metoda różni się od API Key / Access token poziomem złożoności oraz rozdzieleniem strony uwierzytelniającej na *resource server* oraz *authorization server* aby podczas uwierzytelniania klient nie miał dostępu do warstwy aplikacji z danymi do których nie ma dostępu
<img src="https://i.imgur.com/7yGtMfF.png" width="1000" height="600" />

##### A co to JWT?
<img src="https://i.imgur.com/1Drmkr8.png" width="1000" height="600" />

JWT to token używający (zwykle) RSA encryption to zakodowania poufnych danych.

## Front: Priorytet stylów CSS. Opisz zagadnienie oraz wymień kilka przykładów stylów od najmniejszego do najwiekszego priorytetu
Priorytety stylów CSS są następujące
1. Inline CSS - inside html elements - overrides all other CSS
   
```html
<h1 style="color:red;text-align:left;">To jest nagłówek</h1>
```

2. CSS w <head> section
   
```html
<head><style>
h1 {
  color: orange;
}
</style></head>
```

3. External CSS
   
```html
<head>
<link rel="stylesheet" href="external.css">
</head>
```

## Backend: Czym są metody magiczne w PHP? wymień 3 i opisz ich działanie?

Magiczne metody w PHP to zarezerwowane funkcje, zaczynające się od dwóch underscores "__", które wywoływane są podczas niektórych działań na klasie takich jak `__construct()` (konstruktor klasy tworzony przy tworzeniu nowego obiektu klasy) oraz `__destruct()` (wywoływany gdy nie ma już referencji do danej klasy). Te dwie metody zawsze muszą być deklarowane jako `public` inaczej wywala błędy. A destructor (z manuala PHP) wywoływany jest gdy: 
> The PHP manual states "the destructor method will be called as soon as all references to a particular object are removed"

Sprawdziłem jakie są najczęściej używane magic methods w PHP:
<img src="https://www.exakat.io/wp-content/uploads/2019/09/magic_method.stats_-1024x594.png" width="1000" height="600" />
Jako trzecia magic method opiszę `toString()` , która jest drugą najpopularniejszą wg. wyższego diagramu. 
> `toString()` pozwala zdecydować developerowi jak zachowa się klasa gdy będzie traktowana jako string (np. przy użyciu na niej `echo`)
Przykładowo:
```php
class PrzykładowaKlasa{
    public $foo;
    public function __construct($foo){
        $this->foo = $foo;
    }
    public function __toString(){
        return $this->foo
    }
}

class $obiekt = new PrzykładowaKlasa('Hello World');
echo $obiekt 
```
da nam output:
```
Hello World
```