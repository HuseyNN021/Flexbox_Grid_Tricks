# CSS Grid — Stack Elements Pattern
 
## Nədir?
 
Grid istifadə edərək elementləri `position: absolute` olmadan **üst-üstə yığmaq** texnikasıdır. Bütün child elementlərə eyni `grid-area` verilir — grid onları eyni xanaya yerləşdirir və üst-üstə düşürlər.
 
---
 
## Məntiq
 
Grid normalda elementləri növbə ilə ayrı xanalara yerləşdirir. Lakin iki elementə eyni xana koordinatı (`1/1`) veriləndə grid onları eyni yerə qoyur — üst-üstə yığılırlar.
 
DOM-da **sonra gələn element üstdə** görünür — `z-index` vermədən.
 
```
wrapper
┌──────────────────────┐
│  item2 (üstdə)       │  ← DOM-da sonra
│  item1 (altda)       │  ← DOM-da əvvəl
└──────────────────────┘
```
 
---
 
## Vacib qeydlər
 
**1. `width: 100%` mütləq lazımdır.**
Child element default olaraq öz content-i qədər genişlənir. `width: 100%` verilmədikdə element çox kiçik olur və üstdəki element altındakını tamamilə örtür.
 
**2. `top/bottom/left/right` işləmir.**
Bu xüsusiyyətlər yalnız `position: absolute/relative/fixed/sticky` olan elementlərdə təsir edir. Grid elementlərində tamamilə ignore edilir.
 
Offset vermək üçün bunları istifadə et:
 
| İstədiyin effekt | Grid ilə düzgün yol |
|---|---|
| `top: 10px` | `align-self: start` + `margin-top: 10px` |
| `bottom: 10px` | `align-self: end` + `margin-bottom: 10px` |
| `right: 10px` | `justify-self: end` + `margin-right: 10px` |
| `left: 10px` | `justify-self: start` + `margin-left: 10px` |
 
**3. `place-items: center` hər iki elementi mərkəzləşdirir.**
`align-items` + `justify-items` xüsusiyyətlərinin qısaltmasıdır. Hər child-a ayrıca `align-self`/`justify-self` verərək override edə bilərsən.
 
---
 
## `position: absolute` ilə müqayisə
 
| | `grid-area: 1/1` | `position: absolute` |
|---|---|---|
| Parent-ə ehtiyac | Yox | `position: relative` lazım |
| Normal flow | Qorunur | Çıxır |
| `place-items` ilə | İşləyir | İşləmir |
| Offset vermək | `margin` + `align/justify-self` | `top/bottom/left/right` |
| Responsive | Asandır | Çətindir |
 
---
 
## İstifadə halları
 
Bu pattern ən çox aşağıdakı hallarda işlənir:
 
- **Hero section** — şəkil üzərində mətn
- **Card overlay** — kart üzərində badge və ya label
- **Image + gradient** — şəkil üzərində qaranlıq overlay
- **Loading skeleton** — content üzərində skeleton loader
 
---
 
## Xülasə
 
Eyni `grid-area` vermək → elementlər üst-üstə yığılır.  
`width: 100%` + `height: 100%` → element xananı tam tutur.  
Offset üçün `margin` + `align-self`/`justify-self` istifadə et — `top/bottom/left/right` deyil.