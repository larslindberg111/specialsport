
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

