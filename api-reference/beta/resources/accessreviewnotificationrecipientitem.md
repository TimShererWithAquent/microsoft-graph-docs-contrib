---
title: "accessReviewNotificationRecipientItem resource type"
description: "Defines users or groups who will receive notifications access review notifications."
author: "jyothig123"
ms.localizationpriority: medium
ms.subservice: "entra-id-governance"
doc_type: resourcePageType
ms.date: 03/21/2024
---

# accessReviewNotificationRecipientItem resource type

Namespace: microsoft.graph

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

[!INCLUDE [accessreviews-disclaimer-v2](../../includes/accessreviews-disclaimer-v2.md)]


Represents a Microsoft Entra [access review](accessreviewsv2-overview.md) notification event on an instance of a review. This item contains an email template type and recipient properties to enable sending certain type of notifications for a given [access review instance](accessreviewinstance.md).

## Properties

| Property                     | Type     | Description                          |
| :--------------------------- | :------  | :----------                          |
| notificationTemplateType  |String  | Indicates the type of access review email to be sent. Supported template type is `CompletedAdditionalRecipients` which sends review completion notifications to the recipients.|
| notificationRecipientScope |[accessReviewNotificationRecipientScope](../resources/accessreviewnotificationrecipientscope.md)  | Determines the recipient of the notification email.|

## Relationships
None.


## JSON representation

The following JSON representation shows the resource type.

<!-- {
  "blockType": "resource",
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.accessReviewNotificationRecipientItem",
  "openType": true
}
-->

```json
{
  "@odata.type":"#microsoft.graph.accessReviewNotificationRecipientItem",
  "notificationRecipientScope": {
      "@odata.type":"#microsoft.graph.accessReviewNotificationRecipientQueryScope"                
    },
  "notificationTemplateType": "String"
}
```
