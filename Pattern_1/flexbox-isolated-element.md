# CSS Layout Patterns — Flexbox & Grid
 
## Pattern 1 — Flexbox Isolated Element
 
### Nədir?
 
Flex container içindəki bir elementi qrupdan "qoparıb" müstəqil şəkildə yerləşdirmək texnikasıdır. Bunun üçün `margin: auto` istifadə olunur.
 
---
 
### Məntiq
 
Flex container-də həmişə **boş yer (free space)** olur. Bu boş yeri normalda `justify-content` idarə edir.
 
Lakin bir elementə `margin: auto` veriləndə — **bütün boş yer həmin margin tərəfindən udulur.** Digər elementlər sıxışdırılır.
 
---
 
### İstifadə halları
 
**Sağa itələmək** — `margin-left: auto`
```
[A] [B] [C]                         [D]
         ←————————auto————————————→
```
 
**Sola itələmək** — `margin-right: auto`
```
[A]                         [B] [C] [D]
    ←————————auto————————→
```
 
**Ortaya çəkmək** — `margin-left: auto` + `margin-right: auto`
```
[A] [B]           [C]           [D] [E]
          ←auto→       ←auto→
```
 
---
 
### Vacib qeydlər
 
**1. Parent flex olmalıdır.**
`margin: auto` yalnız flex child-da işləyir. Elementin birbaşa parent-i `display: flex` olmalıdır.
 
**2. Boş yer olmalıdır.**
Əgər container öz content-i qədər kiçilərsə (shrink-to-content), boş yer qalmır və `auto` heç nə etmir. Buna görə bəzən container-ə `width` vermək lazım gəlir.
 
**3. Birdən çox `auto` olarsa**, mövcud boş yer aralarında bərabər bölünür.
 
---
 
### `justify-content` ilə fərqi
 
| | `justify-content` | `margin: auto` |
|---|---|---|
| Təsir edir | Bütün child-lara | Yalnız həmin elementə |
| Nəzarət | Container tərəfindən | Element özü tərəfindən |
| İstifadə | Ümumi layout | Bir elementi qoparmaq |
 
---
 
### Xülasə
 
`margin: auto` flex-də **"qalan boş yeri mənə ver"** deməkdir.  
Bir tərəfdən verilsə → o tərəfə itələnir.  
Hər iki tərəfdən verilsə → ortaya düşür.
 
Bu pattern ən çox **navbar**, **toolbar** və **card footer** layoutlarında işlənir.
 
---
 
## Pattern 2 — CSS Grid Area
 
### Nədir?
 
`grid-template-areas` — grid layout-u vizual olaraq **string xəritəsi** ilə təyin etmək üsuludur. Hər child elementə `grid-area` ilə ad verilir, container-də isə bu adlar yerləşdirilib sıralanır.
 
---
 
### Məntiq
 
Container-də sütun və sıra sayı təyin olunur. Sonra `grid-template-areas`-da hər xana üçün ad yazılır. Eyni ad bir neçə xanada yazılarsa, həmin element o xanaları birləşdirib tutur (span).
 
```
"navbar navbar"     ← navbar 2 sütunu da tutur
"aside  main  "     ← aside sol, main sağ
"footer footer"     ← footer 2 sütunu da tutur
```
 
Hər child-a `grid-area: <ad>` verilir — container-dəki ada uyğun yerə düşür.
 
---
 
### Vacib qeydlər
 
**1. Ad HTML id/class ilə eyni olmaq məcburiyyətində deyil.**
`grid-template-areas`-dakı ad ilə `grid-area`-dakı ad uyğun olmalıdır — HTML atributu ilə əlaqəsi yoxdur.
 
**2. Hər sıra eyni sayda sütun olmalıdır.**
Bütün sətirlərdə sütun sayı bərabər olmalıdır, əks halda layout pozulur.
 
**3. Boş xana üçün nöqtə (`.`) istifadə olunur.**
```
"header header"
"sidebar .     "   ← sağ xana boş buraxılır
"footer footer"
```
 
### Nümunə — Bento Grid
 
Bento Grid, Grid Area-nın praktik tətbiq nümunəsidir. Müxtəlif ölçülü kartlar mozaik kimi yerləşdirilir — eyni adı bir neçə xanaya yazmaqla element həmin xanaları birləşdirir, ayrıca `colspan`/`rowspan` lazım deyil.
 
```
"grid1 grid2 grid2"   ← grid2 iki sütun tutur (geniş kart)
"grid1 grid3 grid4"   ← grid1 iki sıra tutur (uzun kart)
"grid5 grid5 grid6"   ← grid5 iki sütun tutur
```
 
---
 
### Vacib qeyd — `%` vs `fr`
 
Sütun genişliyi üçün `%` əvəzinə `fr` istifadə etmək tövsiyə olunur.
 
`30% 30% 30%` — `gap` əlavə olunanda ümumi en 90% + gap olur, overflow riski var.
 
`repeat(3, 1fr)` — `gap` çıxıldıqdan sonra qalan yer bərabər bölünür, overflow olmur.
 
---
 
### Responsive davranış
 
`@media` sorğusu ilə kiçik ekranlarda `grid-template-areas` yenidən təyin oluna bilər. Eyni `grid-area` adları qaldığı üçün child elementlərə toxunmaq lazım gəlmir — yalnız container-in xəritəsi dəyişir.
 
---
 
## Ümumi xülasə
 
| Pattern | Əsas xüsusiyyət | İstifadə |
|---|---|---|
| Isolated Element | `margin: auto` boş yeri udur | Bir elementi qoparmaq |
| Grid Area | `grid-template-areas` ilə vizual xəritə | Mürəkkəb page layout, Bento Grid |