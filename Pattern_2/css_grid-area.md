# CSS Grid — Grid Area Pattern
 
## Nədir?
 
`grid-template-areas` — grid layout-u vizual olaraq **string xəritəsi** ilə təyin etmək üsuludur. Hər child elementə `grid-area` ilə ad verilir, container-də isə bu adlar sıralanıb yerləşdirilir.
 
---
 
## Məntiq
 
Container-də sütun və sıra sayı təyin olunur. Sonra `grid-template-areas`-da hər xana üçün ad yazılır. Eyni ad bir neçə xanada yazılarsa, həmin element o xanaları birləşdirib tutur.
 
```
"navbar navbar"     ← navbar 2 sütunu da tutur
"aside  main  "     ← aside sol, main sağ
"footer footer"     ← footer 2 sütunu da tutur
```
 
Hər child-a `grid-area: <ad>` verilir — container-dəki ada uyğun yerə düşür.
 
---
 
## Vacib qeydlər
 
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
 
---
 
## Nümunə — Bento Grid
 
Bento Grid, Grid Area-nın praktik tətbiq nümunəsidir. Müxtəlif ölçülü kartlar mozaik kimi yerləşdirilir — eyni adı bir neçə xanaya yazmaqla element həmin xanaları birləşdirir, ayrıca `colspan`/`rowspan` lazım deyil.
 
```
"grid1 grid2 grid2"   ← grid2 iki sütun tutur (geniş kart)
"grid1 grid3 grid4"   ← grid1 iki sıra tutur (uzun kart)
"grid5 grid5 grid6"   ← grid5 iki sütun tutur
```
 
---
 
## Vacib qeyd — `%` vs `fr`
 
Sütun genişliyi üçün `%` əvəzinə `fr` istifadə etmək tövsiyə olunur.
 
`30% 30% 30%` — `gap` əlavə olunanda ümumi en 90% + gap olur, overflow riski var.
 
`repeat(3, 1fr)` — `gap` çıxıldıqdan sonra qalan yer bərabər bölünür, overflow olmur.
 
---
 
## Responsive davranış
 
`@media` sorğusu ilə kiçik ekranlarda `grid-template-areas` yenidən təyin oluna bilər. Eyni `grid-area` adları qaldığı üçün child elementlərə toxunmaq lazım gəlmir — yalnız container-in xəritəsi dəyişir.
 
---
 
## Xülasə
 
`grid-template-areas` grid layout-u **vizual xəritə** kimi yazmağa imkan verir.  
Eyni adı bir neçə xanaya yazmaq → element həmin xanaları birləşdirir.  
Responsive etmək üçün yalnız container-in xəritəsini dəyişmək kifayətdir.
 