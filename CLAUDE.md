# Aero Academy — Project Brief

## Kontext
Web pro pilotní školu na letišti Praha Letňany. Kreativní ředitel: uživatelka. Exekutiva: Claude.
Brand voice: přátelská parta pilotů, kteří žijí létáním. Tón: akční, moderní, civilní.
Hlavní sdělení: **Létat je jednoduché jako řídit auto.**

## Kontakty (z live webu aero-academy.cz)
- Tel: +420 607 077 373
- Email: info@aero-academy.cz
- Adresa: Hůlkova 1075/35, 198 00 Praha 18 — Letiště Praha Letňany

## Vizuální systém

### Barvy
| Token | Hodnota | Použití |
|---|---|---|
| Adriatic Sea | `#005f80` | Primární brand, linky, ikony, label-upper |
| Sky Deep | `#001a2c` | Nadpisy, tmavé texty |
| CTA Cyan | `#00CFEF` | Primární CTA tlačítko (schváleno v paměti) |
| **CTA Amber** | `#F07800` | **Navržená** doplňková CTA barva — vysoký kontrast na light glass, teplá energie |

### Glassmorphism (schválené hodnoty — neměnit bez pokynu)
```css
.glass          { background: rgba(224,241,252,0.48); backdrop-filter: blur(18px); border: 1px solid rgba(255,255,255,0.72); }
.glass-strong   { background: rgba(210,233,250,0.58); backdrop-filter: blur(28px); border: 1px solid rgba(255,255,255,0.78); }
.glass-light    { background: rgba(255,255,255,0.35); backdrop-filter: blur(12px); border: 1px solid rgba(255,255,255,0.65); }
.glass-adriatic { background: rgba(0,95,128,0.15);   backdrop-filter: blur(16px); border: 1px solid rgba(0,150,200,0.30); }
.glass-nav      { background: rgba(255,255,255,0.80); backdrop-filter: blur(24px); border-bottom: 1px solid rgba(255,255,255,0.85); }
```

### Text na light glass
| Element | Barva |
|---|---|
| Nadpisy (h2, h3) | `#001a2c` |
| Body primární | `rgba(0,26,44,0.72)` |
| Body sekundární | `rgba(0,26,44,0.52)` |
| Ikony, linky, akcenty | `#005f80` |
| label-upper | `#005f80` |

### Výjimky (bílý text / cyan)
- Hero headline + subline — přes oblohu, není na glass → bílé
- ZL banner — vlastní tmavý gradient → bílé + cyan
- Hero overline label-upper → `#00CFEF`
- ZL banner label-upper → `#00CFEF`
- btn-cta — cyan fill všude

### Bristell SVG watermark
Soubor: `graphic-elements/bristell-vector/Bristell-vector.svg`
Integrován přes CSS `::after` pseudo-element:
- Světlé panely: `opacity: 0.07`, `mix-blend-mode: multiply` (modrá patina)
- ZL banner (tmavý): `filter: brightness(0) invert(1)`, `opacity: 0.13` (bílý odlesk)

### Pozadí
`photo/photo-sky-background.jpg` — `background-attachment: fixed`, pokrývá celou stránku.
Komponenty (glass panely) kloužou přes fixní oblohu.

## Lišta aktualit (top bar)

Výška 36 px, pozadí `#001220`, border-bottom `rgba(0,95,128,0.28)`.

**Struktura zleva doprava:**
1. **Label „Aktuality"** — třída `.label-up-w` (cyan, 0.67rem, letter-spacing 0.18em, uppercase), flex-shrink:0
2. **Separátor** — 1px × 14px, `rgba(0,150,200,0.35)`
3. **Scrollující novinka** — jedna zpráva jako `<a href="..." class="ticker-link">`, zduplikovaná pro bezešvou smyčku (`translateX(-50%)`), animace 14 s linear infinite, fade na krajích přes `mask-image` (gradient transparent→black)
4. **Separátor** — 1px × 14px, `rgba(0,150,200,0.25)`
5. **Telefon** — SVG ikona + číslo, `<a href="tel:...">`, flex-shrink:0
6. **Separátor** — 1px × 14px, `rgba(0,150,200,0.25)`, skrytý pod `sm` (`hidden sm:block`)
7. **Email** — SVG ikona + adresa, `<a href="mailto:...">`, skrytý pod `sm` (`hidden sm:flex`)

**Novinky:** 3 různé zprávy, každá jako `<a href="..." class="ticker-link">`. Celá sada zduplikována (6 prvků celkem) pro bezešvou smyčku — `-50%` překladu odpovídá přesně jedné sadě.

**CSS třídy:**
```css
.ticker-wrap  { overflow:hidden; mask-image: fade-okraje; }
.ticker-track { display:inline-flex; gap:0; animation: tick 36s linear infinite; }
.ticker-track:hover { animation-play-state: paused; }   /* zastaví se pro klik */
.ticker-link  { color:rgba(255,255,255,0.60); text-decoration:none; padding-right:7rem; transition:color 0.2s; }
.ticker-link:hover { color:#00CFEF; }
```

**Pozor:** `gap` musí být `0` — mezery jsou řešeny přes `padding-right` na `.ticker-link`, jinak `-50%` translate nesedí a animace bliká na konci smyčky.

## Sticky header (nav)

Výška 76 px, třída `.glass-nav` (80% bílá + blur 24px).

**Layout:** 3-sloupcový grid — `grid-template-columns: 1fr auto 1fr`
- Vlevo: logo `Aero_Academy-logo-text_black.png`, výška 26 px, `justify-self: start`
- Střed: nav odkazy (`auto` šířka) — přesně vycentrované
- Vpravo: CTA tlačítko `.btn-cta`, `justify-self: end`

**Nav položky:** Výcviky · Flotila · Náš tým · Magazín · Kontakt
Třída `.nav-link` — 0.875rem, barva `rgba(0,26,44,0.70)`, hover: `#005f80` + `rgba(0,95,128,0.06)` bg, border-radius 4px.

**Telefon v navu není** — je pouze v top liště a v kontaktním widgetu.

**Mobile:** nav skrytý pod `lg`, hamburger (3 linky, poslední kratší) toggleuje `#mob-nav` dropdown s `.glass` stylem.

## Stack
- Tailwind CSS v4 Browser CDN (`@tailwindcss/browser@4`)
- AOS.js (scroll animace, CDN)
- Flowbite CDN (interaktivní komponenty, přestylováno glass CSS)
- Font NouvelR (lokální .ttf v `font-nouvel-r/`)

## Výcvikové programy
| Průkaz | Popis | Létání | Teorie |
|---|---|---|---|
| ULL | Ultralight, 2 osoby | 20 h | 45 h |
| LAPL(A) | Rekreační, 4 osoby | 30 h | 100 h |
| PPL(A) | Plný průkaz, bez omezení | 45 h | 100 h |

Další kurzy: NIGHT, IR(A) SEP, VMC→IMC, Safety kurz, Obnova průkazu, VFR řízené lety

## Flotila (8 letadel)
ALTO NG Gold · Blue · Grey · Bristell LSA · Bristell B23 Red · Bristell B23 · CESSNA C172SP · Cirrus SR20

## Konverzní architektura
Primární cíl: **Zkušební let**
ZL banner v aside = designový magnet (tmavý gradient, Bristell watermark, cyan CTA, sticky).

## TODO — další stránky
- [ ] Detail výcvikového programu
- [ ] Flotila + detail letadla
- [ ] Náš tým (Lukáš Vychodil, Radek Sekyra)
- [ ] Magazín + detail článku
- [ ] Kontakt / rezervační formulář
