---
title: Full bredd inuti element med en bredd
lead: Använd vw för att skapa sektioner på en sida med full bredd oberoende av elementets bredd.
date: 05-12-2015 00:21
slug: 2015-12-05-full-bredd
published: true
---

Tänk dig att du vill lägga till en ny sektion på en sida som går ut över hela fönstrets bredd. Någonstans högre upp i markupen sätts en bredd. Du skulle nu kunna skriva om sidans grund-css för att komma runt detta, eller ta till js. Eller, med modern css, kan du göra något mycket fiffigare.

Jag fick en idé när en kollega hade exakt det här problemet. Bredden på sidan sattes många steg upp men kunden ville ha en bakgrund som gick ut över hela fönstrets bredd. Lösningen är väldigt enkel.

```
.element {
  position: relative;
}
.element:before {
  content: "";
  position: absolute;
  z-index: -1;
  left: 50%;
  top: 0px;
  width: 100vw;
  height: 100%;
  margin-left: -50vw;
  background-color: #f5f5f5;
}
```

I exemplet ovan vill vi att vårt element (`.element`) behåller sin bredd för att följa sidans övriga layout men att vi bakom elementet lägger en bakgrundsfärg som går ut över hela fönstrets bredd. Bakgrundsfärgen läggs därför som `:before` istället för på själva elementet. Sektionen nedan är skapad på detta vis.

<div class="full-width-example">
  Bakgrunden går ut över hela sidan men innehållet anpassar sig efter övrigt innehåll.
</div>

### Så hur funkar det egentligen?

`left:50%` placerar elemenetet i mitten av sin parent, i det här fallet `.element` (eftersom vi satt denna som `position: relative`). `width:100vw` är detsamma som 100% av viewportens bredd. Slutligen sätter vi `margin-left: -50vw` för att putta ytan 50% av viewportens bredd åt vänster, dvs. 0px från vänster eftersom vi utgick från mitten (`left: 50%`).

Om vi istället vill flytta hela elementet längst till vänster snarare än skapa en bakgrund bakom det kan vi göra det så här:

```
.element {
  position: relative;
  left: 50%;
  width: 100vw;
  margin-left: -50vw;
}
```

### Mixin
Vi kan även enkelt skapa mixins för detta

```
/* Full width bg */
.full-width-bg(@bg: #f5f5f5) {
  position: relative;

  &:before {
    content: "";
    position: absolute;
    z-index: -1;
    left: 50%;
    top: 0px;
    width: 100vw;
    height: 100%;
    margin-left: -50vw;
    background-color: @bg;
  }
}

/* Full width container */
.full-width(@bg: #f5f5f5) {
  position: relative;
  left: 50%;
  width: 100vw;
  margin-left: -50vw;
  background-color: @bg;
}
```

### Begränsningar
Viewport-enheter [stöds i IE9+](http://caniuse.com/#feat=viewport-units) vilket därför inte borde vara någon större begränsning. I övrigt kräver exemplet ovan att `.element` är centrerad så att `left:50%` blir i mitten av viewporten.

Beroende på den övriga designen kan du även behöva ändra `z-index`. Tänk på att när du sätter en bakgrundsfärg bakom elementet med `:before` måste `z-index` vara lägre där än på elementet.

>>> **Scrollbars i OSX**  
>>> Om scrollbars visas i OSX tar de upp plats men räknas inte bort vid `100vw`. Eftersom detta är en inställning användaren gör (och som är default när man använder en vanlig mus) är det ingenting vi i sig kan hindra. Däremot finns det en enkel lösning som bör fungera i de allra flesta fall. Sätt `overflow-x: hidden;` på exempelvis body (eller annan valfri parent med full bredd).