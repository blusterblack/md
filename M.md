# Money lover app

## User stories

- create account

- login

- add transactions contain money, category, date ( auto), detail, wallet

- remove transaction

- edit transaction

- view all transactions by date

- view report of custom time period

- view all transaction by category

## Database

| User       |            |
| ---------- | ---------- |
| _id        | objectId   |
| email      | string     |
| password   | string     |
| salt       | string     |
| walletList | [objectId] |

| Wallet  |          |
| ------- | -------- |
| _id     | objectId |
| name    | string   |
| balance | decimal  |

| Transaction |           |
| ----------- | --------- |
| _id         | objectId  |
| category    | string    |
| amount      | decimal   |
| detail      | string    |
| date        | timestamp |
| ofWallet    | objectId  |

## APIs

| Method   | Route                 |
| -------- | --------------------- |
| POST     | user/login            |
| POST     | user/register         |
| POST/GET | wallet/:userId        |
| POST/GET | transaction/:walletId |
<!--stackedit_data:
eyJoaXN0b3J5IjpbMzUzMTE5NjldfQ==
-->