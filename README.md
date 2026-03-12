# Flexbox & Grid Tricks
 
CSS Flexbox və Grid-in praktik pattern-lərini əhatə edən nümunələr toplusu.
 
---
 
## Folder Structure
 
```
FLEXBOX_GRID_TRICKS/
├── Pattern_1/          # Flexbox — Isolated Element
│   ├── index.html
│   ├── style.css
│   └── flexbox-isolated-element.md
├── Pattern_2/          # CSS Grid — Grid Area & Bento Grid
│   ├── index.html
│   ├── style.css
│   └── css_grid_area.md
├── Pattern_3/          # CSS Grid — Stack Elements
│   ├── index.html
│   ├── style.css
│   └── stack_element_with_grid.md
├── Pattern_4/          # CSS Grid — Responsive Grid Wrapping
│   ├── index.html
│   ├── style.css
│   └── responsive_grid_wrapping.md
├── Pattern_5/          # CSS Grid — Fix Floating Footer
│   ├── index.html
│   ├── style.css
│   └── fix_floating_footer.md
└── Pattern_6/          # CSS Grid — Card Layout
    ├── index.html
    ├── style.css
    └── card_layout.md
```
 
---
 
## Patterns
 
| # | Pattern | Mövzu |
|---|---------|-------|
| 1 | Isolated Element | `margin: auto` ilə elementi qrupdan qoparmaq |
| 2 | Grid Area & Bento Grid | `grid-template-areas` ilə vizual layout xəritəsi |
| 3 | Stack Elements with Grid | `grid-area: 1/1` ilə elementləri üst-üstə yığmaq |
| 4 | Responsive Grid Wrapping | `auto-fit` + `minmax` ilə `@media`-sız responsive grid |
| 5 | Fix Floating Footer | `1fr` ilə footer-i həmişə aşağıda saxlamaq |
| 6 | Card Layout | `auto 1fr auto` ilə card içindəki button-u sabit yerləşdirmək |
 
---
 
## Necə işə salmaq olar
 
### Üsul 1 — Birbaşa brauzerdə açmaq
 
Hər pattern üçün həmin qovluğa girib `index.html` faylını brauzerdə aç:
 
```
Pattern_1/index.html → sağ klik → Open with Browser
```
 
### Üsul 2 — VS Code Live Server (tövsiyə olunur)
 
1. VS Code-da **Live Server** extension-unu quraşdır
2. İstənilən `index.html` faylını aç
3. Aşağı sağ küncdə **Go Live** düyməsinə bas
4. Brauzer avtomatik açılır və dəyişikliklər anında görünür
 
### Üsul 3 — Terminal ilə
 
```bash
# Python quraşdırılıbsa
cd Pattern_1
python -m http.server 3000
# http://localhost:3000 ünvanına get
```
 
---
 
## Hər pattern üçün README
 
Hər qovluqda həmin pattern-i izah edən ayrıca `.md` faylı var. Pattern-i başa düşmək üçün əvvəlcə həmin faylı oxu, sonra koda bax.
 
---
 
## Texnologiyalar
 
- HTML5
- CSS3 (Flexbox & Grid)
- JavaScript yoxdur — yalnız CSS
