---
title: Layline
lead: Onepage-sida med en god dos modern webbteknik.

background: "Ny hemsida till Understandits delägare Layline. Sidan skapades runt samma tid som Google visade upp sin Material Design vilket jag jag väldigt sugen att kolla närmare på."

my_role: "Jag hade helhets-ansvar över projektet. Allt från design till prototyp och vidare in i Drupal. Nyhetsflödet är byggt ihop med Joel Söderberg på Understandit."

preview: preview-layline.png

order_weight: 17

process:
    markdown: true
    twig: true
---

![](layline1.jpg)  
"Startsidan", alltså översta sektionen på sidan. Alla sektioner är minst 100% av skärmens höjd men kan även växa.

##Processen
Efter ett par korta möten med Layline satte jag upp en design i Photoshop. Eftersom navigation och animationer är svåra att visa den vägen blev nästa logiska steg att sätta upp en enkel prototyp. Denna byggdes i html och med samma less-struktur som på våra Drupal-sidor. På så vis kunde style:n senare enkelt lyftas in i Drupal utan större modifikation.

![](layline-olle.jpg)  
När sidan lanserades jobbade det två personer på Layline, det här är en av dem - Olle. Bilderna togs i samband med sidan och är utformade på ett sätt som gör dem enkla att använda som skalade bakgrundsbilder.

## CSS-animationer
Vi bestämde tidigt att lägga lite extra krut på modern webbteknik för att kunna använda Layline som ett bra exempel på vad man kan göra på webben idag. En stor del i detta är de animationer som förekommer flitigt på sidan. Under finns ett exempel på hur sidans *innehav* visas när besökaren scrollar till den sektionen. Animationerna är inspirerade av Googles Material Design.

<ul class="layline-case-anim animated">
	<li>{{ page.media['anim-item.png'].html() }}</li>
	<li>{{ page.media['anim-item.png'].html() }}</li>
	<li>{{ page.media['anim-item.png'].html() }}</li>
	<li>{{ page.media['anim-item.png'].html() }}</li>
	<li>{{ page.media['anim-item.png'].html() }}</li>
	<li>{{ page.media['anim-item.png'].html() }}</li>
	<li>{{ page.media['anim-item.png'].html() }}</li>
	<li>{{ page.media['anim-item.png'].html() }}</li>
</ul>


![](layline-case.png)  
Case-listning på sidan.

## Inlästa nyheter
Nyheterna på sidan hämtas via RSS. Layline har även möjlighet att skapa egna nyheter. RSS-syncningen är utvecklad i sammarbete med [Joel Söderberg](http://joelsoderberg.se/) på Understandit och använder [Feeds-modulen](https://www.drupal.org/project/feeds) till Drupal.

![](layline-news.jpg)  
Nyhetslistning på "startsidan", inne i filtret finns även möjlighet att filtrera på företag mm.

![](layline-map.jpg)
