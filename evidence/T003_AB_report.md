# Niezależna kontrola A/B i remisów — Turtle T003, archiwalny wariant SPY

Status: **sensitivity_not_verdict**. Wszystkie stare pliki wynikowe pozostają bez zmian. Nie przeprowadzono nowego testu GC.

Oryginalny silnik i oddzielny ledger odtworzyły dokładnie metryki, operacje i dzienne NAV trzech segmentów.

| Segment | v1 | A: gotówka DTB3 | B: sygnały nominalne | B: dywidendy cash | A+B | SPY |
|---|---:|---:|---:|---:|---:|---:|
| development | 1.110043 | 2.022466 | 0.886147 | 0.887433 | 1.837458 | 4.918073 |
| validation | 4.982420 | 5.635420 | 4.263947 | 4.265007 | 4.970559 | 14.784655 |
| retrospective_check | 3.502802 | 4.700172 | 2.798229 | 2.785713 | 4.047800 | 15.127449 |

Wartości to CAGR w procentach, przy archiwalnym założeniu5bps na stronę. development2001–2015, validation2016–2019, retrospective_check2020–27.10.2026. To nie pełne netto podatkowe ani nietknięty OOS.

A, B i A+B potwierdzają liczby Claude w podanej dokładności. B-exact ma ujawnioną różnicę0,0153pp w ostatnim segmencie; nie dopasowywano danych ani reguł do jego liczby.

Noclegi gotówki A:3208/623/1046, identycznie z przejść NAV i dat wykonania operacji. Średnia stopa ważona nocami:1,511880/1,430417/2,700163%. Osobny cash-ledger i przekształcenie zwrotów zgadzają się z błędem NAV<6e−14.

**Operacje:** wg klucza(kierunek,data sygnału,data wykonania,pora,powód) tylko w v1 występuje17/4/5=26operacji i tyle samo tylko w B; symetryczna lista ma52wpisy. Przypisywanie operacji po samym indeksie daje fałszywie62/4/11różnic, bo jedna przesunięta operacja przesuwa dalsze indeksy. Po pominięciu wyjścia20.01.2005 liczba17 spada do16, co dokładnie wyjaśnia podane przez Claude16/4/5.

**Remisy:**

| Sygnał | Nominalny close−kanał | Skorygowany close−kanał | Decyzja v1 |
|---|---:|---:|---|
| 2005-01-20 | 0.000000000000 | -0.000006564834 | wyjście |
| 2009-07-21 | -0.540000915527 | -0.000114828431 | brak wejścia |
| 2017-08-10 | 0.000000000000 | 0.000001160299 | utrzymanie |

Różnica z2005 pozostaje ujemna także w obliczeniu60-cyfrowym na dokładnych wartościach wejściowych. Problemem jest wrażliwość na basis/korekty danych, nie dowiedziony błąd operatora`<`. Nie dodawano tolerancji po wyniku. Kontrfaktyczne pominięcie jednego wyjścia obniża CAGR development z1,110043 do1,069860(−0,040183pp).

**Ograniczenie gotówki:** data obserwacji DTB3 wcześniejsza od poprzedniej sesji nie dowodzi godziny historycznej publikacji ani zachowania dawnych vintages. [FRED DTB3](https://fred.stlouisfed.org/series/DTB3) opisuje stopę dyskontową; [H15](https://www.federalreserve.gov/releases/h15/) publikuje obecnie o16:15. Dlatego A jest odtworzonym przybliżeniem Claude, a nie potwierdzoną wykonalną stopą cash.

Pełny zapis: conclusions.json, comparison_to_Claude_and_prior_candidate.json, specific_ties.json(z12miejscami), different_operations.csv, *_ledger_and_daily_NAV.json, *_cash_intervals.json, plan.json, freeze.json, test_recalculate.py. SHA256 wszystkich plików i kontrola nienaruszenia starych danych w final_verification.json.
