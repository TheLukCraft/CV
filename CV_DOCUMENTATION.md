# CV Documentation - Łukasz Capała

## Przegląd projektu

Jednostronicowe CV zoptymalizowane pod ATS (Applicant Tracking Systems) oraz czytelne dla rekruterów.

**Język CV:** English  
**Format:** HTML + inline CSS  
**Rozmiar strony:** A4 (210mm × 297mm)  
**Plik:** `cv.html`

---

## Kluczowe decyzje projektowe

### 1. Struktura HTML (semantyka ATS)

```
header          → dane kontaktowe, imię, tytuł
main
  section.summary        → podsumowanie zawodowe
  section.skills         → umiejętności (kategorie)
  section.experience     → doświadczenie zawodowe
  section.education      → wykształcenie
  section.certifications → certyfikaty
  section.languages      → języki
  section.gdpr           → klauzula RODO
```

**Dlaczego:** ATS najlepiej parsuje semantyczne tagi HTML5. Unikamy `div`-ów tam, gdzie to możliwe.

### 2. Typografia

| Element | Rozmiar | Uwagi |
|---------|---------|-------|
| Body/treść | 10.5px | Kompromis między czytelnością a zmieszczeniem na 1 stronie |
| Nagłówki sekcji (h2) | 11px | Uppercase + letter-spacing dla wyróżnienia |
| Imię (h1) | 18px | Największy element |
| Tytuł stanowiska | 12px | Pod imieniem |
| Line-height | 1.3 | Optymalne dla gęstości tekstu |

**Font stack:**
```css
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Arial, "Noto Sans", "Liberation Sans", sans-serif;
```

**Dlaczego:** Fonty systemowe = 100% kompatybilność z ATS, brak problemów z embedowaniem fontów w PDF.

### 3. Marginesy i układ

- `@page { size: A4; margin: 14mm; }` — standardowe marginesy drukarskie
- Brak kolumn, brak tabel — ATS często źle parsuje wielokolumnowe układy
- Flexbox tylko dla wyrównania nagłówków (job-header, edu-header)

### 4. Format dat

Spójny format: `MM/YYYY – MM/YYYY` lub `MM/YYYY – Present`

Przykłady:
- `06/2024 – Present`
- `09/2021 – 06/2022`
- `10/2017 – 03/2021`

### 5. Sekcja Experience — struktura

**Dla stanowisk standardowych:**
```
Company — Role
Date | Location
• Bullet point 1
• Bullet point 2
Tech stack: ...
```

**Dla projektów freelancerskich:**
```
Freelancer — Full Stack Developer
Date | Location
  Project: Nazwa — opis
  • Bullet 1
  • Bullet 2
  Tech stack: ...
  Link: URL
```

### 6. Sekcja Skills — format

Kategorie oddzielone, wartości rozdzielone przecinkami:

```
Backend: C#, .NET, ASP.NET Core, Entity Framework Core, REST API, xUnit
Frontend: Angular, TypeScript, HTML, CSS, Tailwind CSS
...
```

**Dlaczego:** ATS łatwo wyciąga słowa kluczowe z list przecinkowych.

### 7. Linki

Format: `<a href="https://...">https://...</a>`

ATS widzi zarówno tekst linku, jak i atrybut href. Pełne URL-e są bardziej profesjonalne i parsowalne.

### 8. Elementy unikane (problematyczne dla ATS)

- ❌ `position: absolute/fixed`
- ❌ Wielokolumnowość (`column-count`, `float`)
- ❌ SVG, ikony, obrazki
- ❌ Progress bary / wykresy umiejętności
- ❌ Tabele do layoutu
- ❌ Zewnętrzne fonty (Google Fonts)
- ❌ Tła kolorowe, ramki dekoracyjne

---

## Instrukcja generowania PDF

### Chrome "Print to PDF"

1. Otwórz `cv.html` w Chrome
2. `Ctrl+P` (Print)
3. Destination: **Save as PDF**
4. Layout: **Portrait**
5. Paper size: **A4**
6. Margins: **Default** lub **None** (CSS kontroluje marginesy)
7. Background graphics: **OFF**
8. Save

### Potencjalne problemy

| Problem | Rozwiązanie |
|---------|-------------|
| Treść ucięta na dole | Zmniejsz `font-size` o 0.5px lub `line-height` na 1.25 |
| Za dużo białej przestrzeni | Zwiększ `margin-bottom` sekcji |
| Linki nieaktywne | Sprawdź czy `href` ma pełny URL z `https://` |

---

## Dane kontaktowe (źródło)

```
Name:      Łukasz Capała
Title:     .NET & Angular Developer
Location:  Katowice / Remote
Phone:     +48 667711900
Email:     lukasz@capala.pl
Portfolio: https://www.capala.pl
GitHub:    https://github.com/TheLukCraft
LinkedIn:  https://www.linkedin.com/in/lukaszcapala/
```

---

## Kolejność sekcji

1. **Header** — imię, tytuł, kontakt
2. **Summary** — 2-3 zdania o sobie
3. **Skills** — kategoryzowane umiejętności
4. **Experience** — od najnowszego
5. **Education** — od najnowszego
6. **Certifications** — lista
7. **Languages** — inline
8. **GDPR Consent** — mały tekst na dole

---

## Wersjonowanie

| Wersja | Data | Zmiany |
|--------|------|--------|
| 1.0 | 2024-12-14 | Wersja początkowa |

---

## Checklist przed wysłaniem CV

- [ ] Otwórz w Chrome i sprawdź Print Preview
- [ ] Całość mieści się na 1 stronie A4
- [ ] Wszystkie linki działają
- [ ] Brak literówek
- [ ] Daty są spójne (MM/YYYY)
- [ ] PDF wygląda identycznie jak podgląd

---

## Dla przyszłych agentów AI

### Modyfikacja treści
- Edytuj bezpośrednio w `cv.html`
- Zachowaj semantyczne tagi HTML
- Nie dodawaj kolumn ani tabel

### Modyfikacja stylu
- CSS jest w `<style>` w tym samym pliku
- Testuj zmiany w Chrome Print Preview
- Zachowaj font-size w zakresie 10-11px dla treści

### Jeśli nie mieści się na 1 stronie
1. Zmniejsz `line-height` z 1.3 na 1.25
2. Zmniejsz `margin-bottom` sekcji z 8px na 6px
3. Zmniejsz `font-size` z 10.5px na 10px
4. Skróć bullet pointy w Experience

### Słowa kluczowe dla ATS (zachowaj w CV)
`C#`, `.NET`, `ASP.NET Core`, `Angular`, `TypeScript`, `REST API`, `Entity Framework`, `SQL Server`, `Redis`, `Docker`, `Git`, `SOLID`, `Clean Code`, `Unit Testing`, `Full Stack Developer`
