# Izvještaj o testiranju (Black Box & Unit Testing)

## 1. Testiranje crne kutije (Black Box Testing)
Cilj ovog testiranja bio je provjeriti funkcionalnost aplikacije unosom različitih aritmetičkih izraza bez uvida u samu internu logiku koda.

| Testni slučaj | Unos (Input) | Očekivani rezultat | Stvarni rezultat | Status |
| :--- | :--- | :--- | :--- | :--- |
| Jednostavno zbrajanje | `5+5` | `10.0` | `10.0` | Prošlo |
| Prioritet operacija | `2+2*2` | `6.0` | `6.0` | Prošlo |
| Dijeljenje s nulom | `10/0` | Poruka o pogrešci ili `NaN` | `ArithmeticException` (Pad programa) | **Pao** |
| Prazan unos | (Samo Enter) | Upozorenje korisniku | `StringIndexOutOfBoundsException` | **Pao** |
| Negativni brojevi | `-5+3` | `-2.0` | Pogrešan izračun ili Error | **Pao** |
| Specijalni znakovi | `5!@#2` | Poruka o neispravnom unosu | `NumberFormatException` | **Pao** |

## 2. Jedinični test (Unit Test)
U skladu s lekcijom "Nivoi testiranja", pripremljen je testni scenarij za metodu `Calculate`.

**Testni scenarij:**
- **Metoda:** `Calculator.Calculate(String expression)`
- **Ulaz:** `"10+5*4"`
- **Očekivani izlaz:** `30.0`

**Kod testa (JUnit stil):**
```java
@Test
public void testCalculatePriority() {
    String expression = "10+5*4";
    float expected = 30.0f;
    float actual = Calculator.Calculate(expression);
    assertEquals(expected, actual, 0.001);
}
