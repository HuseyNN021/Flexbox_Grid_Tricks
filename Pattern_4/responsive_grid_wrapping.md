# CSS Grid — Responsive Grid Wrapping Pattern
 
## Nədir?
 
`@media` sorğusu olmadan grid-in ekran eniinə görə avtomatik sütun sayını tənzimləməsi texnikasıdır. `repeat()`, `auto-fit`/`auto-fill` və `minmax()` birlikdə istifadə olunur.
 
---
 
## Məntiq
 
```
grid-template-columns: repeat(auto-fit, minmax(250px, 1fr))
```
 
Bu bir sətir — tam responsive grid deməkdir. Heç bir `@media` lazım deyil.
 
---
 
## `repeat()`
 
İki parametr qəbul edir:
 
**1ci parametr** — neçə sütun olacaq. Rəqəm olarsa sabit sütun sayı, `auto-fit`/`auto-fill` olarsa dinamik olur.
 
**2ci parametr** — hər sütunun eni.
 
---
 
## `auto-fit` vs `auto-fill`
 
| | `auto-fit` | `auto-fill` |
|---|---|---|
| Boş xanalar | Collapse edilir (yox olur) | Saxlanılır |
| Az elementdə | Mövcud elementlər genişlənir | Elementlər genişlənmir, boşluq qalır |
| Çox elementdə | Eyni davranış | Eyni davranış |
 
```
3 card, 5 sütun ola biləndə:
 
auto-fit:  [card1]  [card2]  [card3]
auto-fill: [card1]  [card2]  [card3]  [    ]  [    ]
```
 
Əksər hallarda `auto-fit` daha uyğundur.
 
---
 
## `minmax(min, max)`
 
Sütunun minimum və maksimum enini təyin edir.
 
`minmax(250px, 1fr)` — sütun heç vaxt 250px-dən kiçilməz, amma mövcud boş yeri `1fr` ilə bərabər böləcək qədər böyüyə bilər.
 
**Necə işləyir:**
- Wrapper geniş olduqda → sütunlar `1fr` ilə bərabər böyüyür
- Wrapper daraldıqca → 250px həddə çatanda sütun sayı azalır, növbəti kart alt sıraya keçir
 
```
1500px wrapper, 250px min:
1500 / 250 = 6 sütun → hər kart ~250px
 
900px wrapper:
900 / 250 = 3 sütun → hər kart ~300px
 
500px wrapper:
500 / 250 = 2 sütun → hər kart ~250px
```
 
---
 
## `@media` ilə müqayisə
 
| | `auto-fit` + `minmax` | `@media` |
|---|---|---|
| Kod miqdarı | 1 sətir | Hər breakpoint üçün ayrı blok |
| Breakpoint | Avtomatik | Manual təyin edilir |
| Elastiklik | Yüksək | Orta |
| İstifadə | Kart grid, qalereya | Mürəkkəb layout dəyişiklikləri |
 
---
 
## Xülasə
 
`repeat(auto-fit, minmax(250px, 1fr))` — bir sətirdə tam responsive grid.  
`auto-fit` boş xanaları yox edir, elementlər mövcud yeri bölüşür.  
`minmax` kartın minimum enini qoruyur, ekran daraldıqca sütun sayı azalır.