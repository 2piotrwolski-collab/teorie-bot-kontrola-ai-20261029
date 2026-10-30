# GC: rzeczywiste rolowanie — runda14

GC April→June,22.03.2024: oba miesiące mają własny long. Kontrola 1 kontraktu kosztuje modelowo 40,02USD. Przy 16 kontraktach i opóźnieniu 250 ms koszt 705,32USD; przy 1 s 610,32USD. Zamknięcie starego przed nowym, częściowe fille, depozyty, bilans i wszystkie stopy uzgodnione niezależnie. Jeden przypadek,3 warianty wykonania; brak pełnego wyniku strategii.

Osobne przeliczenia: python3 research_round14/T003_GC_roll/verify_baseline.py oraz verify_capacity.py.
Plany zamrożone przed wynikami; błędy wgrania i przypadkowy stary marginreplay zachowane. Dane/źródła/limity/pozostałe braki: findings.json i REPORT.html.

Rozszerzyć ten sam zweryfikowany mechanizm na pełną historię GC i następnie stały koszyk12rynków, bez zmiany progów. Równolegle uzupełniać datowane depozyty i kalendarze; zamrozić pełny plan przed obliczeniem zwrotu strategii.
