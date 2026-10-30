# Turtle: rachunek i przygotowanie pełnego testu

Gotowe moduły rolowania, depozytów, kosztów i portfela przeszły90kontroli syntetycznych. Darmowy QC:56974dziennych obserwacji kontraktów,12rynków,2019–2025,0błędów depozytu. ICE:42poprawneCSV, starsze pliki i mapowanie nadal niekompletne. Pełny test zyskowności jeszcze NIEURUCHOMIONY; Turtle nieodrzucony.

Nic nowego teraz: kontoFree i dostęp do edytora działają po zamknięciu okienka. Nie potrzeba płatnegoAPI, hasła ani nowego konta.

Następny krok: Dokończyć darmowe dane i adapter: najpierw kontrolowany replay jednego rzeczywistego rolowania GC z własnym sygnałem obu miesięcy, potem niezmieniony portfel12rynków; osobno ICEstarsze lata i pełne kalendarze przed wynikiem zyskowności.

Pełny zakres/braki: findings.json, SOURCE_FIT_AND_DESIGN.json, ACCOUNT_COMPONENTS_FREEZE.json. Sprawdzenie: python3 -m unittest discover -s research_round13/T003_full_futures -p "test_*.py" -v.

Stare wyniki pozostają bez zmian. PnL jeszcze nie policzony.
