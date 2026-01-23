

## Villkor för användning av Intermediation-EU API (SDG Uppslag och Bevishämtning)

**Version:** 1.0
**Gäller från och med:** [2026-06-01]
**Tillhandahållare:** Myndigheten för digital förvaltning (Digg)


### 1. Om tjänsten

Intermediation-EU API (”**API:t**”) är en teknisk tjänst som tillhandahålls av Digg för att möjliggöra uppslag och hämtning av bevis (”**evidens**”) från andra medlemsstater inom ramen för det tekniska systemet för bevisutbyte (Once-Only Technical System, OOTS) enligt Single Digital Gateway-förordningen (EU) 2018/1724 med tillhörande rättsakter.([GitHub][1])

API:t är avsett att användas av svenska behöriga myndigheter och deras e-tjänster (”**konsumenter**”) för att, med användarens samtycke och i enlighet med tillämplig rätt, hämta nödvändiga bevis från andra medlemsstater.

---

### 2. Tillämpning och accept av villkoren

Dessa villkor (”**Villkoren**”) reglerar användningen av API:t.
Genom att:

* registrera en klient/applikation för åtkomst till API:t,
* eller anropa API:t med giltiga autentiseringsuppgifter,

accepterar konsumenten Villkoren för egen och eventuella underleverantörers användning.

Om konsumenten inte accepterar Villkoren får API:t inte användas.

---

### 3. Behöriga användare

3.1 **Behörig organisation**
API:t får endast användas av:

* svenska myndigheter eller andra organisationer som enligt lag eller förordning är behöriga att handlägga ärenden där bevis kan hämtas via OOTS, och
* som har ingått Anslutningsavtal med Digg
* som har godkänts av Digg för anslutning till API:t.

3.2 **Underleverantörer**
Konsumenten får anlita underleverantörer (t.ex. IT-driftsleverantör) för teknisk användning av API:t, under förutsättning att:

* underleverantören endast använder API:t för konsumentens räkning, och
* konsumenten säkerställer att underleverantören följer dessa Villkor.

Konsumenten ansvarar gentemot Digg för underleverantörers användning.

---

### 4. Tillåten användning

4.1 **Ändamål**
API:t får endast användas för att:


* i enlighet med tillämplig lagstiftning, inklusive SDG-förordningen och nationella regler om ärendehantering, dataskydd och sekretess,
* i enlighet med Anslutningsavtal,
* initiera uppslag och hämtning av bevis via OOTS från andra medlemsstater,
* ta emot, hämta och vidarebearbeta bevis som en del av ett pågående administrativt förfarande.

4.2 **Förbjuden användning**
API:t får inte användas för att:

* hämta bevis utan rättslig grund eller utan stöd i ett konkret ärende,
* kringgå eller försöka kringgå säkerhetsmekanismer (t.ex. autentisering, auktorisering, rate-limit),
* utsätta tjänsten för onormalt hög belastning, t.ex. genom massanrop, stress-tester eller automatiserade uppslag som inte är motiverade av riktiga ärenden,
* vidareförmedla API-åtkomst till tredje part som inte omfattas av konsumentens uppdrag eller avtal.

---

### 5. Tekniska förutsättningar, autentisering och åtkomst

5.1 **Tekniska krav**
För att använda API:t krävs att konsumenten:

* följer den publicerade OpenAPI-specifikationen för `sdg-intermediation-eu` (struktur, endpoints, statuskoder m.m.),
* uppfyller de tekniska krav som Digg i övrigt anger i dokumentation och integrationsanvisningar,
* håller sin tekniska miljö uppdaterad och säker (certifikat, protokoll, kryptering, m.m.).

5.2 **Autentisering och auktorisation**
Åtkomst till API:t skyddas med [OAuth 2.0/OpenID Connect-baserad] autentisering via Diggs auktorisationstjänst inom SDG-systemet.([GitHub][2])

