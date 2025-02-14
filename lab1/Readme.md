# Laboratorium nr 1

Celem laboratorium jest zapoznanie się z podstawowymi pojęciami oraz narzędziami Javy.

## Przydatne informacje
* W programie Javy funkcja (a właściwie metoda) `main` musi być częścią jakiejś klasy. Jest ona punktem startowym programu.
* Metoda `main` akceptuje tablicę argumentów typu `String`, ponadto jest publiczną metodą statyczną:
```java
public class World {
   public static void main(String[] args) {
      // treść metody
   }
}
```
* Do wypisywania komunikatów użyj wywołań `System.out.print` oraz `System.out.println`.
* Standardowe wyjście można zaimportować do programu poleceniem `import static java.lang.System.out;`. 
  Wtedy komunikaty można wypisywać za pomocą wywołania `out.print` i `out.println`.
* Warunki logiczne w Javie są przechowywane w zmiennej typu `boolean` - nie ma automatycznej konwersji z innych typów.
* W Javie dostępna jest standardowa pętla `for` znana z C/C++. Można również użyć alternatywnej pętli `for` (tzw. `for each`) 
  do iterowania po elementach kolekcji:
```java
for(String argument : arguments){
}
```
* **Uwaga!** W Javie łańcuchy znaków (oraz inne typy referencyjne) porównuje się za pomocą wywołania `equals`, np.
  `string1.equals(string2)`.
* Typ wyliczeniowy deklaruje się za pomocą słowa kluczowego `enum`, np.:
```java
enum Direction {
  FORWARD,
  BACKWARD,
  RIGHT,
  LEFT
}
```
* Typu wyliczeniowego można użyć odwołując się do jego składowych, np.:
```java
Direction direction = Direction.FORWARD;
```
* W Javie (od wersji 7) można wykonywać instrukcję `switch` na łańcuchach znaków, np.
```java
switch(argument){
  case "f":
    out.println("Do przodu");
    break;
  case "b":
    out.println("Do tyłu");
    break;
}
```
* Od Javy w wersji 13 można również używać nowej składni wyrażenia `switch`, która pozwala przypisać jego wynik do
  zmiennej:
```java
String message = switch(argument){
  case "f" -> "Do przodu";
  case "b" -> "Do tyłu";
  default -> "Nieznana komenda";
}

out.println(message);
```

* W Javie można dość łatwo przekazać fragment tablicy, np. jako rezultat wywołania funkcji lub jako argument pętli for.
  Służy do tego wywołanie 
  ```java
  Arrays.copyOfRange(array, startInclusive, endExclusive);
  ```


## Zadania do wykonania

1. Uruchom program IntelliJ.
2. Utwórz nowy projekt typu **`Gradle` -> `Java`** (!**nie `Java` -> `Java`**) o nazwie `oolab`.
4. W katalogu `src/main/java/` utwórz pakiet `agh.ics.oop` (ppm na `src/main/java` -> `New package`).
5. W pakiecie `agh.ics.oop` utwórz klasę `World` ze statyczną funkcją `main`.
6. Zaimplementuj metodę `main` tak aby wyświetlały się dwa komunikaty:
   - `system wystartował`
   - `system zakończył działanie`
7. Uruchom program z p. 7 np. klikając zieloną ikonę pojawiającą się na początku linii, w której występuje metoda `main`.
8. Dodaj metodę statyczną `run`, która jest wywoływana pomiędzy tymi komunikatami.
9. Metoda `run` powinna informować o tym, że zwierzak idzie do przodu.
10. Uruchom program.
11. Rozszerz metodę `run` tak by akceptowała tablicę argumentów typu `String`.
12. Po komunikacie o poruszaniu się do przodu wypisz w konsoli wartości wszystkich argumentów tej metody oddzielone przecinkami.
13. Zwróć uwagę na to, żeby nie było nadmiarowych przecinków.
14. Uruchom program z dowolnymi parametrami (muszą występować co najmniej 2).
15. Zmodyfikuj program tak aby interpretował wprowadzone argument:
    - `f` - oznacza, że zwierzak idzie do przodu,
    - `b` - oznacza, że zwierzak idzie do tyłu,
    - `r` - oznacza, że zwierzak skręca w prawo,
    - `l` - oznacza, że zwierzak skręca w lewo,
    - pozostałe argumenty powinny być ignorowane.
16. Poruszanie się oraz zmiana kierunku ma być oznajmiana odpowiednim komunikatem. Program powinien akceptować dowolną liczbę
    argumentów. Przykładowo wprowadzenie sekwencji `f f r l` powinno dać w wyniku następujące komunikaty:
    - Start
    - Zwierzak idzie do przodu
    - Zwierzak idzie do przodu
    - Zwierzak skręca w prawo
    - Zwierzak skręca w lewo
    - Stop
17. Zmodyfikuj program w ten sposób, aby metoda `run` nie akceptowała tablicy łańcuchów znaków, lecz tablicę
    wartości typu wyliczeniowego (`enum`). Zamiana łańcuchów znaków powinna być realizowana przez metodę wywoływaną w
    funkcji `main` przed wywołaniem metody `run`, natomiast typ wyliczeniowy powinien być zdefiniowany w osobnym pliku
    (`Direction.java`) w pakiecie `agh.ics.oop`.
18. Zweryfikuj poprawność działania programu poprzez jego uruchomienie.
19. Zamknij IntelliJ.
21. W pliku `gradle.build` w sekcji `plugins` dodaj linię `id 'application'`: 
    ```
    plugins {
      id 'application'
      id 'java'
    }
    ```
23. W tym samym pliku dodaj sekcję:
    ```
    application {
      mainClassName = 'agh.ics.oop.World'
    }
    ```
20. Otwórz konsolę (np. terminal/PowerShell).
20. Wywołaj komendę `export JAVA_HOME=/usr/lib/jvm/java-16` (pod Windows trzeba będzie ustawić zmienną środowiskową wskazującą na katalog, w którym zainstalowana jest Java). **Komendę trzeba zaadaptować do lokalnej instalacji Javy!**
21. Uruchom program poleceniem `./gradlew run --args="f l"` (lub `gradlew.bat ...` w systemie Windows)
23. Zmodyfikuj argumenty wywołania i sprawdź zachowanie programu.
24. (**Dla zaawansowanych**) Zmień kod odpowiedzialny za konwersję argumentów oraz wyświetlanie kierunków, tak by 
    korzystał z interfejsu `stream` dostępnego w Javie 8.
