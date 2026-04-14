# Izvještaj o softverskim metrikama i statičkoj analizi

## 1. Softverske metrike (LOC)
Na osnovu statičke analize izvornog koda, izmjerene su sljedeće vrijednosti:
- **Calculator.java:** 134 LOC (Lines of Code)
- **Start.java:** 19 LOC (Lines of Code)
- **Ukupni LOC za kompletan projekat:** 153 LOC

## 2. Neformalan pregled i statička analiza (Izvještaj)
Pregledom koda (Code Review) i korišćenjem principa statičke analize, uočeni su sljedeći propusti i "Code Smells":

| Fajl | Linija koda | Zapažanje |
| :--- | :--- | :--- |
| Calculator.java | 6 | **Code Smell:** Korišćenje statičkog polja `finalResult` za čuvanje rezultata operacije. Ovo onemogućava reentratnost i može dovesti do problema u višenitnom okruženju. |
| Calculator.java | 18 | **Naming Convention:** Metoda `ToString()` krši Java standarde imenovanja (treba da počinje malim slovom). |
| Calculator.java | 55 | **Logički propust:** U slučaju dijeljenja nulom, aplikacija ispisuje poruku ali nastavlja sa radom, što uzrokuje `ArithmeticException` i krah programa. |
| Start.java | 6 | **Naming Convention:** Promjenljiva `Expression` počinje velikim slovom, što je u suprotnosti sa Java konvencijom za lokalne promjenljive. |
| Start.java | 12 | **Resource Leak:** Instanca `Scanner` objekta se kreira unutar `while` petlje u svakoj iteraciji, što je veoma neefikasno trošenje memorije. |
| Start.java | 19 | **Code Smell:** Pozivanje metode `Calculator.Run` bez prethodne validacije korisničkog unosa može dovesti do neočekivanih grešaka u radu. |

## 3. Zaključak
Kôd posjeduje funkcionalnost, ali zahtijeva refaktorisanje u skladu sa Clean Code principima, posebno u pogledu rukovanja resursima (Scanner) i poštovanja konvencija imenovanja.
