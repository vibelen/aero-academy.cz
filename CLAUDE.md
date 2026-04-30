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

## Logo — pravidla použití (z logomanuálu v2, BrandBoost)

### Koncept loga
Logo tvoří dvě části: **„Aero"** (velké, silné písmo) + **„Academy"** (menší, pod tím). V písmenu „A" je vylisovaná silueta letadla Alta NG pohledem shora — to je klíčový grafický prvek identity. Letadélko lze používat i samostatně jako dekorativní prvek v grafice.

### Varianty loga a kdy je použít
| Varianta | Soubor | Použití |
|---|---|---|
| Plné logo (ikona + text pod) | `logo/Aero_Academy-logo-final.png` | Hero sekce — velké, na tmavém/foto pozadí |
| Horizontální text logo | `logo/Aero_Academy-logo-text_black.png` | Nav, footer, malé formáty |
| Barevná verze | modrá | Světlé pozadí |
| Černá verze | černé PNG | Světlé pozadí (nav na glass) |
| Bílá verze | `filter: brightness(0) invert(1)` | Tmavé pozadí (hero, footer, ZL banner) |
| Favicon | `logo/Aero_Academy-FAVI_blue.png` | Prohlížeč, app ikona |

### Barva loga
Původní modrá loga je steel blue (~`#4B8EC8`). Na webu používáme verzi **Nová 03** — teal/adriatic (~`#005f80`), která je konzistentní s primární brand barvou webu.

### Pravidla použití
- Na **světlém pozadí** (glass, bílá): černá nebo barevná varianta — bez filtru
- Na **tmavém pozadí** (hero foto, footer, ZL banner): bílá varianta — `filter: brightness(0) invert(1)`
- Ve **footeru**: bílá verze, `opacity: 0.50` (jemně potlačená)
- **Nedeformovat**, nepřebarvovat libovolně, nezmenšovat pod čitelnou velikost
- Horizontální „dlouhé logo" (`Aero Academy` na jednom řádku) — použít jen kde není prostor pro stacked verzi

### Grafické prvky z identity
- **Silueta letadla** (Alta NG shora) — lze použít samostatně jako dekorativní prvek, watermark, ikona
- **Textura z letadel** — opakující se pattern letadélek (viz logomanuál str. 7), vhodné pro pozadí, obaly, desky
- Oba prvky zachovávají modrý/adriatický tón identity

## Hero sekce

**Výška:** `height: calc(100vh - 112px)` — kompenzuje top bar (36px) + nav (76px), aby vše bylo vidět bez scrollování.

**Layout:** `display: flex; flex-direction: column; justify-content: flex-end` — obsah kotví ke spodní hraně viewportu.

**Gradient overlay:** `linear-gradient(to bottom, ...)` — průhledný nahoře, tmavý (~0.72 opacity) dole pro čitelnost textu.

**Pořadí prvků (shora dolů):**
1. Logo `Aero_Academy-logo-final.png` — výška 56px, `filter: brightness(0) invert(1)` (bílé), `mb-4`
2. Divider — 48×2px, `rgba(255,255,255,0.40)`, `mb-4`
3. H1 „Létat je jednodušší, než sis kdy myslel." — třída `.hero-h1` (`clamp(2.8rem, 7.5vw, 5.8rem)`, weight 800, white), `mb-3`
4. Subline „Pilotní výcvik Praha Letňany" — třída `.hero-sub` (`clamp(1rem, 2vw, 1.35rem)`, weight 300, bílá 82%), `mb-6`
5. 2 CTA tlačítka — `.btn-cta` (cyan) + `.btn-ghost` (outline bílý), `mb-6`
6. Statistiky panel — `.glass-light`, `display: inline-grid; grid-template-columns: repeat(4, 1fr)`, `pb-8`

**Statistiky (4 stejně široké sloupce, `text-align: center`):**
| Číslo | Popis |
|---|---|
| 160+ | Absolventů |
| 8 | Letadel ve flotile |
| 4 | Typy průkazů |
| Praha / Letňany | Praha = `.stat-num` (výrazné), Letňany = `.stat-lbl` (jemné) |

Oddělovač sloupců: `border-right: 1px solid rgba(255,255,255,0.18)`, poslední bez borderu.

**Co v hero NENÍ:** žádný overline label, žádný podnadpis s více větami.

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

**Hover efekt nav odkazů:** podtržení přesně na délku textu (ne padding) — `text-decoration: underline`, `text-decoration-color: #005f80`, `text-decoration-thickness: 3px`, `text-underline-offset: 5px`. Přechod přes `transition: text-decoration-color 0.2s`. Nepoužívat `border-bottom` (podtrhuje celou šířku včetně paddingu).

