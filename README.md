### Microsoft 365 as an integrated suite ##

This diagram conceptualises Microsoft 365 as an integrated suite, highlighting its core services and their interconnectedness to facilitate collaboration and communication:

<img width="745" height="594" alt="image" src="https://github.com/user-attachments/assets/54fc62b0-6647-4e2a-b066-f07526d93652" />

### SharePoint Online: Core Structure & Content ##

This schematic illustrates the fundamental structural hierarchy of SharePoint Online, detailing its key components such as site collections, sites, hub sites, and the primary content types like lists and libraries.

<img width="1212" height="499" alt="image" src="https://github.com/user-attachments/assets/766fad05-0d65-40f1-aefb-456c0186e8f2" />

### SharePoint Permissions: User Management & Access Control ##

This diagram conveys the basic principles of user management via Azure Active Directory and how permissions operate within SharePoint, including roles and the concept of inheritance.

<img width="931" height="535" alt="image" src="https://github.com/user-attachments/assets/a387d256-c70a-42da-b8b6-317eb5c40959" />



---

UML Manifest #1:

@startuml
!theme plain
skinparam component {
  BorderColor #333333
  BackgroundColor #CCEEFF
  FontColor #333333
  Shadowing false
}
skinparam rectangle {
  BorderColor #333333
  BackgroundColor #F8F8F8
  FontColor #333333
  Shadowing false
}
skinparam ArrowColor #333333
skinparam Linetype ortho

title Microsoft 365: Integrated Collaboration Suite

rectangle "Microsoft 365 Ecosystem" {
  component "Exchange Online\n(Email & Calendar)" as Exchange
  component "Microsoft Teams\n(Chat, Meetings, Calls)" as Teams
  component "OneDrive\n(Personal File Storage)" as OneDrive
  component "SharePoint Online\n(Collaboration & Document Management)" as SharePoint
}

Exchange <--> Teams : "Facilitates Communication"
Teams <--> OneDrive : "Shares Files from"
Teams <--> SharePoint : "Uses for Team Sites & Files"
OneDrive <--> SharePoint : "Integrates Personal & Team Files"
Exchange <--> SharePoint : "Notifications & Data Sharing"

note top of Exchange: Centralised Email
note top of Teams: Hub for Teamwork
note top of OneDrive: Cloud Storage for Individuals
note top of SharePoint: Platform for Collaboration & Content

@enduml


UML Manifest #2:

@startuml
!theme plain
skinparam rectangle {
  BorderColor #333333
  BackgroundColor #CCEEFF
  FontColor #333333
  Shadowing false
}
skinparam component {
  BorderColor #333333
  BackgroundColor #F8F8F8
  FontColor #333333
  Shadowing false
}
skinparam database {
  BorderColor #333333
  BackgroundColor #FFCCEE
  FontColor #333333
  Shadowing false
}
skinparam ArrowColor #333333
skinparam Linetype ortho

title SharePoint Online: Core Structure & Content

rectangle "SharePoint Online Environment" as SPO {
  rectangle "Site Collection" as SiteCollection1 {
    component "Hub Site (Optional)" as HubSite
    rectangle "Site (e.g., Team Site)" as TeamSite
    rectangle "Site (e.g., Communication Site)" as CommSite
  }
  rectangle "Site Collection" as SiteCollection2 {
    rectangle "Site" as OtherSite
  }
}

HubSite -down-> TeamSite : "Associates"
HubSite -down-> CommSite : "Associates"
SiteCollection1 --> SiteCollection2 : "Independent but can link"

rectangle "Site Content" {
  database "Lists\n(Structured Data)" as Lists
  database "Libraries\n(Documents & Files)" as Libraries
}

TeamSite ..> Lists : "Contains"
TeamSite ..> Libraries : "Contains"
CommSite ..> Lists
CommSite ..> Libraries

note top of Lists: For items, tasks, contacts
note top of Libraries: For documents, images, videos
note bottom of TeamSite: Collaboration focus
note bottom of CommSite: Publishing focus

@enduml

UML Manifest #3:

@startuml
!theme plain
skinparam actor {
  BorderColor #333333
  BackgroundColor #DDDDDD
  FontColor #333333
  Shadowing false
}
skinparam cloud {
  BorderColor #333333
  BackgroundColor #CCEEFF
  FontColor #333333
  Shadowing false
}
skinparam rectangle {
  BorderColor #333333
  BackgroundColor #F8F8F8
  FontColor #333333
  Shadowing false
}
skinparam database {
  BorderColor #333333
  BackgroundColor #FFCCEE
  FontColor #333333
  Shadowing false
}
skinparam ArrowColor #333333
skinparam Linetype ortho

title SharePoint Permissions: User Management & Access Control

actor "User" as User

cloud "Azure Active Directory\n(Identity Management)" as AzureAD

rectangle "SharePoint Site / Content" as SharePointSite {
  rectangle "Permission Group: Owners" as Owners
  rectangle "Permission Group: Members" as Members
  rectangle "Permission Group: Visitors" as Visitors
  database "Lists & Libraries" as Content
}

User --> AzureAD : "Authenticated Identity"

AzureAD --> Owners : "Manages Users & Groups"
AzureAD --> Members
AzureAD --> Visitors

Owners --> SharePointSite : "Full Control"
Members --> SharePointSite : "Edit/Contribute"
Visitors --> SharePointSite : "Read Only"

SharePointSite --> Content : "Permissions apply to"

note bottom of SharePointSite: Permissions can be inherited\nor set uniquely for sub-elements.
note left of AzureAD: Central source of user identities.

@enduml



