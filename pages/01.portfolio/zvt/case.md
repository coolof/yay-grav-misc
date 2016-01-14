---
title: Zero Vision Tool - Timeline
lead: Visualisera projekt över tid
preview: preview-zvt.png
background: ZVT ville  hitta ett sätt att visualisera hur deras projekt lever och utvecklas över tid.
my_role: Brainstorma fram hur sidan borde fungera, ta fram design samt prototyp.
color: 59afbe
preview_style: light
size: small

order_weight: 20
---

![](timeline-overview.jpg){.img-border}  
Överblick med alla projekt, alla har en start och eventuell slutpunkt. När sidan byggdes var det flera projekt som var på väg att avslutas vilket kommer göra tidslinjen lite roligare i framtiden.

## Uppbyggnad
Varje projekt har ett start- och eventuellt ett slutdatum som visas på överblicken. Väl inne på ett projekt finns en ganska rejäl _"Story"_ som sammanfattar vad projektet handlar om samt snabbinformation om t.ex. partners. Stänger man storyn kan man se projektets olika _"händelser"_ över tid, inne på varje händelse kan man hitta relaterade dokument mm.

![](timeline-story.jpg){.img-border}

## Lager på lager
För att visualisera hur storyn ligger över tidslinjen används skuggor för att skapa "lager". I moderna webbläsare blir även innehållet bakom storyn oskarpt (med `filter:blur();` i css) för att förstärka effekten yttrligare. Utöver skuggor används gradients och highlights för att skapa kontrast och djup.

![](timeline-item.jpg){.img-border}  
Händelse med kortfattad text om vad som hände på datumet ifråga. Varje händelse har även möjlighet att ha en film istället för bild.

![](timeline-docs.jpg){.img-border}  
Dokument på en händelse.