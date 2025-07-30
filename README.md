This diagram conceptualises Microsoft 365 as an integrated suite, highlighting its core services and their interconnectedness to facilitate collaboration and communication:

<img width="745" height="594" alt="image" src="https://github.com/user-attachments/assets/54fc62b0-6647-4e2a-b066-f07526d93652" />

---

UML Manifest:

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
