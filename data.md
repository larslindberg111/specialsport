Generelle betragtninger om at gemme data i evt. database
* Vi gemmer i første omgang kun data fra Donorfy
* For at gemme data skal vi først hente alle data fra Donorfy, dette kan ske på 2 måder
  * Donorfy API (man laver et program der kan hente data ud og skrive til databasen
  * Gennem et job i Azure Data Factory (ADF) - kan se at der allerede ligger et ADF job der hover nogle data ud og skriver til databasen 

Databasen kan f.eks. se således ud (men vil ikke gå igang med at designe denne da der tilsyneladende allerede findes en i Azure):


Constituent
> Contains all constituents
* ConstituentId
* ConstituentNumber
* ConstituentType
* Firstname
* Lastname
* Birthdate
* Type (1,2,3)


ConstituentTag
> Contains information about whitch htags are applied to each constituent
> Det er ikke muligt at få ekstra felter med på tags
* ConstituentId
* TagId

ConstituentType
> Maps constituentTypeID to Name
* Forening
* Hold
* Individual

Relation
> Contains information about how constituents are related to each other, ie. Forening may be related to one or more Hold.
* ParentId
* ChildId
* RelationType

Address
> Contains address information for constituents
> 
