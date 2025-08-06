# Specialsport

## Systemer
* Donorfy: [app.donorfy.com](https://app.donorfy.com/)
* Hjemmeside: [specialsport.dk](https://specialsport.dk/)
* Specialsport Guiden: [https://specialsportguide.com](https://specialsportguide.com)
* Trello:[https://trello.com](https://trello.com/) : Bruges til at følge 
* Sharepoint?
* 

## Terminologi


## Åbne spørgsmål
Hvordan kan jeg tilgå Azure databasen

## Hvilke ønsker er der til ny funktionalitet

### Indlæse fra Trello
#### Trello Export funktionalitet
Eksport funktionaliteten i Trello er ved at blive afskaffet i Trello.
Den eksporterer i en blanding af csv og json
Formatet er ikke dokumenteret, så det er ikke lige til at trække data ud på en truktureret måde, tror mest det anvendes om en mulighed for backup
#### Trello REST API
Der er dog et REST API, som kan anvendet til at hente data ud på en mere struktureret måde. Dette kræver at man laver en såkaldt Trello Power-Up og får en Api nøgle.
Denne nøgle skal så bruger til alle kald der henter information, den kan også skrive til Trello boards
Sikkerhedsrisiko: Der er en stor risiko ved denne da enhver med adgang til Api nøglen kan læse, skrive og slette alt i alle Trello boards (nøglen har samme rettigheder som brugeren der oprette nøglen)

### Integration med Office365


### Genbruge  entitetsoplysninger fra Donorfy når man arbejder i Trello
Hvilke data drejer det sig om? (disse data skal være i begge systemer)
Findes både data fra Donorfy og modtager systemet i Azure databasen?

Skal data kopeieres i Azure databasen fra Donory til andre systemer, og i givet fald hvilke



### Evt ønsker til rapportering
