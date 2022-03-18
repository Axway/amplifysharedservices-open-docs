---
title: ListCasesRequest
linkTitle: ListCasesRequest
weight: 30
date: 2020-03-05
description: Request format for the List Cases method.
---

### Filter

| Property Name | Data Type             | Optional | Description |
|---------------|-----------------------|----------|-------------|
| created       | [TimeSpan](#timespan) |      yes | Get cases created within the specified time span. |
| updated       | [TimeSpan](#timespan) |      yes | Get cases updated within the specified time span. |
| sac           | string                |      yes | Get cases for the specified support access code. |
| types         | [IncludeCaseTypes](#includecasetypes) or [ExcludeCaseTypes](#excludecasetypes) | yes | Get cases of the specified types. |
| statuses      | [IncludeCaseStatuses](#includecasestatuses) or [ExcludeCaseStatuses](#excludecasestatuses) | yes | Get cases according to the specified case statuses. |

### TimeSpan

| Property Name | Data Type | Optional | Description |
|---------------|-----------|----------|-------------|
| before        | string    |       no | Starting date/time of the time span. [Format](/docs/shared_services/supportapi/formats/miscellaneous/#common-date-and-time-format-for-requests). |
| after         | string    |       no | Ending date/time of the time span. [Format](/docs/shared_services/supportapi/formats/miscellaneous/#common-date-and-time-format-for-requests). |

### IncludeCaseTypes

| Property Name | Data Type                 | Optional | Description |
|---------------|---------------------------|----------|-------------|
| include       | [CaseType](#casetype) (array) |       no | Filter-in the specified case types. Filter out all others. The list of types must not be empty and must contain unique elements. |

### ExcludeCaseTypes

| Property Name | Data Type                 | Optional | Description |
|---------------|---------------------------|----------|-------------|
| exclude       | [CaseType](#casetype) (array) |       no | Filter-out the specified case types.  The list of types must not be empty and must contain unique elements. |

### CaseType

An open-ended list of case types that are supported in a List Cases filter.

* **Data Type**: string
* **Enumeration Elements**:
    * Enhancement Request
    * Business Service Request

### IncludeCaseStatuses

| Property Name | Data Type                     | Optional | Description |
|---------------|-------------------------------|----------|-------------|
| include       | [CaseStatus](#casestatus) (array) |       no | Filter-in cases in the specified statuses. Filter out all others. The list of statuses must not be empty and must contain unique elements. |

### ExcludeCaseStatuses

| Property Name | Data Type                     | Optional | Description |
|---------------|-------------------------------|----------|-------------|
| exclude       | [CaseStatus](#casestatus) (array) |       no | Filter-out cases in the specified statuses.  The list of statuses must not be empty and must contain unique elements. |

### CaseStatus

An open-ended list of case statuses that are supported in a List Cases filter.

* **Data Type**: string
* **Enumeration Elements**:
    * In Support
    * Customer Owns Next Steps
    * In Escalation
    * Ready for Deployment
    * In R&D
    * R&D Delivery
    * Pending Closure
    * Closed
