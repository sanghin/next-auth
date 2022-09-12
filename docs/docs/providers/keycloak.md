---
id: keycloak
title: Keycloak
---

## Documentation

https://www.keycloak.org/docs/latest/server_admin/#_oidc_clients

## Options

The **Keycloak Provider** comes with a set of default options:

- [Keycloak Provider options](https://github.com/nextauthjs/next-auth/blob/main/packages/next-auth/src/providers/keycloak.ts)

## Example
For confidential client:

```js
import KeycloakProvider from "next-auth/providers/keycloak";
...
providers: [
  KeycloakProvider({
    clientAccessType: 'confidential',
    clientId: process.env.KEYCLOAK_ID,
    clientSecret: process.env.KEYCLOAK_SECRET,
    issuer: process.env.KEYCLOAK_ISSUER,
  })
]
...
```

For public client:

```js
import KeycloakProvider from "next-auth/providers/keycloak";
...
providers: [
  {
  ...KeycloakProvider({
    clientSecret: '',
    clientId: process.env.KEYCLOAK_ID,
    issuer: process.env.KEYCLOAK_ISSUER,
  }),
  client: {
    token_endpoint_auth_method: 'none',
    introspection_endpoint_auth_method: 'none',
    revocation_endpoint_auth_method: 'none',
  },
},
]
...
```

:::note
`issuer` should include the realm – e.g. `https://my-keycloak-domain.com/realms/My_Realm`
:::
