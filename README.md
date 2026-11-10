# 📅 Plan zajęć – semestr zimowy 2026/27

Interaktywny plan laboratoriów **mgr inż. Andrzeja Hermana** (Informatyka inż., Łódź) dla studiów dziennych i zaocznych. Wszystko w jednym miejscu: kalendarz, lista przedmiotów i zajęcia dzień po dniu.

> Statyczna strona bez zależności: HTML, CSS i czysty JavaScript. Nie wymaga budowania ani serwera.

---

## ✨ Funkcje

- **Podsumowanie semestru**: liczba zajęć, godzin, zajęć pozostałych i data najbliższego dnia zajęć.
- **Kalendarz październik–luty**: dni zajęć oznaczone kolorem trybu studiów i kropkami przedmiotów; kliknięcie dnia przewija do jego agendy.
- **Filtr trybu studiów**: *Wszystkie* / *Dzienne* / *Zaoczne*.
- **Ukrywanie minionych dni**: jednym przełącznikiem.
- **Agenda dzień po dniu**: godziny, przedmiot, grupa, semestr i sala; wyróżnione dzisiejsze lub najbliższe zajęcia.
- **Oznaczenia zmian**: zajęcia odwołane i odrabiane.
- **Zapamiętywanie ustawień**: filtr i przełącznik są zapisywane w `localStorage`.
- **Tryb ciemny** (zgodnie z ustawieniem systemu), **układ mobilny** i płynne przewijanie z poszanowaniem `prefers-reduced-motion`.

## 🗓️ Organizacja semestru

| Tryb | Dni | Miejsce |
| --- | --- | --- |
| Studia dzienne | czwartki | sala P-42, ul. Kilińskiego 98 |
| Studia zaoczne (zjazdy B) | soboty i niedziele | sala P-42, ul. Kilińskiego 98 |

### Ważne daty

- **8.10.2026**: zajęcia dzienne odwołane; *Projektowanie i programowanie z użyciem wzorców projektowych* odrabiane **12.11.2026**.
- **6–7.02 i 13–14.02.2027**: zjazdy 9 i 10 (egzaminacyjne).
- **15–28.02.2027**: przerwa.

## 📚 Przedmioty

| Przedmiot | Semestr | Tryb |
| --- | :---: | --- |
| Technologie internetowe | III | zaoczne |
| Wykorzystanie wzorców w technologiach | V | dzienne |
| Wykorzystanie wzorców w technologiach internetowych | V | zaoczne |
| Projektowanie i programowanie z użyciem wzorców projektowych | V | dzienne, zaoczne |
| Mappery obiektowo-relacyjne | VII | dzienne, zaoczne |
| Biznesowe systemy COTS | VII | zaoczne |
| Systemy masowego przetwarzania informacji | VII | zaoczne |

## 🚀 Uruchomienie

Wystarczy otworzyć `index.html` w przeglądarce:

```bash
git clone https://github.com/aherman-spoleczna-akademia-nauk/plan-zajec.git
cd plan-zajec
start index.html      # Windows (macOS: open, Linux: xdg-open)
```

Możesz też uruchomić lokalny serwer, np. `npx serve .` albo `python -m http.server`.

### Publikacja na GitHub Pages

W repozytorium: **Settings → Pages → Deploy from a branch → `main` / `(root)`**. Strona pojawi się pod adresem
`https://aherman-spoleczna-akademia-nauk.github.io/plan-zajec/`.

## 🗂️ Struktura projektu

```text
plan-zajec/
├── index.html   # układ strony: nagłówek, statystyki, filtry, kalendarz, agenda
├── style.css    # wygląd, kolory, tryb ciemny, widok mobilny
├── app.js       # dane planu i logika renderowania
└── favicon.svg  # ikona strony (kalendarz) w karcie przeglądarki
```

## ✏️ Edycja planu

Wszystkie zajęcia są w obiekcie `DATA` na początku [`app.js`](app.js).

**Zajęcia** (`DATA.ev`), jeden wpis na blok:

```js
{ "d": "2026-10-15",                  // data (RRRR-MM-DD)
  "s": "08:00", "e": "09:30",         // początek i koniec
  "n": "Mappery obiektowo-relacyjne", // przedmiot
  "g": "Grupa 1 TP",                  // grupa
  "sem": "VII",                       // semestr
  "t": "D",                           // tryb: "D" dzienne, "Z" zaoczne
  "z": 3,                             // numer zjazdu (tylko zaoczne)
  "x": 1,                             // opcjonalnie: zajęcia odwołane
  "m": 1 }                            // opcjonalnie: zajęcia odrabiane
```

**Kolory przedmiotów** (`DATA.col`): mapa `nazwa przedmiotu → kolor HEX`. Nowy przedmiot wymaga dodania tu koloru.

**Zjazdy egzaminacyjne**: tablica `EXAM` w `app.js`.
**Zakres miesięcy w kalendarzu**: lista `[rok, miesiąc]` w funkcji `render()` (miesiące liczone od 0).

## 📄 Źródło danych

Plany „HERMAN ANDRZEJ D” (studia dzienne) i „HERMAN ANDRZEJ B” (studia zaoczne, zjazdy B). W razie rozbieżności obowiązuje oficjalny plan uczelni.