Konsumenten ansvarar för att:

* klienthemligheter, certifikat och andra autentiseringsuppgifter hanteras säkert,
* endast behöriga system och personer har åtkomst till dessa uppgifter,
* omedelbart meddela Digg vid misstanke om intrång eller röjda autentiseringsuppgifter.

Digg får när som helst spärra eller begränsa en konsuments åtkomst vid misstanke om missbruk, säkerhetsincident eller brott mot Villkoren.

5.3 **Rate limiting och kvoter**
Digg kan tillämpa begränsningar för antalet anrop per tidsenhet (”rate limiting”) och andra kvoter för att skydda tjänstens stabilitet.

* Aktuella gränsvärden anges i dokumentationen eller genom tekniska svarshuvuden.
* Vid upprepad överskridning kan Digg temporärt eller permanent begränsa konsumentens åtkomst.

---

### 6. Behandling av personuppgifter

6.1 **Roller enligt dataskyddsregelverket**
När konsumenten använder API:t för att hämta bevis är konsumenten personuppgiftsansvarig för den fortsatta behandlingen i sin ärendehandläggning. Digg behandlar personuppgifter i samband med API:t för att tillhandahålla tjänsten och är då personuppgiftsbiträde till konsumenten för dessa delar.

Rollfördelningen preciseras i Anslutningsavtal samt personuppgiftsbiträdesavtal.

6.2 **Rättslig grund**
Konsumenten ansvarar för att:

* det finns giltig rättslig grund för varje användning av API:t (t.ex. rättslig förpliktelse eller uppgift av allmänt intresse),
* behandlingen sker i enlighet med dataskyddsförordningen (EU) 2016/679 och kompletterande svensk lagstiftning (dataskyddslagen m.fl.).

6.3 **Överföring och lagring av bevis**
Konsumenten ska säkerställa att:

* mottagna bevis endast används för det specifika förfarande och ändamål de hämtats för,
* lagringstid och gallring följer gällande lagstiftning och interna informationshanteringsregler,
* åtkomst till bevis begränsas i enlighet med principen om minsta möjliga åtkomst.

6.4 **Informationssäkerhet**
Konsumenten ska vidta lämpliga tekniska och organisatoriska säkerhetsåtgärder, i nivå med bl.a. NIS-, NIS2- och informationssäkerhetsföreskrifter när så är tillämpligt, för att skydda personuppgifter och andra skyddsvärda uppgifter som hanteras via API:t.

---

### 7. Loggning, spårbarhet och statistik

7.1 **Loggning hos Digg**
Digg loggar användningen av API:t, inklusive men inte begränsat till:

* tidpunkt för anrop,
* klient-/systemidentitet,
* endpoint och tekniska parametrar,
* tekniska felkoder.

Syftet är att säkerställa spårbarhet, säkerhet, felavhjälpning, incidentutredning och tjänsteutveckling.

Loggar sparas under den tid som krävs för dessa ändamål och i enlighet med tillämplig lagstiftning om arkiv, offentlighet och dataskydd.

7.2 **Loggning hos konsumenten**
Konsumenten bör föra ändamålsenlig loggning över sin användning av API:t, så att:

* behörighetskontroll och spårbarhet kan säkerställas,
* incidenter och oegentligheter kan utredas.

---

### 8. Tillgänglighet, drift och support

8.1 **Tillgänglighet**
Digg eftersträvar hög tillgänglighet för API:t men lämnar ingen garanterad tjänstenivå om inte annat följer av separat avtal.

Tjänsten kan vara otillgänglig vid:

* planerade driftavbrott (underhåll, uppgraderingar),
* akuta åtgärder för att hantera incidenter eller sårbarheter,
* störningar i underliggande nationella eller europeiska komponenter (t.ex. OOTS-noder, Evidence Broker, Data Service Directory).([GitHub][1])

