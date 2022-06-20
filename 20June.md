> OpenAPI - czym jest? w czym nam pomaga?

OpenAPI to format w jakim jest opisywane i dokumentowane API. Jest to teraz standard w jakim dokumentowane i rozwijane powinno być RESTful API. Ma ono z góry określoną strukturę co zapewnia szybkość zrozumienia przez różnych deweloperów, poprzez ułatwienie dostępności (zrozumienie działania bez czytania kodu źródłowego). Format w jakim OpenAPI jest pisane to YAML lub JSON. 

Każda poprawna specyfikacja OpenAPI zawiera:
- metadata - informację o API takie jak nazwa, obecna wersja i opis
- servers - ta sekcja zawiera info o URLach serwera API
- paths - opisuje się tutaj poszczególne endpointy, metody HTTP, które mogą być na nich używane oraz jakie informacje są zwracane w odpowiedzi i w jakim formacie
 - parameters - parametry podawane mogą być w URL (/employees/{employeeId}), przez query string (/company?building=headquarters), nagłówki (Header: Value), lub cookies (PHPSESSID: 12345)  
 - responses - statusy odpowiedzi, response body (properties)
- security - używane do opisania jaki rodzaj autentykacji jest obecny (np. OAuth 2 lub API key) 

> Czym w Larvie są Policies? w jaki sposób możemy dzięki nim sprawdzić czy użytkownik jest autoryzowany do pobrania jakiegoś rekordu? Podajcie krótkiego snippeta, jak może działać takie połączenie Policy + FormRequest

Policies w Larvie są używane do autentykacji akcji na danym modelu / resource. Można szybko stworzyć Policy używając komendy php artisan make:policy. Aby sprawdzić czy dany użytkownik jest zautoryzowany do pobrania jakiegoś rekordu możemy w Policy opisać w jakich przypadkach użytkownik jest do tego uprawniony. Mój przykład pokazuje użycie połączenia użycia Policy i FormRequest aby upewnić się że stworzyć nowego użytkownika może tylko Admin, oraz że walidacja zasadami zostanie przeprowadzona przez Form Request. 

in \App\Http\Requests\CreateUserRequest:
```
class CreateUserRequest extends FormRequest
{
    public function rules()
    {
        return [
            'name' => 'required|min:3|max:50',
            'email' => 'required|email|unique:users',
            'password' => 'required|confirmed|min:8',
            //... more validation
        ];
    }
}    
```


then injecting the Form Request into the controller

in Controller:
```
public function create(CreateUserRequest $request, Post $post)
    {
        if ($request->user()->cannot('create', $post)) {
            abort(403); 
        }
 
        // create the post...
    }
```

in Policy:
```
class PostPolicy
{
    public function create(?User $user, Post $post)
    {
        return $user->name == 'Admin';
    }
}
```

