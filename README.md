# Specialsport

## Terminologi
* Entitet: Dette dækker og de ting der registeres i Donorfy. Alle entiteter har et unikt ID i Donorfy
  * Entiteter indeles i entitetstyperne individ, hold og forening.
  * Entiteter har typisk en profil med kontaktoplysninger og tags
  * Entiteter har typisk en timeline bestående af aktiviteter.
* Individ(entitetstype): Dækker personer, dette er typisk individer der ønsker at deltage på hold eller frivillige eller ansatte i specialsport
* Hold (entitetstype): Dækker de hold som individer kan tilmelde sig, er typisk knyttet til en forening
* Forening (entitetstype): Dækker de foreninger som har holdene. Er typisk knyttet til et eller flere hold.
* Aktivitet: Der kan registereres aktiviteter på entiteter. Aktivieter stemples altid med et datostempel samt hvornår de er oprettet for at danne en timeline.
* Forløb (Trelloboard): Viser kort for de individer der deltager i forløbet. Når et individ kommer videre i forløbet flyttes kortet til en ny liste på boardet.

## Systemer
* Donorfy: [app.donorfy.com](https://app.donorfy.com)
* Hjemmeside: [specialsport.dk](https://specialsport.dk)
* Specialsport Guiden: [https://specialsportguide.com](https://specialsportguide.com)
* Trello:[https://trello.com](https://trello.com) : Bruges til at lave forløb
* BusinessCentral: ?
* Survey Exact: [https://www.survey-xact.dk](https://www.survey-xact.dk)

### Donorfy
Bruges til at oprette entiteter, entiteter for deres unikke ID når de oprettes i Donorfy
Her kan tilføjes kontaktoplysninger og tags til entiteter, ligesom der kan oprettes aktiviteter i entitetens timeline
Entiteter kan knyttes til hinanden, f.eks. kan der knyttes flere hold til en forening.

#### Håndtering af tags og tag kategorier
Man kan se tags og tag kategorier i Donorfy ved at gå til Settings -> Configuration -> Vælge "Tags and Tag Categories" -> vælge en tag kategori fra listen

#### Forms
Man kan lave forms som kan bruges til at modtage input fra hjemmesiden.
F.eks. kan man lave en form for at tilføje en forening. 
I formen angiver man hvilke felter brugeren skal se på hjemmesiden og evt. andet tekst. 
Dette præsenteres så på hjemmesiden og brugeren på hjemmesiden kan direkte oprette en forening

### Trello
Består af boards med lister og kort
Der kan f.eks. være et board med forløb ad sportsaktiviteter i hovedstaden, hvor hver liste indeholder de individer der er igang med forløbet.
Kort har labels beskrivelse og aktiviteter og checkliste med checklist items. Alle kort har et custom ID felt der svarer til entitet ID i Donofy




## Hvilke ønsker er der til ny funktionalitet

### Indlæse fra Trello
Hvad skal man bruge disse data til i databasen?
* Man kan måske få et overblik over hvilke entiteter der findes på de enkelte boards og hvilken status (liste) de er i
* Indholdet af det enkelte kort er ikke struktureret data men blot en mængde tekst, så man kan ikke f.eks. søge på navn eller kommune eller andet.
#### Option: Trello Export funktionalitet
Eksport funktionaliteten i Trello er ved at blive afskaffet i Trello.
Den eksporterer i en blanding af csv og json
Formatet er ikke dokumenteret, så det er ikke lige til at trække data ud på en truktureret måde, tror mest det anvendes om en mulighed for backup
#### Option: Trello REST API
Der er dog et REST API, som kan anvendes til at hente data ud på en mere struktureret måde. Dette kræver at man laver en såkaldt Trello Power-Up og får en Api nøgle.
Denne nøgle skal så bruges til alle kald der henter information, den kan også skrive til Trello boards
Sikkerhedsrisiko: Der er en stor risiko ved denne da enhver med adgang til Api nøglen kan læse, skrive og slette alt i alle Trello boards (nøglen har samme rettigheder som brugeren der oprette nøglen)

### Integration med Office365


### Genbruge  entitetsoplysninger fra Donorfy når man arbejder i Trello
Hvilke data drejer det sig om? (disse data skal være i begge systemer)
Findes både data fra Donorfy og modtager systemet i Azure databasen?
Skal data kopeieres i Azure databasen fra Donory til andre systemer, og i givet fald hvilke

#### Option: Kopier data Donorfy til Trelloboards
Det er ikke muligt på en struktuereret måde at overføre f.eks. adresseoplysninger fra Donorfy til de enkelte kort i Trello, selvom der er en reference i Trello til de pågældende entitets id fra Donorfy

#### Option: Lave et program på den enkelte maskine, hvor brugeren kan slå oplysninger op ud fra entitets id

## Åbne spørgsmål
Hvordan kan jeg tilgå Azure databasen


### Evt ønsker til rapportering
