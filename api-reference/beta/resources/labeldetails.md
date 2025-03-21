---
title: "labelDetails resource type"
description: "Represents the label details of an information protection label."
ms.localizationpriority: medium
author: "tommoser"
ms.subservice: "security"
doc_type: "resourcePageType"
ms.date: 07/22/2024
---

# labelDetails resource type

Namespace: microsoft.graph

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Represents the label details of an information protection label. **labelDetails** provides information about a single information protection label. Inherits from
the [parentLabelDetails](parentlabeldetails.md). Can be returned by [evaluateRemoval](../api/informationprotectionlabel-evaluateremoval.md), [evaluateApplication](../api/informationprotectionlabel-evaluateapplication.md), and [extractLabel](../api/informationprotectionlabel-extractLabel.md)

## Properties

| Property    | Type                                         | Description                                                                                                  |
| :---------- | :------------------------------------------- | :----------------------------------------------------------------------------------------------------------- |
| color       | String                                       | The color that the user interface should display for the label, if configured.                               |
| description | String                                       | The admin-defined description for the label.                                                                 |
| id          | String                                       | The label ID is a globally unique identifier (GUID).                                                         |
| isActive    | Boolean                                      | Indicates whether the label is active or not. Active labels should be hidden or disabled in user interfaces. |
| name        | String                                       | The plaintext name of the label.                                                                             |
| sensitivity | Int32                                        | The sensitivity value of the label, where lower is less sensitive.                                           |
| tooltip     | String                                       | The tooltip that should be displayed for the label in a user interface.                                      |
| parent      | parentLabelDetails | The parent label associated with a child label.                                                              |

## JSON representation

The following JSON representation shows the resource type.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.labelDetails",
  "baseType": null
}-->

```json
{
  "color": "String",
  "description": "String",
  "id": "String",
  "isActive": true,
  "name": "String",
  "sensitivity": 1024,
  "tooltip": "String"
}
```

<!-- uuid: 16cd6b66-4b1a-43a1-adaf-3a886856ed98
2019-02-04 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "labelDetails resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->

