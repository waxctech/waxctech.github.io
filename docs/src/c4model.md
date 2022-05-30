# Plantuml Installation

- `$cargo install mdbook-graphviz`
- `$cargo install mdbook-plantuml` : require to change source code for "graphviz"
- `$brew install graphviz` : current 3.0.0
- `$brew install plantuml` : current 1.2022.5
- for C4, remove any string after @startuml, otherwise mdbook will not render

# install mdbook preprocessor in book.toml
```toml
[preprocessor.plantuml]
plantuml-cmd="/usr/local/bin/plantuml"
```

# Container View 
- sample with links, showing connection protocol between services
```plantuml
@startuml
!include <C4/C4_Container>

Person(admin, "Administrator", $sprite="person2", $link="https://github.com/plantuml-stdlib/C4-PlantUML/blob/master/LayoutOptions.md#hide_person_sprite-or-show_person_spritesprite")
System_Boundary(c1, "Sample System", $link="https://github.com/plantuml-stdlib/C4-PlantUML") {
    Container(web_app, "Web Application", "C#, ASP.NET Core 2.1 MVC", $descr="Allows users to compare multiple Twitter timelines", $link="https://github.com/plantuml-stdlib/C4-PlantUML/blob/master/LayoutOptions.md")
}
System(twitter, "Twitter", $link="https://github.com/plantuml-stdlib/C4-PlantUML")

Rel(admin, web_app, "Uses API", "HTTPS", $link="https://plantuml.com/link")
Rel(web_app, twitter, "Gets tweets from API", "HTTPS", $link="https://plantuml.com/link")
@enduml
```

# System Context View
```plantuml
@startuml
scale 400 width
!include <C4/C4_Container>
' uncomment the following line and comment the first to use locally
' !include C4_Context.puml

LAYOUT_WITH_LEGEND()

title System Context diagram for Internet Banking System

Person(customer, "Personal Banking Customer", "A customer of the bank, with personal bank accounts.")
System(banking_system, "Internet Banking System", "Allows customers to view information about their bank accounts, and make payments.")

System_Ext(mail_system, "E-mail system", "The internal Microsoft Exchange e-mail system.")
System_Ext(mainframe, "Mainframe Banking System", "Stores all of the core banking information about customers, accounts, transactions, etc.")

Rel(customer, banking_system, "Uses")
Rel_Back(customer, mail_system, "Sends e-mails to")
Rel_Neighbor(banking_system, mail_system, "Sends e-mails", "SMTP")
Rel(banking_system, mainframe, "Uses")
@enduml
```