**Mobile:** nav skrytý pod `lg`, hamburger (3 linky, poslední kratší) toggleuje `#mob-nav` dropdown s `.glass` stylem.

## Stack
- Tailwind CSS v4 Browser CDN (`@tailwindcss/browser@4`)
- AOS.js (scroll animace, CDN)
- Flowbite CDN (interaktivní komponenty, přestylováno glass CSS)
- Font NouvelR (lokální .ttf v `font-nouvel-r/`)

## Sekce Výcvikové programy

Třída `.glass`, padding 2.5rem. Label: „Výcvikové programy". H2: „Vyber si svůj průkaz."

**4 karty v gridu 2×2** (`grid-template-columns: 1fr 1fr`, `gap: 0.75rem`). Každá karta `.prog-card.glass-light`, padding 1.5rem.

Struktura karty:
- H3 (1.75rem, weight 800, adriatic letter-spacing) — zkratka průkazu
- Podtitulek (0.75rem, weight 300, color rgba(0,26,44,0.55)) — název na 1 řádku
- Popis (0.78rem)
- `<hr>` oddělovač
- Odrážky `—` v adriatic barvě
- Tlačítko `.btn-adriatic` „Zjistit více →" (full width)

| Průkaz | Podtitulek | Odrážky |
|---|---|---|
| ULL | Ultralehký letoun | 2 osoby, 20 h, 45 h teorie |
| PPL(A) | Soukromý pilot | Bez omezení, 45 h, 100 h teorie |
| LAPL(A) | Lehký sportovní pilot | 4 osoby, 30 h, 100 h teorie |
| CPL(A) | Obchodní pilot | Komerční lety, 200 h, ATPL teorie |

Pod kartami: sekce „Pokračovací kurzy:" s chip tagy (Noční létání, IR(A) SEP, Létání za špatného počasí, Safety kurz, Obnova průkazu, VFR řízené lety).

## Flotila (8 letadel)
ALTO NG Gold · Blue · Grey · Bristell LSA · Bristell B23 Red · Bristell B23 · CESSNA C172SP · Cirrus SR20

## Pořadí sekcí — main 8col (zleva)

1. Úvod (`id="o-nas"`)
2. Proč si vybrat nás (`id="proc"`)
3. Výcvikové programy (`id="vycviky"`)
4. 6 kroků jak se stát pilotem
5. Citát
6. Flotila (`id="flotila"`)

## Sekce 1 — Úvod (první panel v main 8col)

Třída `.glass .bw .bw-xl`, padding 2.5rem, border-radius 3px, overflow hidden. Bristell watermark vpravo nahoře.

**Obsah:**
1. Label `.label-up` — „Začít je jednoduché"
2. H2 `.sec-title` — „Chceš se naučit řídit letadlo?"
3. Odstavec 1 — typy průkazů + instruktoři. Vytučněno: `<strong>typy průkazů</strong>`, `<strong>dopravní piloti</strong>`
4. Odstavec 2 — řidičák + zkušební let. Vytučněno: `<strong>Zkušebním letem</strong>`

**Co tam není:** fotky, chipy, bento grid.

## Sekce 2 — Proč si vybrat nás (druhý panel v main 8col)

Třída `.glass .bw .bw-xl`, padding 2.5rem, border-radius 3px, overflow hidden. Bristell watermark vpravo nahoře.

**Obsah:**
1. Label `.label-up` — „Proč si vybrat nás"
2. H2 `.sec-title` — „Létáme srdcem."
3. Grid 6 karet — `grid-template-columns: 1fr 1fr`, `gap: 0.625rem`

**Každá karta** (`.glass-light`, padding 1rem 1.125rem, border-radius 2px):
- SVG ikona (18×18, stroke `#005f80`, stroke-width 1.75)
- Nadpis 0.82rem, font-weight 700, color `#001a2c`
- Text `.body-s`, 0.78rem
- Hover: `translateY(-3px)` + `box-shadow: 0 12px 32px rgba(0,95,128,0.14)`

**6 karet a jejich ikony:**
| Nadpis | Ikona |
|---|---|
| Dopravní piloti jako instruktoři | srdce (heart) |
| Teorie online | monitor/screen |
| Moderní letadla | vrstvy (layers) |
| Flexibilní rezervace | kalendář |
| Přátelská parta | lidé (users) |
| 160+ absolventů | medaile (award) |

