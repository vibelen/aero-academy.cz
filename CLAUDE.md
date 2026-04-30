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