# Container View - shows application, service, microservice, etc
```plantuml
@startuml
!include <C4/C4_Container>
!define DEVICONS https://raw.githubusercontent.com/tupadr3/plantuml-icon-font-sprites/master/devicons
!define FONTAWESOME https://raw.githubusercontent.com/tupadr3/plantuml-icon-font-sprites/master/font-awesome-5
' uncomment the following line and comment the first to use locally
' !include C4_Container.puml
!include DEVICONS/angular.puml
!include DEVICONS/dotnet.puml
!include DEVICONS/java.puml
!include DEVICONS/msql_server.puml
!include FONTAWESOME/server.puml
!include FONTAWESOME/envelope.puml

' LAYOUT_TOP_DOWN()
' LAYOUT_AS_SKETCH()
LAYOUT_WITH_LEGEND()

title Container diagram for Internet Banking System

Person(customer, Customer, "A customer of the bank, with personal bank accounts")

System_Boundary(c1, "Internet Banking") {
    Container(web_app, "Web Application", "Java, Spring MVC", "Delivers the static content and the Internet banking SPA", "java")
    Container(spa, "Single-Page App", "JavaScript, Angular", "Provides all the Internet banking functionality to cutomers via their web browser", "angular")
    Container(mobile_app, "Mobile App", "C#, Xamarin", "Provides a limited subset of the Internet banking functionality to customers via their mobile device", "dotnet")
    ContainerDb(database, "Database", "SQL Database", "Stores user registraion information, hased auth credentials, access logs, etc.", "msql_server")
    Container(backend_api, "API Application", "Java, Docker Container", "Provides Internet banking functionality via API", "server")
}

System_Ext(email_system, "E-Mail System", "The internal Microsoft Exchange system", "envelope")
System_Ext(banking_system, "Mainframe Banking System", "Stores all of the core banking information about customers, accounts, transactions, etc.")

Rel(customer, web_app, "Uses", "HTTPS")
Rel(customer, spa, "Uses", "HTTPS")
Rel(customer, mobile_app, "Uses")

Rel_Neighbor(web_app, spa, "Delivers")
Rel(spa, backend_api, "Uses", "async, JSON/HTTPS")
Rel(mobile_app, backend_api, "Uses", "async, JSON/HTTPS")
Rel_Back_Neighbor(database, backend_api, "Reads from and writes to", "sync, JDBC")

Rel_Back(customer, email_system, "Sends e-mails to")
Rel_Back(email_system, backend_api, "Sends e-mails using", "sync, SMTP")
Rel_Neighbor(backend_api, banking_system, "Uses", "sync/async, XML/HTTPS")
@enduml
```
# Component View
```plantuml
@startuml
!include https://raw.githubusercontent.com/plantuml-stdlib/C4-PlantUML/master/C4_Component.puml
' uncomment the following line and comment the first to use locally
' !include C4_Context.puml

LAYOUT_WITH_LEGEND()

title Component diagram for Internet Banking System - API Application

Container(spa, "Single Page Application", "javascript and angular", "Provides all the internet banking functionality to customers via their web browser.")
Container(ma, "Mobile App", "Xamarin", "Provides a limited subset ot the internet banking functionality to customers via their mobile mobile device.")
ContainerDb(db, "Database", "Relational Database Schema", "Stores user registration information, hashed authentication credentials, access logs, etc.")
System_Ext(mbs, "Mainframe Banking System", "Stores all of the core banking information about customers, accounts, transactions, etc.")

Container_Boundary(api, "API Application") {
Component(sign, "Sign In Controller", "MVC Rest Controlle", "Allows users to sign in to the internet banking system")
Component(accounts, "Accounts Summary Controller", "MVC Rest Controller", "Provides customers with a summary of their bank accounts")
Component(security, "Security Component", "Spring Bean", "Provides functionality related to singing in, changing passwords, etc.")
Component(mbsfacade, "Mainframe Banking System Facade", "Spring Bean", "A facade onto the mainframe banking system.")

    Rel(sign, security, "Uses")
    Rel(accounts, mbsfacade, "Uses")
    Rel(security, db, "Read & write to", "JDBC")
    Rel(mbsfacade, mbs, "Uses", "XML/HTTPS")
}

Rel(spa, sign, "Uses", "JSON/HTTPS")
Rel(spa, accounts, "Uses", "JSON/HTTPS")

Rel(ma, sign, "Uses", "JSON/HTTPS")
Rel(ma, accounts, "Uses", "JSON/HTTPS")
@enduml
```

# System Landscape View
```plantuml
@startuml
!include <C4/C4_Container>
' uncomment the following line and comment the first to use locally
' !include C4_Context.puml

'LAYOUT_TOP_DOWN()
'LAYOUT_AS_SKETCH()
LAYOUT_WITH_LEGEND()

title System Landscape diagram for Big Bank plc

Person(customer, "Personal Banking Customer", "A customer of the bank, with personal bank accounts.")

Enterprise_Boundary(c0, "Big Bank plc") {
    System(banking_system, "Internet Banking System", "Allows customers to view information about their bank accounts, and make payments.")

    System_Ext(atm, "ATM", "Allows customers to withdraw cash.")
    System_Ext(mail_system, "E-mail system", "The internal Microsoft Exchange e-mail system.")

    System_Ext(mainframe, "Mainframe Banking System", "Stores all of the core banking information about customers, accounts, transactions, etc.")

    Person_Ext(customer_service, "Customer Service Staff", "Customer service staff within the bank.")
    Person_Ext(back_office, "Back Office Staff", "Administration and support staff within the bank.")
}

Rel_Neighbor(customer, banking_system, "Uses")
Rel_R(customer, atm, "Withdraws cash using")
Rel_Back(customer, mail_system, "Sends e-mails to")

Rel_R(customer, customer_service, "Asks questions to", "Telephone")

Rel_D(banking_system, mail_system, "Sends e-mail using")
Rel_R(atm, mainframe, "Uses")
Rel_R(banking_system, mainframe, "Uses")
Rel_D(customer_service, mainframe, "Uses")
Rel_U(back_office, mainframe, "Uses")

Lay_D(atm, banking_system)

Lay_D(atm, customer)
Lay_U(mail_system, customer)
@enduml
```

