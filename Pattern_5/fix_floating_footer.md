# CSS Grid — Fix Floating Footer Pattern
 
## Problem nədir?
 
Səhifədə kontent az olduqda footer yuxarı qalxır — səhifənin altına yapışmır. Bu xüsusilə az məlumat olan səhifələrdə (login, 404, boş state) görünür.
 
```
┌──────────────────┐
│ Header           │
├──────────────────┤
│ Az kontent       │
├──────────────────┤
│ Footer           │  ← yuxarıda qalır
│                  │
│   (boşluq)       │
└──────────────────┘
```
 
---
 
## Həll — Grid ilə
 
`min-height: 100vh` + `grid-template-rows: auto 1fr auto` birlikdə istifadə edilir.
 
```
┌──────────────────┐
│ Header (auto)    │  ← öz hündürlüyü qədər
├──────────────────┤
│                  │
│ Main (1fr)       │  ← qalan bütün boşluğu tutur
│                  │
├──────────────────┤
│ Footer (auto)    │  ← öz hündürlüyü qədər, həmişə aşağıda
└──────────────────┘
```
 
---
 
## Məntiq
 
**`min-height: 100vh`** — wrapper-in ən azı ekran hündürlüyü qədər olmasını təmin edir. Kontent çox olduqda böyüyə bilir.
 
**`auto`** — element öz content-i qədər yer tutur, nə az nə çox.
 
**`1fr`** — `auto`-lar öz yerlərini aldıqdan sonra qalan **bütün boşluğu** tutur. Bu boşluq `main`-i aşağıya uzadır və footer-i səhifənin dibinə sıxışdırır.
 
---
 
## `position: absolute` ilə müqayisə
 
Footer-i aşağıya yapışdırmaq üçün köhnə üsul `position: absolute` idi — amma bu üsulun problemləri var:
 
| | Grid (`1fr`) | `position: absolute` |
|---|---|---|
| Kontent çox olanda | Footer aşağıya düşür | Footer kontenti örtür |
| Kod sadəliyi | Sadə | Mürəkkəb, hesablama lazım |
| Responsive | Avtomatik | Əlavə iş lazım |
 
---
 
## Xülasə
 
Footer-i həmişə aşağıda saxlamaq üçün:  
`min-height: 100vh` → wrapper ekranı tutur.  
`grid-template-rows: auto 1fr auto` → `1fr` boşluğu udaraq footer-i aşağıya sıxışdırır.  
`position: absolute` lazım deyil, kontent çox olanda da layout pozulmur.