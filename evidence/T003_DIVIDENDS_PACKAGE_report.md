# Turtle T003 — paczka Claude sprawdzona, rozbieżność dywidend zamknięta

Status: **CLOSED_NUMERICAL_RECONSTRUCTION_DISCREPANCY**. Sprawdzono nową rekonstrukcję archiwalnego wariantu SPY long/cash 55/20. Nie jest to potwierdzenie oryginalnego Turtle na futures ani odzyskanie utraconego pierwotnego przebiegu Claude.

## Co faktycznie wykonano

- ZIP v3: 56 452 B, SHA256 `2330ffc99b573f247bb2bc504043787011dd073566843a8c315267a5a7052727`; CRC poprawne i 17/17 sum plików zgodnych.
- Odczytano cały runner i oba pliki obliczeniowe. Uruchomiono ich niezmienione bajty lokalnie, bez sieci i odziedziczonych danych środowiska. Jeden przebieg Node v24.22.1, osobny pusty katalog wyników. Nie zmieniano kodu, danych ani założeń w celu dopasowania hashy.
- Oba SHA wejściowe zgodne z zamrożonymi SPY.csv i SPY_yahoo.json; 6997 rekordów, 112 dywidend, 0 splitów, braków OHLC, duplikatów dat dywidend i przesunięć UTC/NY.
- Wszystkie 12 CSV zgadzają się co do SHA256, bajtów i liczby wierszy z deklaracją Claude. Sześć dostarczonych dzienników zdarzeń jest identycznych z wygenerowanymi; sześć brakujących dziennych CSV zostało faktycznie wygenerowanych i potwierdzonych.
- Księgi cash mają dzienne NAV, liczbę akcji, gotówkę i dywidendy identyczne z niezależnym Pythonem. W księgach reinwestowania maksymalna różnica NAV to 1,1102230246251565e-15, czyli arytmetyka double. Wszystkie listy operacji są identyczne.
- Wszystkie 48 wyników czterech przełączników i rozbicie Shapleya zgadzają się z niezależnym audytem po uzgodnieniu kolejności czynników i kierunku znaku. Pełny dziennik 48 zdarzeń dywidendowych zgadza się z osobnym CSV.

## Wyniki — CAGR (% rocznie)

| Okres | Dywidendy cash | Rekonstrukcja Claude | Dotychczasowy matched SPY |
|---|---:|---:|---:|
| 2001–2015 | 0.887433 | 0.886664 | 4.918073 |
| 2016–2019 | 4.265007 | 4.263415 | 14.784655 |
| 2020–27.10.2026 | 2.785713 | 2.800930 | 15.127449 |

Model 5 bps na stronę, przed podatkami/FX i bez rzeczywistych filli. Benchmark to ten sam archiwalny skorygowany SPY. Przyczyna różnicy pozostaje potwierdzona: reinwestycja zamiast trzymania dywidend w cash odpowiada za 99,3871% różnicy do zaokrąglonych 2,801%; reszta to koszt od dywidendy przy sprzedaży, baza roku i zaokrąglenie.

## Przegląd kodu

`features` wyklucza aktualny bar z kanału i zachowuje ścisłe nierówności, a `sim` realizuje sygnał poprzedniej sesji na następnym otwarciu. Prawo do dywidendy przysługuje poprzedniemu posiadaczowi. Dywidenda przy zakupie na ex-date nie jest naliczana; przy sprzedaży jest. Różnice reinwestycji i prowizji od dywidendy są jawnie przełączane. `runOrig` jest portem fragmentu notatek, a nie zachowanym oryginalnym programem.

Stałe `CODEX_PUBLISHED` i `HISTORICAL_REPORTED` są punktami odniesienia, nie podstawionym wynikiem. Wartości `sim` i dzienniki wynikają z cen oraz zdarzeń dywidend. Runner może nadpisywać katalog OUT; zabezpieczyliśmy wykonanie przez utworzenie pustego nowego katalogu, bez zmiany paczki.

Pierwszy checker porównania JSON zatrzymał się na różnicy schematu: runner zawiera `events`, a dostarczony JSON pomija tę listę i przechowuje ją w osobnym CSV. Checker v1 i opis tej próby zachowano. Checker v2 porównuje listę z tym CSV, a wszystkie pozostałe pola z JSON-em. Nie zmieniano runnera ani wyników.

## Co zamykamy, a czego to nie dowodzi

**Zamykamy różnicę rachunkową dywidend w nowej rekonstrukcji.** Nie ma już brakującej paczki ani niesprawdzonych 12 hashy jej dzienników. Nie trzeba wracać do tej rozbieżności bez konkretnego nowego dowodu.

Pierwotny CSV i pełny kod Claude z 29.10 pozostają utracone. To trwałe ograniczenie historycznego pochodzenia, którego zgodna rekonstrukcja nie usuwa. Nie potwierdziliśmy rzeczywistych dat wypłat, DRIP, podatków, FX, filli ani strategii Turtle na futures. Te pytania mają osobny zakres i wymagają odrębnego planu.

149 wcześniejszych plików zachowuje swoje SHA. Wszystkie wiersze 90 eksperymentów, 247 prób i 21 decyzji pozostały niezmienione. Pełne nowe CSV, oryginalny ZIP, rozpakowana paczka, stdout/stderr i weryfikacja są lokalnie oraz w prywatnym archiwum. Publiczna kopia zawiera kod, hashe i agregaty, bez pełnego szeregu cen.