# Dynamic View
```plantuml
@startuml
!include https://raw.githubusercontent.com/plantuml-stdlib/C4-PlantUML/master/C4_Dynamic.puml
LAYOUT_WITH_LEGEND()

ContainerDb(c4, "Database", "Relational Database Schema", "Stores user registration information, hashed authentication credentials, access logs, etc.")
Container(c1, "Single-Page Application", "JavaScript and Angular", "Provides all of the Internet banking functionality to customers via their web browser.")
Container_Boundary(b, "API Application") {
  Component(c3, "Security Component", "Spring Bean", "Provides functionality Related to signing in, changing passwords, etc.")
  Component(c2, "Sign In Controller", "Spring MVC Rest Controller", "Allows users to sign in to the Internet Banking System.")
}
Rel_R(c1, c2, "Submits credentials to", "JSON/HTTPS")
Rel(c2, c3, "Calls isAuthenticated() on")
Rel_R(c3, c4, "select * from users where username = ?", "JDBC")
@enduml
```

# Deployment with Detail View
```plantuml
@startuml
!include https://raw.githubusercontent.com/plantuml-stdlib/C4-PlantUML/master/C4_Deployment.puml
' uncomment the following line and comment the first to use locally
' !include C4_Deployment.puml

AddElementTag("fallback", $bgColor="#c0c0c0")
AddRelTag("fallback", $textColor="#c0c0c0", $lineColor="#438DD5")

WithoutPropertyHeader()

' calculated legend is used (activated in last line)
' LAYOUT_WITH_LEGEND()

title Deployment Diagram for Internet Banking System - Live

Deployment_Node(plc, "Live", "Big Bank plc", "Big Bank plc data center"){
    AddProperty("Location", "London and Reading")
    Deployment_Node_L(dn, "bigbank-api***\tx8", "Ubuntu 16.04 LTS", "A web server residing in the web server farm, accessed via F5 BIG-IP LTMs."){
        AddProperty("Java Version", "8")
        AddProperty("Xmx", "512M")
        AddProperty("Xms", "1024M")
        Deployment_Node_L(apache, "Apache Tomcat", "Apache Tomcat 8.x", "An open source Java EE web server."){
            Container(api, "API Application", "Java and Spring MVC", "Provides Internet Banking functionality via a JSON/HTTPS API.")
        }
    }
    AddProperty("Location", "London")
    Deployment_Node_L(bigbankdb01, "bigbank-db01", "Ubuntu 16.04 LTS", "The primary database server."){
        Deployment_Node_L(oracle, "Oracle - Primary", "Oracle 12c", "The primary, live database server."){
            ContainerDb(db, "Database", "Relational Database Schema", "Stores user registration information, hashed authentication credentials, access logs, etc.")
        }
    }
    AddProperty("Location", "Reading")
    Deployment_Node_R(bigbankdb02, "bigbank-db02", "Ubuntu 16.04 LTS", "The secondary database server.", $tags="fallback") {
        Deployment_Node_R(oracle2, "Oracle - Secondary", "Oracle 12c", "A secondary, standby database server, used for failover purposes only.", $tags="fallback") {
            ContainerDb(db2, "Database", "Relational Database Schema", "Stores user registration information, hashed authentication credentials, access logs, etc.", $tags="fallback")
        }
    }
    AddProperty("Location", "London and Reading")
    Deployment_Node_R(bb2, "bigbank-web***\tx4", "Ubuntu 16.04 LTS", "A web server residing in the web server farm, accessed via F5 BIG-IP LTMs."){
        AddProperty("Java Version", "8")
        AddProperty("Xmx", "512M")
        AddProperty("Xms", "1024M")
        Deployment_Node_R(apache2, "Apache Tomcat", "Apache Tomcat 8.x", "An open source Java EE web server."){
            Container(web, "Web Application", "Java and Spring MVC", "Delivers the static content and the Internet Banking single page application.")
        }
    }
}

Deployment_Node(mob, "Customer's mobile device", "Apple IOS or Android"){
    Container(mobile, "Mobile App", "Xamarin", "Provides a limited subset of the Internet Banking functionality to customers via their mobile device.")
}

Deployment_Node(comp, "Customer's computer", "Mircosoft Windows of Apple macOS"){
    Deployment_Node(browser, "Web Browser", "Google Chrome, Mozilla Firefox, Apple Safari or Microsoft Edge"){
        Container(spa, "Single Page Application", "JavaScript and Angular", "Provides all of the Internet Banking functionality to customers via their web browser.")
    }
}

Rel(mobile, api, "Makes API calls to", "json/HTTPS")
Rel(spa, api, "Makes API calls to", "json/HTTPS")
Rel_U(web, spa, "Delivers to the customer's web browser")
Rel(api, db, "Reads from and writes to", "JDBC")
Rel(api, db2, "Reads from and writes to", "JDBC", $tags="fallback")
Rel_R(db, db2, "Replicates data to")

SHOW_LEGEND()
@enduml
```

