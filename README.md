# Specialsport

## Systemer
* Donorfy: [app.donorfy.com](https://app.donorfy.com/)
* Hjemmeside: [specialsport.dk](https://specialsport.dk/)
* Specialsport Guiden: [https://specialsportguide.com](https://specialsportguide.com)
* Trello:[https://trello.com](https://trello.com/) : Bruges til at følge 
* Sharepoint?
* 

## Terminologi
* Entitet: Dette dækker og de ting der registeres i Donorfy.
  * Entiteter indeles i entitetstyperne individ, hold og forening.
  * Entiteter har typisk en profil med kontaktoplysninger, tags
  * Entiteter har typisk en timeline bestående af aktiviteter.
* Individ(entitetstype): Dækker personer, dette er typisk individer der ønsker at deltage på hold eller frivillige eller ansatte i specialsport
* Hold (entitetstype): Dækker de hold som individer kan tilmelde sig, er typisk knyttet til en forening
* Forening (entitetstype): Dækker de foreninger som har holdene. Er typisk knyttet til et eller flere hold.
* Aktivitet: Der kan registereres aktiviteter på entiteter. Aktivieter
* Forløb: Viser 


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
