# Zadatak 2 - Dekkerov postupak međusobnog isključivanja

## Opis zadatka

Cilj ovog zadatka je implementirati i demonstrirati Dekkerov algoritam za međusobno isključivanje (mutual exclusion) na sustavu paralelnih procesa. Program koristi dva procesa koja se paralelno izvršavaju i koordiniraju pristup kritičnom odsječku kako bi spriječili istovremeni ulazak i time konflikt ili oštećenje zajedničkih podataka.

Dekkerov algoritam je klasičan primjer algoritma za rješavanje problema međusobnog isključivanja bez korištenja hardverske podrške za atomarne operacije. Koristi dvije zastavice (`ZASTAVICA`) za označavanje namjere ulaska u kritični odsječak i zajedničku varijablu (`PRAVO`) koja određuje koji proces ima prednost u slučaju sukoba.

## Što program radi

- Program stvara dva procesa korištenjem funkcije `fork()`.
- Svaki proces pokušava 5 puta ući u kritični odsječak.
- Prije ulaska u kritični odsječak, proces koristi Dekkerov algoritam da osigura da drugi proces ne ulazi istovremeno.
- U kritičnom odsječku proces ispisuje svoje identifikacijske podatke i brojače (`k` i `m`) 5 puta.
- Nakon izlaska iz kritičnog odsječka, proces daje prednost drugom procesu i ponavlja postupak.
- Program koristi zajedničku memoriju (pomoću `mmap`) za dijeljenje zastavica i varijable `PRAVO` između procesa.

## Zahtjevi i korištene tehnologije

- Program je napisan u C programskom jeziku.
- Koristi se POSIX funkcija `fork()` za stvaranje procesa.
- Dijeljena memorija implementirana je preko `mmap` sustavne poziva s opcijama `MAP_SHARED` i `MAP_ANONYMOUS`.
- Program je dizajniran za izvršavanje na Unix/Linux sustavima.
- Ispis rezultata omogućuje praćenje redoslijeda ulaska procesa u kritični odsječak.

## Kako pokrenuti program
   gcc main.c -o zadatak2
