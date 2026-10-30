# T003: uzgodnienie dywidend — 30.10.2026

**Potwierdzono rachunek nowej rekonstrukcji Claude. Pochodzenie utraconego pierwotnego przebiegu pozostaje nieudowodnione.**
Zakres: archiwalny SPY long/cash Donchian 55/20, sygnał na poprzednim zamknięciu, wykonanie na następnym otwarciu, koszt 5 bps na stronę. To analiza konwencji księgowych, bez nowego werdyktu oryginalnego Turtle.

| Okres | Dywidendy w gotówce | Rekonstrukcja Claude | Claude historycznie, zaokrąglone | Dotychczasowy SPY |
|---|---:|---:|---:|---:|
| 2001–2015 | 0.887433 | 0.886664 | 0.887000 | 4.918073 |
| 2016–2019 | 4.265007 | 4.263415 | 4.263000 | 14.784655 |
| 2020–27.10.2026 | 2.785713 | 2.800930 | 2.801000 | 15.127449 |

CAGR w % rocznie. Benchmark pozostaje tym samym archiwalnym SPY z dywidendami w skorygowanym szeregu i tym samym kosztem 5 bps. Nie jest to pełny wynik po podatkach, FX lub rzeczywistych fillach.

## Przyczyna różnicy

W naszej metodzie dywidenda zwiększa gotówkę i czeka do następnego wejścia. W opisanej przez Claude rekonstrukcji zwiększa liczbę akcji po zamknięciu dnia ex-date, bez kosztu. Dlatego wartość obu portfeli w samym dniu ex-date może być identyczna, a od następnej sesji dywidenda pracuje z ceną tylko w metodzie reinwestowania.

Różnica 2020–27.10.2026 (rekonstrukcja minus gotówka), pp CAGR:
- Reinwestycja: +0.0151930235.
- Koszt także od dywidendy przy sprzedaży na otwarciu ex-date: -0.0000347025.
- 365,25 zamiast 365,2425 dni w roku: +0.0000581521.
- Pominięcie sygnału sprzed początku segmentu: +0.0000000000.
- Suma do rekonstrukcji: +0.0152164731.
- Zaokrąglenie 2,800929759 do 2,801: +0.0000702410.
- Suma do raportowanych 2,801: +0.0152867141.

Reinwestycja odpowiada za **99.38711%** różnicy do zaokrąglonej liczby. Rozdział policzono jako średni wpływ po wszystkich kolejnościach czterech zmian (Shapley), z pełnych 16 kombinacji dla każdego z 3 segmentów. Jest to uzgodnienie rachunku, nie wybór najlepszego wariantu.

## Dowód i jego granice

Nasz nowy, niezależnie napisany Python odtwarza wszystkie dzienne NAV wcześniejszego wariantu cash dokładnie (maksymalna różnica 0). Odtwarza też liczby nowej rekonstrukcji Claude do jej zadeklarowanych miejsc po przecinku. We wszystkich kombinacjach zachowano identyczne operacje: 74 / 18 / 40 oraz 24 / 9 / 15 naliczeń dywidend. Pierwsze rozbieżności NAV: 15.06.2001 (koszt od dywidendy przy sprzedaży), 20.06.2016 i 22.06.2020 (pierwsza sesja po reinwestycji).

Nie otrzymaliśmy wymienionej w tekście paczki JS/CSV. Nie sprawdziliśmy jej kodu, 12 deklarowanych hashy dzienników ani świeżych plików Yahoo Claude. Claude przyznał, że pierwotny CSV i pełny kod nie zostały zachowane. Dopasowanie nowej rekonstrukcji do trzech zaokrąglonych dawnych wyników nie dowodzi identyczności z utraconym przebiegiem. Stwierdzenie „dane nie mają udziału” jest potwierdzone tylko dla naszego porównania metod na tym samym zamrożonym zbiorze; nie dla utraconego historycznego pobrania.

Natychmiastowy kredyt dywidendy na ex-date i reinwestycja bez kosztu na zamknięciu są założeniami modeli. Daty wypłat, rzeczywisty DRIP i podatki nie są odtworzone. Koszt od dywidendy przy sprzedaży odtworzono diagnostycznie; nie wynika z kosztu obrotu samymi akcjami. Nie wybieramy wygodniejszej konwencji po wyniku.

Stare pliki wynikowe, plan A/B, dane i wcześniejszy raport pozostają niezmienione. Pełne nowe dzienniki wszystkich 48 kombinacji są lokalnie w osobnych skompresowanych plikach; publiczna kopia zawiera agregaty, plan, kod i weryfikację.

Następny krok: jeżeli paczka Claude zostanie dostarczona, porównać jej kod i hashe z tą niezależną rekonstrukcją. Właściwy test wykonywalnej strategii wymaga osobnego planu z rzeczywistymi datami wypłat i zasadami reinwestycji oraz nadal brakującego pełnego adaptera Turtle na futures.
