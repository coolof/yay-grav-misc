---
title: Designa med en minsta gemensamma nämnare
lead: Snabbt och varför du kan ha nytta av att hitta en
date: 12-01-2016 23:34
slug: 2016-01-11-minsta-namnare

published: false
---

Det kanske låter begränsande eller onödigt svårt. Men att hitta en minsta gemensamma storlek i din design kan förenkla väldigt mycket.

## Hitta din nämnare
Jag utgår från **8**, nördigt, enkelt och passande. Det spelar egentligen ingen roll vad värdet är, så länge det är enkelt för dig att komma ihåg och räkna på. Sedan hittar jag en grundmarginal, ett värde delbart med 8. Inte för stor, inte för liten, jag brukar utgå från det avståndet jag vill ha mellan paragrafer. På exempelvis yay.se är detta värde **32**, alltså 8\*4. Sedan använder jag detta värde som en grund för all storlek och positionering på sidan. Eftersom 32 är min basmarginal, inte för stor, inte för liten, blir det enkelt att hitta andra scenarion. Ibland vill man ha en rejälare marginal, kanske 48 (32\*1,5) eller t.om. 64 (32\*2). Ibland vill man ha en mindre marginal, t.ex. 24 (32\*0,75) eller 16 (32\*0,5).

### Radavstånd
Vidare använder jag samma värden på radavstånd, däremot inte slaviskt till 32 så klart utan det som passar. Ska det vara en längre text, t.ex. det här blogginlägget så passar 32 på, textstorleken är 20px och min line-height 32px (eller 1.6em om man så vill, alltså 32/20). Som du ser måste inte textstorleken följa samma mönster, så länge radavståndet gör det. Att slaviskt följa den minsta nämnaren hade gett oss alldeles för dålig precsision vad det gäller textstorlekar. På större texter där jag inte vill ha lika stort radavstånd brukar jag testa mig fram, säg att textstorleken är 32, då är nog 40 lagom radavstånd osv. Detsamma gäller så klart mindre texter (till 16 blir t.ex 24 lagom).

## Det praktiska
I Sketch använder jag helt enkelt dessa värden som en bas för hur jag bygger upp designen. Lägger jag till en knapp så funderar jag hur stor den kan vara för att följa min minsta nämnare. Avstånd mellan list-element likaså osv. osv. Väl i LESS brukar jag utgå från min grundmarginal, alltså 32 och spara det värden i variabeln `@gutter`.

### Testa
<a href="#" class="grid-toggle">Klicka här</a> för att slå på ett grid på sidan och se hur alla element anpassar sig efter detta. För tydlighets skulle utgår griden från 16 och därför kan vissa objekt hamna "mellan" två rader. Exempelvis kommentarerna under inlägget jobbar inte mot samma bas.