## Sekce „6 kroků jak se stát pilotem"

Třída `.glass`, padding 2.5rem, border-radius 3px. Label: „Jak probíhá výcvik". H2: „6 kroků jak se stát pilotem."

Umístění: za sekcí Výcvikové programy, před Citátem.

**Timeline — struktura `<ol>`:** `display:flex; flex-direction:column; gap:0; list-style:none`

**Každý `<li>`:** `display:flex; gap:1.25rem; align-items:center`

Levý sloupec (šířka 2.25rem, `align-self:stretch`, `flex-direction:column`, `align-items:center`):
- Horní čára: `width:2px; flex:1; background:rgba(0,95,128,0.20)` — první krok má `opacity:0`
- Kroužek: `width/height:2.25rem; border-radius:50%; z-index:1` (překrývá čáru)
- Dolní čára: stejná — poslední krok má `opacity:0`

Kroužky: kroky 1–5 = adriatic `#005f80`, text bílý 0.7rem 800; krok 6 = cyan `#00CFEF` s SVG checkmark (stroke `#001a2c`).

Pravý sloupec: `padding:1rem 0`, h3 0.95rem 700, text `.body-s`.

**6 kroků:**
1. Zkušební let
2. Briefing a výběr výcviku
3. Lékařská prohlídka — „kdo může řídit, ten může létat"
4. Teorie
5. Výcvik ve vzduchu
6. Zkouška & průkaz v ruce — „a obloha je tvoje. Průkaz na celý život."

**Pozor:** nesmí být `margin` na čárových segmentech — způsobuje viditelné mezery. Čára je nepřerušená, kroužek ji překrývá díky `z-index:1`.

## Magazín widget (aside)

Třída `.glass`, padding 1.875rem, border-radius 3px.

**Hlavička:** label „Magazín" vlevo + odkaz „Všechny články →" vpravo.

**Každý článek = 3 informace, žádné jiné:**
1. **Fotka** — 64×52 px, `object-fit: cover`, border-radius 2px, flex-shrink 0
2. **Název článku** — `.hl`, 0.85rem, line-height 1.35
3. **Autor** — `.body-xs` (jméno instruktora, např. Lukáš Vychodil / Radek Sekyra)

**Co tam není:** kategorie/chip tagy, datumy, perex.

**Layout `.mag-row`:** `display: flex`, `align-items: center`, `gap: 0.875rem`. Oddělovač: `border-bottom: 1px solid rgba(0,26,44,0.08)`. Hover: `opacity: 0.75` na celém řádku.

**Fotky:** zatím placeholdery z `/photo/` (opakují se), konkrétní přijdou později.

## Sekce Citát

Třída `.glass-adriatic`, padding `2rem 2.5rem`, border-radius 3px, `border-left: 3px solid #005f80`.

Text: „V oblacích jsi nad věcí. Létání není jen způsob dopravy — je to pohled na svět ze správné perspektivy."
Autor: „— Lukáš Vychodil, hlavní instruktor" (0.72rem, weight 700, color `#005f80`, uppercase).

Umístění: za sekcí 6 kroků, před Flotilou.

## Sekce Flotila

Třída `.glass`, padding 2.5rem. Label: „Flotila". H2: „8 letadel. Vždy připravených."

Obsah: foto letadla (height 210px, object-fit cover) + chip tagy 8 letadel (Bristell tagy = `.chip.chip-a`) + popisný text.
Tlačítko `.btn-adriatic` „Prohlédnout flotilu →" vpravo vedle nadpisu.

## Aside — pořadí widgetů (4col vpravo)

1. **ZL Banner** (`id="zl"`) — tmavý gradient `#001220→#003148→#005f80`, Bristell watermark bílý vpravo nahoře, checklist 3 benefitů, `.btn-cta` cyan, `position: sticky; top: 96px`
2. **Magazín** (`id="magazin"`) — 4 články, každý: fotka 64×52px + název + autor
3. **Kontakt** (`id="kontakt"`) — `.glass-adriatic`, tel + email + adresa se SVG ikonami

## Konverzní architektura
Primární cíl: **Zkušební let**
ZL banner v aside = designový magnet (tmavý gradient, Bristell watermark, cyan CTA, sticky).

## TODO — další stránky
- [ ] Detail výcvikového programu
- [ ] Flotila + detail letadla
- [ ] Náš tým (Lukáš Vychodil, Radek Sekyra)
- [ ] Magazín + detail článku
- [ ] Kontakt / rezervační formulář