# Container View on Messaging Bus
```plantuml
@startuml
!include <C4/C4_Container>
' uncomment the following line and comment the first to use locally
' !include C4_Container.puml

AddElementTag("microService", $shape=EightSidedShape(), $bgColor="CornflowerBlue", $fontColor="white", $legendText="micro service (eight sided)")
AddElementTag("storage", $shape=RoundedBoxShape(), $bgColor="lightSkyBlue", $fontColor="white")

SHOW_PERSON_OUTLINE()

Person(customer, Customer, "A customer")

System_Boundary(c1, "Customer Information") {
    Container(app, "Customer Application", "Javascript, Angular", "Allows customers to manage their profile")
    Container(customer_service, "Customer Service", "Java, Spring Boot", "The point of access for customer information", $tags = "microService")
    Container(message_bus, "Message Bus", "RabbitMQ", "Transport for business events")
    Container(reporting_service, "Reporting Service", "Ruby", "Creates normalised data for reporting purposes", $tags = "microService")
    Container(audit_service, "Audit Service", "C#/.NET", "Provides organisation-wide auditing facilities", $tags = "microService")
    ContainerDb(customer_db, "Customer Database", "Oracle 12c", "Stores customer information", $tags = "storage")
    ContainerDb(reporting_db, "Reporting Database", "MySQL", "Stores a normalized version of all business data for ad hoc reporting purposes", $tags = "storage")
    Container(audit_store, "Audit Store", "Event Store", "Stores information about events that have happened", $tags = "storage")
}

Rel_D(customer, app, "Uses", "HTTPS")

Rel_D(app, customer_service, "Updates customer information using", "async, JSON/HTTPS")

Rel_U(customer_service, app, "Sends events to", "WebSocket")
Rel_U(customer_service, message_bus, "Sends customer update events to")
Rel(customer_service, customer_db, "Stores data in", "JDBC")

Rel(message_bus, reporting_service, "Sends customer update events to")
Rel(message_bus, audit_service, "Sends customer update events to")

Rel(reporting_service, reporting_db, "Stores data in")
Rel(audit_service, audit_store, "Stores events in")

Lay_R(reporting_service, audit_service)

SHOW_LEGEND()
@enduml
```

# Reference:
- [C4 core diagram](https://github.com/plantuml-stdlib/C4-PlantUML/blob/master/samples/C4CoreDiagrams.md)
- [C4 modelling](https://c4model.com/#examples)
- [graphviz](https://graphviz.org/)
- [cloud arh](https://diagrams.mingrammer.com/)
- [C4-PlantUM](https://github.com/plantuml-stdlib/C4-PlantUML)
- [plantuml](https://plantuml.com/en/)
- [aws plantuml](https://github.com/awslabs/aws-icons-for-plantuml)
- [asciidoc](https://docs.asciidoctor.org/diagram-extension/latest/#meme)
- [VISUALIZATION GRAMMARS](https://vega.github.io/vega/)
- [vega-lite]([https://vega.github.io/vega-lite/)
- [kroki](https://kroki.io/#cheat-sheet)  - using it to support vega ?
- [mermaid demo](https://github.com/mermaid-js/mermaid)
- [cargo dependency graph](https://github.com/kbknapp/cargo-graph)
- [Tutorial on Plantuml](https://crashedmind.github.io/PlantUMLHitchhikersGuide/index.html)