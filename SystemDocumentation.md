# System Dokumentasjon

## Innhold
- Oppsummering applikasjon
- Teknologier
- Database modell
- Sikkerhet
- Frontend

<details>
  <summary>
    Oppsummering applikasjon
  </summary>
  <p>Oppgaven denne applikasjonen skal utføre er å være et blogg verktøy. Målet var å kunne lage, endre, og slette blogg innlegg. Det skulle også være en måte å gi likes på, sammen med mulighet til å filtrere på kategorier. </p>
</details>
<details>
  <summary>
    Teknologier
  </summary>
  <ul>
    <li>Omega 365 CTP</li>
    <li>Microsoft SQL Server</li>
    <li>Vue.js 3 med TypeScript</li>
    <li>Bootstrap 5.3</li>
  </ul>
</details>
<details>
  <summary>
    Database modell
  </summary>
  <img src="/images/logs/datamodel_v2.png" alt="Datamodell" />
  <p>Det er egentlig en ganske enkel og konsis datamodell. Den består av 5 custom tabeller og 1 Omega 365 system tabell;</p>
  <ul>
    <li>Posts - hvor innholdet til poster er lagret sammen med metadata som hvem som laget posten, dato, og tittel.</li>
    <li>Topics - dette er tabellen som har alle kategoriene i seg, Posts har FK til denne.</li>
    <li>PostsTopics - dette er tabellen som linker sammen Posts og Topics, med FK til begge de tabellene.</li>
    <li>PostsReactionsIcons - dette er tabellen som har alle reaksjonsikonene som kan brukes på innlegg. Her ligger også metadata som om det er en default</li>
    <li>PostsReactions - dette er tabellen der alle reaksjoner legges inn, med FK til Posts og Icons</li>
    <li>Persons - dette er en system tabell som oppbevarer info om alle personer som er registrert i systemet. Alle tabellene har en FK til denne for informasjon om hvem som har laget/oppdatert data.</li>
  </ul>
</details>
<details>
  <summary>
    Sikkerhet
  </summary>
  <p>Sikkerheten i views er egentlig ganske enkel siden den sjekker bare om du lesetilgang på tabellen. For økt sikkerhet har brukere aldri direkte tilgang til tabeller. I stedet brukes views, ofte via en atbv. "atbv" står for Application Table View og brukes for å kontrollere hva en bruker kan se.</p>
  <p>Sikkerheten i triggere er litt mer avansert, siden her må det sjekkes på om du har redigering/slette tilganger. På tabellene som relaterer til Posts så sjekker den alltid om <em>du</em> er eier, siden bare eieren av et innlegg kan redigere og/eller slette det. Du skal allerede bli stoppet fra appen, men bør alltid ha en ekstra sjekk i databasen 😊</p>
  <p>All sikkerheten her ble skrevet med bruk av noe som heter SQL Templates, som gjør at du kan skrive en "template" og alle tabeller som oppfyller kravene får da den templaten i den autogenererte seksjonen. Dette sparer en del tid spesielt om du plutselig skal lage et par nye tabeller, eller vil gjøre endringer for mer enn en trigger/view</p>
</details>
<details>
  <summary>
    Frontend ting
  </summary>
  <p>Noe som skiller denne appen litt fra andre apper er at den bruker noe som heter "vue-router", dette gjør at det skal kjøres som en "single page application (SPA)". Siden hele appen kjører som en SPA, er det nesten null i lastetid, og appen føles veldig sømløs. Det er satt opp noen fallback mekanismer som 404 Not Found side, og redirigering om du prøver å gå til "/", så leder den deg til "/register". Ulempen med "vue-router" er jo at det er vanskligere å feilsøke når du har feil å router nivå, men fordelene utveier ulempene.</p>
  <p>Denne appen består av 3 primær komponenter, som er: Register, View, og Edit. Som navnene beskriver så er det for å se en oversikt over alle innlegg (med filtermuligheter), se hele innlegg på en større skjerm (med anbefalinger for andre innlegg på siden), og redigering av innlegg.</p>
  <p>Veldig sentralt i denne appen er BlogCard komponenten, den sørger for mesteparten av det viselle. Hele Register og View bruker denne på flere steder, og siden dette er en komponent er den lett å gjenbruke og gjøre endringer lett i hele løsningen.</p>
  <p>Siden denne appen er skrevet med bruk av rammeverket Omega 365 CTP, så brukes ett konsept som heter DataSources istedenfor direkte koblinger til en SQL Server. Disse DataSourcene er egentlig bare ett JSON-object som sendes inn til det sikrete APIet slik at den kjører verifisering og sender forespørselen videre til SQL Serveren. Ved bruk at dette konseptet sparer det mye av bryet som er å sette opp direkte koblinger, som da ikke er sikret.
  <p>Appen bruker også noe som heter Dynamic Loading, som gjør at den i starten ikke laster så mange innlegg, men kan raskt laste flere innlegg om bruker ønsker det og trykker på "Load more". Dette konseptet er bedre kjent som Pagination.</p>
  <p>Filteringen fungerer ved å ha to "paths" fra SQL Viewet som da er Topics (ID) og TopicsNames (Name). Topics brukes til å filtrere på med en "LIKE" clause i filterstringen. TopicsNames brukes for å rendere hvilke Topics et innlegg er kategorisert som.</p>
  <p>Reaksjoner fungerer ved at SQL Viewet lager en JSON av alle emojier som er blitt brukt/skal være tilgjengelige. Utifra det JSON-objectet renderer den reaksjonene som en "badge" på hvert innlegg. Det oppdaterer i DOMen dynamisk ved bruk at attributen som heter "key", som gjør at hver gang den endrer seg lastes komponenten på ny. I dette tilfellet står "key" som raden sitt Reactions JSON object, siden det endrer seg når du trykker på en reaksjon.</p>
</details>
