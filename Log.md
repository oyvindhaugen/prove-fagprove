<details>
  <summary>Onsdag <sub>05/02</sub></summary>
  I dag har jeg planlagt datamodel, skisser for app, og skrevet planleggings dokumentet. Ingenting er utenfor planen så langt.
</details>
<details>
  <summary>Torsdag <sub>06/02</sub></summary>
  <p>I dag har jeg laget SQL Objektene, som da langt er</p>
  <ul>
    <li>astp_OyvindHaugen_AddOrRemoveReaction</li>
    <li>astp_OyvindHaugen_CreateNewPost </li>
    <li>astp_OyvindHaugen_DeletePost</li>
    <li>atbl_OyvindHaugen_Posts
      <ul>
        <li>
          har lagt til TextContent her for å kunne støtte "preview" av tekst i registeret uten mye frontend prosessering. Egentlig bare en plaintext av HTMLContent.
        </li>
      </ul>
    </li>
    <li>atbl_OyvindHaugen_PostsReactions</li>
    <li>atbl_OyvindHaugen_PostsReactionsIcons</li>
    <li>aviw_OyvindHaugen_PostsReactions
      <ul>
        <li>Er et view som joiner inn Title på post og hvilken reaksjon som er blitt brukt</li>
      </ul>
    </li>
  </ul>
  <p>I dag har jeg også skrevet SQL Templates som er "maler" for de forskjellige views og triggers. Har skrevet dem siden om løsningen skal utvides i fremtiden sparer dette mye arbeid for utvikler.</p>
  <img src="images/logs/sqltemplate.png" alt="SQL template eksempel" width="500"/>
  <br/>
  <p>I dag har jeg også startet utvikling på appen, og har laget de starten av de tre bildene. Det er et lite avvik fra planen her som er at jeg velger å bruke noe som heter vue-router for å ha en "single page application", slik at det ikke blir loading mellom de forskjellige bildene.</p>
  <br/>
  <p>Utenom de tre avvikene (templates, vue-router, og TextContent) så har jeg følgt planen som jeg la.</p>
</details>
<details>
  <summary>
    Fredag <sub>07/02</sub>
  </summary>
  I dag har jeg kommet en god del på frontend delen, har lagt til støtte for editering, sletting, og lagring av poster. For editering har jeg implementert FroalaEditor som er en HTML markup editor som er tilgjengelig via Omega365 CTP. Har også skikkelig implemenert vue-router nå slik at hele appen er en sømløs erfaring uten merkbar lasting. Har også lagt til knappene for emoji, men har ikke implementert skikkelig. Nytt view i dag: aviw_OyvindHaugen_Posts. dette inneholder posts og en subselect json av alle reaksjonene. I dag fikk jeg også en endring, som var å legge til kategorisering med Tags. Det var allerede i tankene som en ekstra feature, men nå skal det implementeres som del av kjernefunksjonaliteten. Dette har jeg ikke begynt på, tenker å bli ferdig med reactions først, men jeg har litt ideer hvordan jeg skal implementere det. Tror faktisk ikke jeg har noen avvik i dag overraskende nok. 😆 
</details>
