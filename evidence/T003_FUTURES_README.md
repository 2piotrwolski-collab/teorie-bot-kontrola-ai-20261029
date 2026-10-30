# Turtle na kontraktach ·30.10.2026

Rzeczywiste GC: po korekcie sesji92dni/kontrakt,184/184 różne OHLC dzienne. Tick/OI dostępne za darmo; pełnego wyniku Turtle jeszcze nie ma.

Turtle na kontraktach 30.10: wróciliśmy do źródłowego System2 i pojedynczych surowych kontraktów GC27G24/GC26J24. Dwie kontrole danych i dwie korekty techniczne zakończone w darmowym QC; starej próby nie dublowano. Nie obliczono nowego zysku strategii.

Turtle na kontraktach 30.10: 1.09.2023–12.01.2024: oba kontrakty mają transakcje w92/92 oczekiwanych dniach giełdowych, łącznie100920 świec minutowych, bez duplikatów i wad OHLCV. Wszystkie184 porównania OHLC natywny dzień vs pełna sesja z minut różnią się; natywnych dni tej próby nie używać bez naprawy do N/kanałów.

Turtle na kontraktach 30.10: oficjalne CME kalendarze łączą LaborDay i Thanksgiving z następną datą giełdową. Zastosowano segmenty sesji i właściwe skrócenie24.11.2023. Pozorne braki25.12/1.01 wynikały z kalendarza, nie z obalenia strategii.

Turtle na kontraktach 30.10: styczniowy GC z dawnej próby miał firstintent28.12.2023 i firstnotice29.12.2023, przy LTD29.01.2024. Filtr dni do wygaśnięcia był niewystarczający. Dodano kontrolę firstintent z datą publikacji metadanych; daty lutego/kwietnia potwierdzono retrospektywnie.

Turtle na kontraktach 30.10: w sesji2.01.2024 pozyskano1413039 ticków obu kontraktów i dodatnie OI po18aktualizacji. Po korekcie jednostronnych aktualizacji bid/ask świeżość obu stron≤1s wystąpiła przy89,38% transakcji GC lutowego i39,14% kwietniowego; to diagnostyka danych, nie obietnica fillu.

Turtle na kontraktach 30.10: 19 nowych testów komponentów PASS, w tym rolling20 podczas pozycji, stała kotwica WilderN, święta/DST i quote-age każdej strony. Pełny adapter portfela, rollu, depozytów i kosztów nadal niegotowy. Błąd pierwszego dekodera zachowano i jawnie wycofano jego interpretację „wszystkie kwotowania wadliwe”.

## Braki i następne kroki

Ticki i kwotowania pozyskano dla jednej sesji; wymagane pełny zakres, własny decoder obu stron, reguła fill po sygnale, rozmiar/poślizg i rozstrzygnięcie równych timestampów. Darmowe źródło: QuantConnect free historical Trade/Quote ticks for the same two individual GC contracts, separate bounded acquisition plan. Warunek: Dla pełnego zakresu zachować czasy obu stron, odrzucać stale/crossed/size0, nie używać kwotowania sprzed sygnału jako gwarantowanego późniejszego fillu.

OI/wolumen dostępne w chwili wyboru oraz overlap stary/nowy kontrakt przed first intent. Darmowe źródło: QC historical individual chain and OpenInterest; dated CME delivery memos and rules. Warunek: Nonzero/stale observations distinguished; carry positions only when successor own source signal supports them; predeclared mechanical roll convention, not hindsight choice.

Historyczne depozyty GC z przypisaniemGC-xx do terminu, initial/maintenance i brokerhouse; pełne opłaty i collateral/variation margin. Darmowe źródło: CME GC-2020-to-present.pdf (official, direct403 retained), IBKR archived current public fees. Warunek: Dated actual rows acquired and parsed; broker assumptions separated; current2.51USD visible fee components are not historical2024/fullnet proof.

Pełny adapter4/6/10/12units, notional reset, source-universe coverage and declared source discretion. Darmowe źródło: Original Turtle PDF plus freeQC covered source-markets; coffee/cocoa/cotton not demonstrated because QC ICE onlysugar. Warunek: Freeze explicit faithful reconstruction; keep unavailable/defunct source markets visible, do not silently replace withSPY/MGC/ETF or advertise exact1980s replication.

To wciąż jeden rynek i dwa terminy, bez wyniku zysku/straty, pełnego portfela ani potwierdzenia Turtle. 92 dni z transakcjami nie dowodzą kompletności każdego ticka.

Źródłowe dyskrecje: tygodniowa aktualizacja N, roczny notional, pełne grupy korelacji i timing rollu wymagają jawnych konwencji rekonstrukcji i integracji; nie stroić pod wynik.

Kawa/kakao/bawełna: pokrycie darmowego QC niepotwierdzone; dokumentacja ICE wymienia tylko cukier. Nie podstawiać ETF ani SPY.

CME źródła odczytano przez web; lokalne pobrania binarnych PDF timeout/403 zachowane. Pełne surowe dane licencjonowane zostały w QC; lokalnie archiwizujemy kod, małe agregaty i pełne logi.

## Dowody i odtworzenie

PLAN.json i freeze.json: pierwotny plan sesji; REPAIR1_FREEZE.json: poprawka kalendarza. TICK_OI_FREEZE.json: osobna kontrola danych; TICK_DECODER_CORRECTION_FREEZE.json: jawny nowy limit1przebiegu po błędzie dekodera, bez nadpisania pierwotnego budżetu0retry. Cztery pełne logi i cztery raporty QC zachowane; raporty sprawdzono przez SHA256/sklejanie ponumerowanych chunków.

source_state.py/gc_sample_calendar.py: nowe, oddzielne komponenty, stary research_kernels.py zachowany. python3 -m unittest discover -s research_round12/T003_futures -p "test_*.py" -v

Nie pozyskano bajtowego readbacku kodu zQC; nie twierdzimy, że jego SHA niezależnie potwierdzono. Źródłowe pliki lokalne są zamrożone, a kod wynikuV2 widoczny wUI potwierdzał protokół/gałęzie. Pełne historyczne dane pozostają wewnątrz darmowegoQC.

Archiwum prywatne obejmuje kod/logi/agregaty/receipts, a nie pełne licencjonowane pricepanel. CMErawPDFniepobrane, timeout/403 jawne. Szczegóły source_evidence.json, calendar_evidence.json, cost_source_evidence.json i receipts. Kosztowe2.51USD to tylko kandydat sumy bieżących widocznych składników, nie pełne netto ani taryfa2024.

Zintegrować nowe sesje, stałą kotwicę N i odczyt obu stron kwotowania z pełnym adapterem System2; sprawdzić OI asof, overlap rolowania i historyczne depozyty/koszty. Potem zamrozić pełny zakres portfela i uruchomić wynik strategii.