Digg strävar efter att informera konsumenten i god tid före planerade avbrott via dokumentation, e-postlista eller annan överenskommen kanal.

8.2 **Support**
Basnivå för support omfattar:

* mottagande av felrapporter och frågor via [supportkanal, t.ex. e-postadress eller ärendehanteringssystem],
* hantering under Diggs ordinarie arbetstid om inte annat avtalats.

---

### 9. Förändringar av API:t

9.1 **Versioner och bakåtkompatibilitet**
Digg kan vidareutveckla API:t, vilket kan innebära:

* införande av nya versioner av API:t,
* ändringar i befintliga endpoints, scheman eller säkerhetsmekanismer,
* avveckling (deprecation) av äldre versioner.

Digg strävar efter:

* att i normalfallet ge skälig förvarning innan förändringar som bryter bakåtkompatibilitet, och
* att dokumentera förändringar i ändringslogg (changelog) kopplad till OpenAPI-specifikationen.

9.2 **Avveckling**
Digg får avveckla API:t helt eller delvis om:

* det ersätts av annan nationell eller europeisk lösning,
* regelverk eller tekniska förutsättningar förändras,
* särskilda skäl föreligger (t.ex. säkerhetsrisker).

Vid planerad avveckling informeras konsumenten i skälig tid.

---

### 10. Ansvarsbegränsning

10.1 **Ingen garanti**
API:t tillhandahålls ”i befintligt skick”. Digg lämnar inga garantier avseende:

* att API:t är felfritt eller alltid tillgängligt,
* att data från andra medlemsstater är fullständiga, korrekta eller uppdaterade.

10.2 **Indirekt skada m.m.**
Digg ansvarar inte för:

* indirekta skador, följdskador, utebliven vinst eller annan ekonomisk följdskada,
* skada som uppkommer till följd av störningar i externa system (andra medlemsstaters noder, EU-komponenter m.m.).

10.3 **Konsumentens ansvar**
Konsumenten ansvarar för:

* sin egen användning av API:t, inklusive hur mottagna bevis används i ärendehandläggning,
* att rutiner, processer och system uppfyller tillämplig lagstiftning,
* skador som orsakas Digg eller tredje man genom användning i strid med Villkoren eller gällande rätt.

---

### 11. Immateriella rättigheter och licens

11.1 **Specifikation vs. driftstjänst**
OpenAPI-specifikationen och dokumentationen för API:t är publicerade under en öppen licens (CC0-1.0) i Diggs GitHub-kodförråd.([GitHub][1])

Detta innebär att specifikationen får användas fritt under angivna licensvillkor.

11.2 **API-tjänsten**
Själva driftstjänsten (API:t) är inte licensierad som öppen källkod. Rätten att använda tjänsten följer av:

* dessa Villkor, samt
* eventuella särskilda avtal mellan Digg och konsumenten.

---

### 12. Ändringar av Villkoren

Digg får ändra dessa Villkor. Vid väsentliga ändringar informerar Digg konsumenten via lämplig kanal, t.ex.:

* uppdatering av denna sida,
* meddelande i utvecklardokumentation eller integrationskanal,
* e-post eller motsvarande.

Fortsatt användning av API:t efter att ändrade Villkor publicerats innebär att konsumenten accepterar de nya Villkoren.

---

### 13. Tillämplig lag och tvister

Villkoren regleras av svensk rätt.
Tvister med anledning av Villkoren eller användningen av API:t ska i första hand lösas genom dialog mellan parterna. Om tvisten inte kan lösas genom förhandling får den prövas av svensk allmän domstol med Stockholms tingsrätt som första instans.

---

### 14. Kontakt

Frågor om API:t, dessa Villkor eller anslutning skickas till:

> **Myndigheten för digital förvaltning (Digg)**
> [Enhet/funktion]
> E-post: [sdg@digg.se](mailto:sdg@digg.se)
> Webb: (https://github.com/diggsweden/sdg-intermediation-eu)

---
