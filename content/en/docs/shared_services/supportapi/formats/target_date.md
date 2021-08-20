---
title: TargetDate
linkTitle: TargetDate
weight: 5
date: 2020-03-05
description: Provided milestone target date for cases of type business service request
---

Milestone Target Date is the time by which an update should be sent to the customer to meet the initial or update commitment. Applicable when the case is a business service request. Sending 'targetDate' with other case types results in an error. See [CaseType](/docs/shared_services/supportapi/formats/case_type).

* **Data Type**: string
* **Format**: `date` as per profile ISO8601 at [RFC 3339](https://datatracker.ietf.org/doc/html/rfc3339#ref-ISO8601); `yyyy-MM-dd`
* **Example**: `2024-08-20`