---
title: "timeZoneInformation resource type"
description: "Represents a time zone. The supported format is Windows, and Internet Assigned Numbers Authority (IANA) time zone (also known as Olson time zone)"
ms.localizationpriority: medium
author: "SuryaLashmiS"
ms.subservice: outlook
doc_type: resourcePageType
ms.date: 04/03/2024
---

# timeZoneInformation resource type

Namespace: microsoft.graph


Represents a time zone. The supported format is Windows, and [Internet Assigned Numbers Authority (IANA) time zone](https://www.iana.org/time-zones) (also known as Olson time zone)
format as well when the current known problem is fixed.

## Properties
| Property	   | Type	|Description|
|:---------------|:--------|:----------|
|alias|string|An identifier for the time zone.|
|displayName|string|A display string that represents the time zone.|

## JSON representation

The following JSON representation shows the resource type.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.timeZoneInformation"
}-->

```json
{
  "alias": "string",
  "displayName": "string"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "timeZoneInformation resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->

