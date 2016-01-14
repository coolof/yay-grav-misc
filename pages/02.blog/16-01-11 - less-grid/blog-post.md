---
title: Världens kanske enklaste LESS-grid
lead: Ett mycket enkelt men samtigit väldigt flexibelt grid i less
date: 11-01-2016 23:40
slug: 2016-01-11-less-grid
---

Detta grid utgår från padding och %-värden istället för som ofta fasta bredder och marginaler. Med hjälp av `box-sizing: border-box` (som jag själv oftast sätter på *) räknas padding inuti elementets bredd istället för att göra det större. Detta innebär att 4 element med `width: 25%;` får plats bredvid varandra oavsett vilken padding de har.

Eftersom vi inte längre behöver räkna på bredder hit och dit blir griden extremt flexibel, anpassar sig automatiskt efter sin parents bredd och är väldigt lätt att modifiera, varje gång det används om så är nödvändigt. Här är mixinen:

``` scss
.clearfix() {
  &:after {
    content: "";
    display: table;
    clear: both;
  }
}

/* -----------------------
 One grid to rule them all
 ------------------------- */
@grid-gutter: 32px;
@grid-size: 12;

/* Grid container inside centered container */
.grid-container (@gutter: @grid-gutter) {
  .clearfix();
  margin-left: -@gutter/2;
  margin-right: -@gutter/2;
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
}
/* Grid item, returns % values */
.grid(@num: 1,@total: @grid-size,@gutter: @grid-gutter, @float: left) {
  @gridwidth: 100%/@total;
  @width: @gridwidth * @num;

  float: @float;
  width: @width;
  padding: 0 @gutter/2;
}
```

Jag har oftast en förbestämd `@gutter` som grund för alla marginaler och storlekar på sidan och sätter därför oftast `@grid-gutter: @gutter;`. Vill man inte ha något mellanrum mellan elementen sätter man helt enkelt `@grid-gutter: 0px`.

Mixinen förutsätter att du har minst en parent till dina grid-element samt att eventuella bakgrunder sätts på element inuti grid-elementet istället för direkt på grid-elementet (finns vägar runt detta med modern css).

En stor styrka med denna princip är att du väldigt enkelt kan skapa responsiva listor med t.ex. 3 element i bredd med fasta avstånd mellan varje grid-element. Eftersom vi kan ändra antalet kolumner i griden varje gång det används är det inte svårare än att sätta `.grid(1,3);`.

Nedan finns just ett sådant exempel:

### Markup
``` html
<ul class="wrapper">
  <li><img src="img1.png" alt="alt" /></li>
  <li><img src="img2.png" alt="alt" /></li>
  <li><img src="img3.png" alt="alt" /></li>
  <li><img src="img4.png" alt="alt" /></li>
  <li><img src="img5.png" alt="alt" /></li>
  <li><img src="img6.png" alt="alt" /></li>
</ul>
```

### LESS
``` scss
@new-gutter: 48px;

.wrapper {
  .grid-container(@new-gutter);
  
  li {
    .grid(1,3,@new-gutter);
  }
}
```

Resultatet av exemplet ovan är en lista där varje element tar upp 1/3 av bredden med 48px mellanrum. Eftersom vi i det här fallet sätter en ny `@grid-gutter` blir det enklast att göra detta som en variabel som båda mixinerna sedan använder. I de flesta fall vill vi så klart använda default.

## Begränsingar
Eftersom `.grid-container()` sätter en negativ marginal behöver vi se till så att någon av dess parents har en padding eller marginal till kanterna på sidan som är minst lika stor. En alternativ lösning skulle kunna vara `overflow-x: hidden` på någon av dess parents (exempelvis body). Om `@grid-gutter` är 0 behöver vi inte tänka på detta eftersom marginalen också blir 0 (eller närmare bestämt -0).
