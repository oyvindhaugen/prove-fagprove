# Egenvurdering

## Oppsummering
Generelt føler jeg at jeg gjorde det ganske greit basert på tiden jeg hadde. Føler at jeg startet ganske sterkt med planleggingen, og føler jeg la en realistisk plan. Selv om jeg hadde noen små endringer fra original planen føler jeg at den var ganske bra laget. Selve utføringen gikk veldig greit med at jeg startet med SQL ting og sikkerhet, for da hadde jeg et mer realistisk tidsrom for frontend. 

## Utfordringer
Hadde litt problemer tidlig i utviklingen med Vue Router, siden dette var noe jeg aldri hadde brukt før, men fant etterhvert ut hvordan jeg kunne bruke det på en god måte. Hadde også en del problemstillinger angående dynamisk rendering i frontend, skapt av manglende unike keys. Dette løste jeg ved å bruke en NEWID i Reactions JSON objectet og brukte det som "key" per BlogCard. 

## Avvik
Jeg hadde et par avvik som er bedre spesifisert i ![systemdokumentasjonen](SystemDocumentation.md). Disse var bruk av VueRouter, bruk av proc for endring av innlegg, view som ikke ble brukt, lagre textcontent i database istedenfor en kalkulert verdi, bruk av SQL Templates, og manglende farger på topics.

Forsåvidt føler jeg at disse avvikene var en normal mengde, og at i det store hadde det ikke mye å si, og jeg føler at med planleggingen jeg gjorde så var det plenti med tid for disse avvikene uten å dette vekk fra planen.

## Endringer om jeg kunne gjøre det igjen
Om jeg kunne gjort dette igjen ville jeg definitivt drøftet mer med andre kollegaer om problemstillinger, som den soleklare feilen i filtreringen min som jeg ikke merket (i.e. "%1%" LIKE "1,2,3" ville også inkludert 21, eller 11, eller 12 etc.). Også med design aspekter ville jeg drøftet med kollegaer fordi jeg er enda ikke helt happy med hvordan det endte opp. Jeg ville også gjerne undersøkt mer innen SQL ting som lengder på datatyper (hvordan det bestemmer ting), seeking vs scanning, pen testing, hvordan APIet fungerer (mer detaljert) etc.   
