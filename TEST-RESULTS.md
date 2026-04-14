# Izvještaj o testiranju (Black Box & Unit Testing)

## 1. Testiranje crne kutije (Black Box Testing)

Cilj ovog testiranja bio je provjeriti funkcionalnost aplikacije unosom različitih aritmetičkih izraza bez uvida u samu internu logiku koda.

| Testni slučaj | Unos (Input) | Očekivani rezultat | Stvarni rezultat | Status |
| :--- | :--- | :--- | :--- | :--- |
| Jednostavno zbrajanje | `5+5` | `10.0` | `10.0` | **Prošlo** |
| Prioritet operacija | `2+2*2` | `6.0` | `6.0` | **Prošlo** |
| Dijeljenje s nulom | `10/0` | Poruka o pogrešci | `ArithmeticException` | **Pao** |
| Prazan unos | *(Samo Enter)* | Upozorenje korisniku | `StringIndexOutOfBoundsException` | **Pao** |
| Negativni brojevi | `-5+3` | `-2.0` | Pogrešan izračun | **Pao** |
| Specijalni znakovi | `5!@#2` | Poruka o neispravnom unosu | `NumberFormatException` | **Pao** |

---

## 2. Jedinični test (Unit Test)

U skladu s lekcijom "Nivoi testiranja", pripremljen je testni scenarij za metodu `Calculate`.

```java
@Test 
public void testCalculatePriority() { 
    // Priprema
    String expression = "10+5*4"; 
    float expected = 30.0f; 
    
    // Izvršavanje
    float actual = Calculator.Calculate(expression); 
    
    // Provjera
    assertEquals(expected, actual, 0.001); 
}
```

## 3. Zapažanja i zaključak

Tijekom sistemskog testiranja uočeno je da aplikacija nije otporna na neispravne korisničke unose (robusnost je niska). Program se ruši kod dijeljenja s nulom i praznih stringova. Unit test potvrđuje da osnovna logika prioriteta operacija radi, ali nedostaje "Error Handling" (obrada pogrešaka) i validacija ulaznih podataka kako bi aplikacija bila stabilna za krajnjeg korisnika.
