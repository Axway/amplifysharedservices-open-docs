---
title: Authentication
linkTitle: Authentication
weight: 20
date: 2021-08-03
hide_readingtime: true
description: Learn how to authenticate your requests to the API.
---

The API requires an access token to be included in each request.

Access tokens can be obtained using a service account added in the Amplify Platform.
For details on how to add a service account, please refer to [Managing service accounts](https://docs.axway.com/bundle/Amplify_Platform_Management_allOS_en/page/managing_organizations.html#ManagingOrganizations-service_accountsManagingserviceaccounts).

#### Obtain an access token

The example below assumes a service account created with its authentication method set to `Client Secret`.
The example client ID will be `example-client-id` and the client secret will be `example-client-secret`. Please replace with the corresponding values for your service account.

Request:

```bash
curl \
-d'grant_type=client_credentials' \
-d'client_id=example-client-id' \
-d'client_secret=example-client-secret' \
https://login.axway.com/auth/realms/Broker/protocol/openid-connect/token
```

Response:

```
{
  "access_token": "example-access-token",
  "expires_in": 1800,
  "refresh_expires_in": 0,
  "token_type": "bearer",
  "not-before-policy": 1571719187,
  ...
}
```

{{% alert title="Note" %}}
The access token will typically be a long JSON Web Token string.
{{% /alert %}}

#### Issue a request to the API

The example below uses an access token of value `example-access-token`. Please replace with an actual access token obtained as shown in the previous section.

Request:

```bash
curl \
-H'Authorization: Bearer example-access-token' \
'https://sphereapi.admin.axway.com/sphere/api/v1/case?limit=1&sort=-modifiedDate'
```

Response:

```
{
  "limit": 1,
  "offset": 0,
  "cases": [
    {
      "caseNumber": "NNNNNNNN",
      "closedDate": "2021-07-22T12:32:55.000+0000",
      "createdDate": "2021-07-22T12:32:36.000+0000",
      "modifiedDate": "2021-07-22T12:32:57.000+0000",
      "severity": "4 - Minor",
      "status": "Closed",
      "subject": "Axway Support Portal API - Example",
      "type": "Support Case"
    }
  ]
}
```

In this example, we retrieved the most recently updated support case for our organization.
We used the [List Cases](/docs/shared_services/supportapi/methods/list_cases/) method.
