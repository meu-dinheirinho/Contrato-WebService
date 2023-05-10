
# Meu dinheirinho Contrato

Software de organização financeira criado para auxiliar o usuário a ter um controle sobre todas as suas finanças.


## Documentação da API - Contrato WebService (v0.1)

### Base URL

PUBLIC_BASE = api/pub

PRIVATE_BASE = api/priv

 
### Header and Error Default

  | Key         | Value      |
  | :---------- | :--------- |
  | *HEADERS* | *OBJECT* |


|     | Attribute       | Type     | Restriction | IsRequired | Description                     |
| --- | :-------------- | :------- | :---------- | :--------- | :------------------------------ |
|     | `x-application` | `String` | `-`         | `false`    | name application                |
|     | `x-version`     | `String` | `-`         | `false`    | Version application  ex.: 0.0.1 |
|     | `x-app-tenant`  | `String` | `-`         | `true`     | URL domain                      |
|     | `x-token`       | `String` | `-`         | `false`    | token for access                |

## Parameters

  | Key       | Value |
  | :-------- | :---- |
  | `version` | `v1`  |

## Status

  | Status | Type                          |
  | :----- | :---------------------------- |
  | 200    | Success                       |
  | 403    | Forbiden                      |
  | 404    | NotFound                      |
  | 407    | Proxy authentication required |
  | 500    | ErrorServer                   |
  | 502    | ErrorNginx                    |

# Error Response

 | Origin    | Type      | Codes                                          |
 | :-------- | :-------- | :--------------------------------------------- |
 | Body      | Object    | 400, 403, 407 500                              |
 | Attribute | Type      | Description                                    |
 | `code`    | `Integer` | code number to error                           |
 | `message` | `String`  | message error                                  |
 | `_mid`    | `String`  | code that identifies the request to the client |

# Default Response

| Origin | Type   | Status |
| :----- | :----- | :----- |
| Body   | Object | 200    |

| Attribute | Type     | Description                                    |
| :-------- | :------- | :--------------------------------------------- |
| `_mid`    | `String` | code that identifies the request to the client |


## Endpoints

### Authentication

```http
  POST {PUBLIC_BASE}/api/login
```
create an authentication

#### - Request:

| Origin | Type   |
| :----- | :----- |
| Body   | Object |


| Attribute    | Type     | Restriction      | IsRequired | Description                                    |
| :----------- | :------- | :--------------- | :--------- | :--------------------------------------------- |
| `email` | `String` | `255 characters` | `true`     | identifier for access                          |
| `password`     | `String` | `255 characters` | `true`     | secret for access                              |
| `_mid`       | `String` | -                | `false`    | code that identifies the request to the client |
| `_v`         | `String` | -                | `false`    | message version                                |


#### - Response:

| Origin | Type   | Status |
| :----- | :----- | :----- |
| Body   | Object | 200    |

| Attribute  | Type     | Description                                    |
| :--------- | :------- | :--------------------------------------------- |
| `jwtToken` | `String` | access token                                   |
| `_mid`     | `String` | code that identifies the request to the client |

---
---


### Register

```http
  POST {PUBLIC_BASE}/api/register
```
create an new user

#### - Request:

| Origin | Type   |
| :----- | :----- |
| Body   | Object |


| Attribute    | Type     | Restriction      | IsRequired | Description                                    |
| :----------- | :------- | :--------------- | :--------- | :--------------------------------------------- |
| `name` | `String` | `50 characters` | `true`     | user name           |
| `password`     | `String` | `255 characters` | `true`     | secret for access   
| `email`     | `String` | `255 characters` | `true`     | identifier for access                  
| `phone`     | `String` | `11 characters` | `true`     | user contact 
| `_mid`       | `String` | -                | `false`    | code that identifies the request to the client |
| `_v`         | `String` | -                | `false`    | message version                                |


#### - Response:

| Origin | Type   | Status |
| :----- | :----- | :----- |
| Body   | Object | 200    |

| Attribute  | Type     | Description                                    |
| :--------- | :------- | :--------------------------------------------- |
| `_mid`     | `String` | code that identifies the request to the client |

