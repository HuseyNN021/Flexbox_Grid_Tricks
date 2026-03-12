# CSS Grid — Card Layout Pattern
 
## Problem nədir?
 
Eyni card-da mətn uzunluğu fərqli olduqda button öz yerini dəyişir — bəzi kartlarda yuxarıda, bəzilərində aşağıda durur. Layout dağılmış görünür.
 
```
┌────────────┐  ┌────────────┐  ┌────────────┐
│ Title      │  │ Title      │  │ Title      │
│ Az mətn    │  │ Çox mətn   │  │ Orta mətn  │
│  [Button]  │  │ uzun uzun  │  │            │
└────────────┘  │ uzun uzun  │  │  [Button]  │
                │  [Button]  │  └────────────┘
                └────────────┘
```
 
---
 
## Həll — Grid ilə
 
`grid-template-rows: auto 1fr auto` — fix floating footer ilə eyni məntiq, bu dəfə card içinə tətbiq olunur.
 
```
┌────────────┐  ┌────────────┐  ┌────────────┐
│ Title      │  │ Title      │  │ Title      │
│            │  │            │  │            │
│ Az mətn    │  │ Çox mətn   │  │ Orta mətn  │
│            │  │ uzun uzun  │  │            │
│            │  │ uzun uzun  │  │            │
│  [Button]  │  │  [Button]  │  │  [Button]  │
└────────────┘  └────────────┘  └────────────┘
```
 
Bütün buttonlar həmişə aşağıda — mətn uzunluğundan asılı olmayaraq.
 
---
 
## Məntiq
 
**`h1` (auto)** — öz hündürlüyü qədər yer tutur.
 
**`p` (1fr)** — qalan bütün boşluğu tutur. Mətn az olduqda boşluq saxlanılır, çox olduqda böyüyür. Button-u həmişə aşağıya sıxışdırır.
 
**`button` (auto)** — öz hündürlüyü qədər yer tutur, həmişə card-ın altında qalır.
 
---
 
## Flex ilə alternativ həll
 
Eyni nəticəni Flexbox ilə də əldə etmək olar:
 
```css
.card {
    display: flex;
    flex-direction: column;
}
 
.card p {
    flex-grow: 1; /* p bütün boş yeri tutur, button aşağıya düşür */
}
```
 
| Xüsusiyyət    | Grid                                   | Flex                                      |
|---------------|----------------------------------------|-------------------------------------------|
| Üsul          | `grid-template-rows: auto 1fr auto`    | `flex-direction: column` + `flex-grow: 1` |
| Məntiq        | Sıraları əvvəlcədən təyin et           | p-yə böyü de, button aşağıya düşsün      |
| Oxunaqlılıq   | Struktur birbaşa görünür               | Bir az dolayı                             |
 
İkisi də düzgündür — grid daha dəqiq struktur verir, flex daha az kod tələb edir.
 
---
 
## Xülasə
 
Card içindəki elementləri sabit yerləşdirmək üçün card-ı grid et.  
`auto 1fr auto` — başlıq və button öz yerlərini alır, mətn aradakı boşluğu tutur.  
Bu pattern fix floating footer ilə eyni məntiqdir — böyük layout-da da, kiçik card-da da işləyir.
 