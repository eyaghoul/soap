# B- Lecture du Contrat (Analysis)

## 1-définir la structure du message SOAP\*

définit les types XML, les éléments de requête et réponse pour le service SOAP.

## 2- dans bank.xsd on a :

GetAccountRequest
accountId : string
GetAccountResponse
owner : string
balance : decimal
currency : string

DepositRequest
accountId : string
amount : decimal

DepositResponse
newBalance : decimal

# C- Resultats de tests Postman

## GetAccount

récupération correcte des informations du compte.
![GetAccount](src/main/images/Capture d'écran 2026-02-11 012212.png)

## Deposit

![Deposit](src/main/images/deposit.png)

### possible fault cases

_unknown account :_
![Unknown Account](src/main/images/unknown_account.png)
_unvalid amount :_
![Invalid Amount](src/main/images/unvalid_amount.png)

## Withdraw

![Withdraw](src/main/images/withdraw.png)

### possible fault cases

_unknown account :_
![Withdraw Unknown Account](images/withdraw_unknown_account.png)
_unvalid amount :_
![Withdraw Invalid Amount](src/main/images/withdraw_unvalid_amount.png)
_insufficient balance :_
![Withdraw Insufficient Balance](src/main/images/withdraw_insufficient_balance.png)

# D- Fonctionnalité ajoutée

_Withdraw_ :nouvelle opération permettant de retirer un montant d’un compte existant.
Le service vérifie que :
le compte existe,
le montant est strictement positif,
le solde est suffisant.

# fichiers modifiés :

_bank.xsd :_ ajout de WithdrawRequest et WithdrawResponse
_BankService.java :_ methode withdraw()
*BankEndpoint.java : *implémentation de la méthode withdraw()
_classes generees jaxb :_ WithdrawRequest et WithdrawResponse
