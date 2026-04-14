# Izvještaj o softverskim metrikama i statičkoj analizi

## 1. Softverske metrike (LOC)
Na temelju statičke analize izvornog koda, izmjerene su sljedeće vrijednosti:
- **Calculator.java:** 134 LOC (Lines of Code)
- **Start.java:** 19 LOC (Lines of Code)
- **Ukupni LOC za cijeli projekt:** 153 LOC

## 2. Neformalan pregled i statička analiza (Izvještaj)
Pregledom koda (Code Review) i korištenjem principa statičke analize, uočeni su sljedeći propusti i "Code Smells":

| Datoteka | Linija koda | Zapažanje |
| :--- | :--- | :--- |
| Calculator.java | 6 | **Code Smell:** Korištenje statičkog polja `finalResult` za pohranu rezultata operacije. Ovo onemogućuje reentratnost i može uzrokovati probleme u višenitnom okruženju. |
| Calculator.java | 18 | **Naming Convention:** Metoda `ToString()` krši Java standarde imenovanja (treba početi malim slovom). |
| Calculator.java | 55 | **Logički propust:** U slučaju dijeljenja s nulom, aplikacija ispisuje poruku, ali nastavlja s radom, što uzrokuje `ArithmeticException` i pad programa. |
| Start.java | 6 | **Naming Convention:** Varijabla `Expression` počinje velikim slovom, što je u suprotnosti s Java konvencijom za lokalne varijable. |
| Start.java | 12 | **Resource Leak:** Instanca `Scanner` objekta kreira se unutar `while` petlje u svakoj iteraciji, što je vrlo neefikasno trošenje memorije. |
| Start.java | 19 | **Code Smell:** Pozivanje metode `Calculator.Run` bez prethodne validacije korisničkog unosa može dovesti do neočekivanih pogrešaka u radu. |

## 3. Zaključak
Kôd posjeduje funkcionalnost, ali zahtijeva refaktoriranje u skladu s Clean Code principima, posebno u pogledu upravljanja resursima (Scanner) i poštivanja konvencija imenovanja.
