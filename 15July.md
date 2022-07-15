# Ogólne: Napiszcie w swojej głównej technologii funkcję, która pozwoli sprawdzić czy dany string/zdanie/wyraz jest palindromem.

Palindromem nazwiemy string lub liczbę, który po odwróceniu kolejności znaków będzie równy stringowi lub liczbie przed odwróceniem.
```php
function isStringPalindrome($string){
    //reverse the string and compare against the original 
    if(strrev($string) == $string){
        return true;
    }else{
        return false;
    }
}

//to musiałem sprawdzić na geeksforgeeks.org bo nie doszedłem do rozwiązania
function isNumPalindrome($num){
    //reverse the order of the numbers, then compare against the original number
    
    $temp = $num;

    //new is going to be a reversed number
    $new = 0; 

    //while $temp is not rounded down to 0 which will also equal false and stop the iteration
    while (floor($temp)) { 
        //cyfra jedności z $temp
        $ones_digit = $temp % 10;

        //creates a reversed number
        $new = $new * 10 + $ones_digit;

        //move one digit to the left
        $temp = $temp/10; 
    } 
    if ($new == $num){ 
        return true; 
    }
    else{
        return false;
    }
}

```


# Backend: Wyjaśnij pojęcia: Dependency Injection, SQL Injection, Dependency Inversion

## Dependency injection
Wstrzykiwanie zależności to paradygmat Odwrócenia Sterowania (Inversion of Control), który to wzorzec oznacza większą kontrolę egzekucji kodu przez bibliotekę/framework, aniżeli przez programistę.
Wstrzykiwanie zależności polega na tworzeniu zależności między komponentami tak aby ograniczyć ("odwrócić") obowiązek kontrolowania zależności przez programistę. Prosty przykład używania dependency injection to używanie seterów.  
## SQL injection
SQL injection to przykład ataku SQL polegającego na próbie egzekwowania queries z miejsc, które nie są do tego przeznaczone (np. pole na imię i nazwisko).

Jednym z przykładów SQL Injection są tzw. "batched" (zgrupowane) statements. Przykładowym atakiem tego rodzaju jest np. wpisanie 
";DROP TABLE Suppliers" po wpisaniu "Paweł" w polu "Imię" do wypełnienia
## Dependency inversion
Dependency inversion principle to ostatnia zasada z SOLID, która propaguje używanie interfejsów (abstrakcji). Pisząc kod oparty na interfejsach gwarantujemy, że implementacja interfejsów zmniejsza ilość zależności do konkretnych implementacji.