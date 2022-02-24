# Assignment 1

Assignment 1: Create Use-case and Sequence diagram using PLantUML tool. 


### 18103034 Ishika Agarwal

## Use-Case Diagram Using PlantUML

### Diagram
![alt Image](https://github.com/ishika-1/SoftwareTesting/blob/main/Assignment%201/UseCaseDiagram.png)

### Code
```
@startuml COGNICHAT

actor "User" as user
actor "Chat Bot" as bot

left to right direction
skinparam packageStyle rectangle


rectangle COGNICHAT{

(Login) as login
(Forgot Password) as forgot
(Verify Password) as verify
(Set Up Profile) as profile
(Account Balance) as balance
(Buy Product) as buy
(Total Expenditure) as tot
(Add Expenditure) as add
(Compare Price & Balance) as compare
(Display Total Expenditure) as disp
(Show Expenses) as show
(Logout) as logout

}

login ..> forgot : extend
login ..> verify : include
buy ..> compare : include
tot ..> disp : extend

user -- login
user -- profile
user -- balance
user -- buy
user -- tot
user -- add
user -- show
user -- logout

verify -- bot
compare -- bot
disp -- bot
add -- bot
logout -- bot


@enduml
```



## Sequence Diagram Using PlantUML

### Diagram
![alt Image](https://github.com/ishika-1/SoftwareTesting/blob/main/Assignment%201/SequenceDiagram.png)

### Code
```
@startuml SequenceDiagram
skinparam style strictuml
skinparam sequenceMessageAlign center
title COGNICHAT - Financial Chatbot
actor User as A
participant "LOGIN PORTAL" as B
participant "CHATBOT INTERFACE" as C
participant "ENGINE" as D
participant "DATABASE SERVER" as E

activate B#LightGray
activate E#LightGray
B -> E : Login Credentials
E --> B : Authentication Success Status
deactivate E

A -> B : Login()
A -> B : Setup Profile()
A -> B : Reset Password ()
B --> A : Valid
B --> A : Invalid

group#Gold #LightGreen SignUp [Success]
    B -> A: Authentication Accepted
else #LightPink Failure
    B -> A: Authentication Rejected
end
deactivate B

|||

A -> C : User Query
activate C#LightGray
activate D#LightGray
C -> D : Can/Cannot buy query
C -> D : Add Expenditure()
C -> D : Show Expenses()
C -> D : Display Account Balance()
C -> D : Display Total Expenditure()

activate E#LightGray
D -> E : Search Database
D -> E : Update Database
E --> D : Retrieve Data
deactivate E

D --> C : Return data for Response
deactivate D

C --> A : Chatbot Reply
deactivate C

@enduml
```