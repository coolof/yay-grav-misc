---
title: En modern vertical align
lead: Med modern css kan man göra mycket kul, även effektivisera vertical-align
date: 23-11-2015 23:55
slug: 2015-11-23-grav

published: false
---
Alla som jobbat med css ett tag känner till dilemmat med `vertical-align`. Först måste jag förstå **hur** det fungerar, eller snarare hur och när det **inte** fungerar. Sedan måste man välja ett av ett antal ganska dåliga hack för att lyckas, alla med sina begränsnigar.

Tills nu, jag ramlade över [den här lösningen](http://zerosixthree.se/vertical-align-anything-with-just-3-lines-of-css/) för lite sen och den en genial (den är också knappast ny ser jag men för mig var den det). Bortsett från att den inte fungerar i gamla webbläsare men det blir ett mindre och mindre problem för varje dag som går.

```
.center-me {
	position: relative;/* Fungerar även med absolute och fixed */
	top: 50%;
	transform: translateY(-50%);
}
```

## Inte bara vertikalt

Principen kan också användas för att centrera horisontella element som är absolute. Vi måste byta ut vissa värden men principen är densamma:

```
.center-me {
	position: absolute;
	left: 50%;
	transform: translateX(-50%);
}
```

Detta fungerar lika bra om elementet har en fast bredd som om det inte har det.

## Less-mixin

Notera att elementet även behöver ha `position:` `relative`, `absolute` eller `fixed`.

```
//Center vertically
.align-middle() {
  top: 50%;
  -webkit-transform: translateY(-50%);
  -ms-transform: translateY(-50%);
  -o-transform: translateY(-50%);
  transform: translateY(-50%);
}
//Center horizontally
.align-center() {
  left: 50%;
  -webkit-transform: translateX(-50%);
  -ms-transform: translateX(-50%);
  -o-transform: translateX(-50%);
  transform: translateX(-50%);
}

/* Använding */
.element {
  .align-middle();
  position: relative;
}
```