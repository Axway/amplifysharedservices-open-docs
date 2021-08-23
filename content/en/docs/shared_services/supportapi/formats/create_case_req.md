---
title: CreateCaseRequest
linkTitle: CreateCaseRequest
weight: 40
date: 2020-03-05
description: Request format for the Create Case method.
---

### Case

| Property Name | Data Type                     | Optional | Description |
|---------------|-------------------------------|----------|-------------|
| sac           | string                        |       no | Support access code. |
| contact       | string                        |       no | The e-mail of the contact. Required for requests that use the [OAuthApplication security scheme](https://sphereapi.admin.axway.com/sphere/api/v1/). |
| subject       | string                        |       no | Brief description of this case. |
| description   | string                        |       no | Detailed description of this case. |
| product       | [Product](#product)           |       no | Affected product. |
| environment   | [Environment](/docs/shared_services/supportapi/formats/environment) |       no | Environment for which this case is created. |
| impact        | [Impact](#impact)             |       no | Impact level. |
| urgency       | [Urgency](/docs/shared_services/supportapi/formats/urgency)         |       no | Urgency level. |
| type          | [CaseType](/docs/shared_services/supportapi/formats/case_type)         |      yes | The type of this case. Default: `Support Case`. |
| targetDate    | string                        |      yes | Applicable when the case is a business service request. Sending `targetDate` with other case types results in an error. See more details [here](/docs/shared_services/supportapi/formats/target_date). |
| ccEmails      | [ string ]                    |      yes | E-mail addresses to be copied in communications regarding this case. |

### Impact

Impact levels supported in Create Case requests to the API, as an open-ended enumeration.

* **Data Type**: string
* **Enumeration Elements**:
    * 2 - High
    * 3 - Mediums
    * 4 - Low

For details on the different enumeration elements, please refer to [Impact](/docs/shared_services/supportapi/formats/impact).

### Product

{{% alert title="Note" %}}
Product, product version and product operating system identifiers can be obtained with a call to the [Get Products](/docs/shared_services/supportapi/methods/get_products) method.
{{% /alert %}}

| Property Name | Data Type                         | Optional | Description |
|---------------|-----------------------------------|----------|-------------|
| id            | string                            |       no | Identifier of this product for the purposes of Axway Support case management. |
| os            | [ProductOs](#productos)           |       no | Operating system on which the product is run. |
| version       | [ProductVersion](#productversion) |       no | Version of the affected product. |
| patch         | string                            |      yes | Service pack or patch in effect. Free form text. |

### ProductOs

| Property Name | Data Type | Optional | Description |
|---------------|-----------|----------|-------------|
| id            | string    |       no | Identifier of this operating system for the purposes of Axway Support case management. |

### ProductVersion

| Property Name | Data Type | Optional | Description |
|---------------|-----------|----------|-------------|
| id            | string    |       no | Identifier of this product version for the purposes of Axway Support case management. |
