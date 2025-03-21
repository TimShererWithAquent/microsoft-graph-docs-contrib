---
title: "removeContentFooterAction resource type (deprecated)"
description: "Represents an action that specifies the details on the content footer to be removed from the information, if applicable. Deprecated."
ms.localizationpriority: medium
author: "tommoser"
ms.subservice: "security"
doc_type: "resourcePageType"
ms.date: 07/22/2024
---

# removeContentFooterAction resource type (deprecated)

Namespace: microsoft.graph

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

[!INCLUDE [informationprotection-deprecate](../../includes/informationprotection-deprecate.md)]

Represents an action that specifies the details on the content footer to be removed from the information, if applicable. The [evaluateApplication](../api/informationprotectionlabel-evaluateApplication.md), [evaluateClassificationResults](../api/informationprotectionlabel-evaluateclassificationresults.md), or [evaluateRemoval](../api/informationprotectionlabel-evaluateremoval.md) APIs may return the **removeContentFooterAction** if the footer is to be removed as a result of updating or removing the label. The action instructs the consuming application to remove the specific UI element that contains the previously-applicable content footer.

## Properties

| Property       | Type              | Description                                                |
| :------------- | :---------------- | :--------------------------------------------------------- |
| uiElementNames | String collection | The name of the UI element of the footer to be removed. |

## JSON representation

The following JSON representation shows the resource type.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.removeContentFooterAction",
  "baseType": "microsoft.graph.informationProtectionAction"
}-->

```json
{
  "uiElementNames": ["String"]
}
```

<!-- uuid: 16cd6b66-4b1a-43a1-adaf-3a886856ed98
2019-02-04 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "removeContentFooterAction resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->

