# GC 2019–2025 — runda15

GC 2019–2025: odczytano 4 635 018 rzeczywistych świec minutowych i 282 879 z rozgrzewki 2018; 103 obserwowane kontrakty łącznie, bez zgłoszonych błędów technicznych. Zebrano 52 zmiany modelu depozytów. Osobny test wykazał przedwczesne stosowanie niższej stawki QC 19.06.2020: od północy zamiast po zamknięciu według CME. Nowy moduł rozdziela te momenty i przeszedł 10 kontroli; pełny adapter oraz wynik strategii po kosztach pozostają do ukończenia.

Dwa ukończone badania danych, nie zysk strategii. Nie ponawiać runów ac1dc2adbff19bfdac2d7b928f14182e i6a20f89b11a33b7a218d2d0b9323e180.

Weryfikacja lokalna: python3 research_round15/T003_GC_2019_2025/verify_range.py oraz verify_timing.py.

Najpierw uzgodnić źródłowy kalendarz GC i datowane stawki z godziną obowiązywania; potem zintegrować pełny adapter GC 2019–2025 i zamrozić reguły przed wynikiem po kosztach. Po GC przejść do stałego portfela 12 rynków.

Kryteria i konkretne źródła przy gap_plan w findings.json. CalendarCME2019–2024 dostępne web, lecz pełna ekstrakcja/2018/2025/firstintent nadal otwarte. Płatnych fallbacków brak. Zachować wszystkie błędy/redirecty. PriorytetGC przedportfelem w istniejącym przeglądzie09Warszawa.
