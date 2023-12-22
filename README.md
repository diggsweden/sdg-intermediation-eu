![Logo](/images/digg.png)

# SDG Bevishämtning, inom det tekniska systemet för bevisutbyte
Här finns beskrivningen av API:et för intermediationEU vilket är Diggs intermediära plattform för att erbjuda svenska behöriga myndigheter möjligheten att hämta bevis via det tekniska systemet för bevisutbyte (OOTS).

## Översiktligt flöde
* Bevishämtning, svenskt onlinfeförarande hämtar bevis från annat medlemsland
```mermaid
flowchart LR
    subgraph Medlemsland
        OMS(OOTS-nod MS)
        FG(Förhandsgranskning MS)
    end
    subgraph Digg
        AT(SDG Auktorisationstjänst)
        OSE(OOTS-nod SE)
        BH(Bevishämtning)
    end
            OLF(Onlineförfarande)-->AT
            OLF-->BH
            BH-->OSE
            OSE-->OMS
            OLF-->FG
    
```
*Diagram 1: Flödesdiagram för bevishämtning*




### Flödesbeskrivning översiktligt flöde

* Använderaren i ett onlineförfarande vill hämta ett bevis från annat medlemsland
* E-tjänsten skickar en signerad begäran om åtkomst till SDG Auktorisationstjänst
* Auktorisationstjänsten validerar begäran och kontrollerar att e-tjänsten tillhör en behörig myndighet
* Auktorisationstjänsten ställer ut ett åtkomstintyg till e-tjänsten
* E-tjänsten anropar Bevishämtningstjänsten och bifogar åtkomstintyget
* Bevishämtningstjänsten validerar att åtkomstintyget är signerat av betrodd auktorisationstjänst
* Bevishämtningstjänsten gör en bevisbegäran via OOTS-SE
* Andvändaren omdirigeras till bevislämnande lands förhandsgranskningstjänst
* Användaren väljer att dela beviset i förhandsgranskningstjänsten varpå beviset levereras över OOTS till bevishämtningstjänsten
* Onlineförfarandet hämtar beviset och låter användaren nyttja det i e-tjänsten


## Detaljerat flöde

```mermaid
sequenceDiagram
autonumber
box Förfarande
participant W as Webläsare
participant OF as e-tjänst
end
box SDG OOTS
participant AT as Auktorisationstjänst
participant BT as Bevishämtning 
participant OTSE as OOTS SE
end
box Annat medlemsland
participant OTMS as OOTS MS
participant MSOF as Förhandsgranskning MS
participant MSBP as Bevisproducent MS
end
W->>OF: Begär bevis
Note right of OF: Authentisering & auktorisation
OF-->OF: eIdas Autetentisering
OF->>AT: Access Token Request
AT-->>OF: Access Token Grant (accesstoken)
Opt Token expired
OF->>AT: Access Token Request(refresh token)
AT-->OF: Access Token Grant (accesstoken)
end
OF->>+BT: /preview-link (accesstoken)
BT->>BT: Validate Access Token
BT->>OTSE: Bevisbegäran
OTSE->>OTMS: Bevisbegäran
OTMS->>OTSE: Svar på bevisbegäran
OTSE->>BT: Svar på bevisbegäran
BT-->>-OF: Svar på bevisbegäran
BT->>OTSE: Bevisbegäran 2
OTSE->>OTMS: Bevisbegäran 2
OF->>W: Omdirigering till Förhandsgranskning MS
W-->>MSOF: omdirigering
MSOF->>MSOF: Återautentisering
MSOF->>+MSBP: Hämta bevis
MSBP-->>-MSOF: Bevissvar
MSOF->>MSOF: Godkänn bevisdelning
MSOF-->>W: omdirigering
W->>OF: Visa bevis
MSOF->>OTMS: Svar på bevisbegäran
OTMS->>OTSE: Svar på bevisbegäran
OTSE->>BT: Svar på bevisbegäran
loop Polla efter svar
OF->>+BT: Hämta bevis /files
BT-->>-OF: Bevissvar
end
```
*Diagram 2: Sekvensdiagram för bevishämtning*

### Flödesbeskrivning detaljerat flöde
