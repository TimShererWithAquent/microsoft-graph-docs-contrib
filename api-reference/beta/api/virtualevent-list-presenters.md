---
title: "List presenters"
description: "Get the list of all virtualEventPresenter objects of a virtual event."
author: "frankpeng7"
ms.localizationpriority: medium
ms.subservice: "cloud-communications"
doc_type: apiPageType
ms.date: 08/02/2024
---

# List presenters

Namespace: microsoft.graph

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Get the list of all [virtualEventPresenter](../resources/virtualeventpresenter.md) objects associated with a virtual event.

Currently the supported virtual event types are: [virtualEventTownhall](../resources/virtualeventtownhall.md), [virtualEventWebinar](../resources/virtualeventwebinar.md).

[!INCLUDE [national-cloud-support](../../includes/global-only.md)]

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "virtualevent-list-presenters-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/virtualevent-list-presenters-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->

``` http
GET /solutions/virtualEvents/townhalls/{townhallId}/presenters
GET /solutions/virtualEvents/webinars/{webinarId}/presenters
```

## Request headers

|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required. Learn more about [authentication and authorization](/graph/auth/auth-concepts).|

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [virtualEventPresenter](../resources/virtualeventpresenter.md) objects in the response body.

## Examples

### Request

The following example shows how to list all presenters of a **virtualEventTownhall**.
# [HTTP](#tab/http)
<!-- {
  "blockType": "request",
  "name": "list_virtualeventpresenter",
  "sampleKeys": ["88b245ac-b0b2-f1aa-e34a-c81c27abdac2@f9448ec4-804b-46af-b810-62085248da33"]
}
-->
``` http
GET https://graph.microsoft.com/beta/solutions/virtualEvents/townhalls/88b245ac-b0b2-f1aa-e34a-c81c27abdac2@f9448ec4-804b-46af-b810-62085248da33/presenters
```

# [C#](#tab/csharp)
[!INCLUDE [sample-code](../includes/snippets/csharp/list-virtualeventpresenter-csharp-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [CLI](#tab/cli)
[!INCLUDE [sample-code](../includes/snippets/cli/list-virtualeventpresenter-cli-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [Go](#tab/go)
[!INCLUDE [sample-code](../includes/snippets/go/list-virtualeventpresenter-go-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [Java](#tab/java)
[!INCLUDE [sample-code](../includes/snippets/java/list-virtualeventpresenter-java-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [JavaScript](#tab/javascript)
[!INCLUDE [sample-code](../includes/snippets/javascript/list-virtualeventpresenter-javascript-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [PHP](#tab/php)
[!INCLUDE [sample-code](../includes/snippets/php/list-virtualeventpresenter-php-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [PowerShell](#tab/powershell)
[!INCLUDE [sample-code](../includes/snippets/powershell/list-virtualeventpresenter-powershell-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [Python](#tab/python)
[!INCLUDE [sample-code](../includes/snippets/python/list-virtualeventpresenter-python-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

---

### Response

The following example shows the response.
>**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "Collection(microsoft.graph.virtualEventPresenter)"
}
-->
``` http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "id": "831affc2-4c8a-9929-50e7-02964563b6e4",
      "identity": {
        "displayName": "Diane Demoss",
        "id": "831affc2-4c8a-9929-50e7-02964563b6e4",
        "tenantId": "77229959-e479-4a73-b6e0-ddac27be315c"
      },
      "email": "DianeDemoss@contoso.com",
      "presenterDetails": null
    },
    {
      "id": "7b7e1acd-a3e0-4533-8c1d-c1a4ca0b2e2b",
      "identity": {
        "id": "7b7e1acd-a3e0-4533-8c1d-c1a4ca0b2e2b",
        "displayName": "Kenneth Brown",
        "tenantId": "77229959-e479-4a73-b6e0-ddac27be315c"
      },
      "email": "KennethBrown@contoso.com",
      "presenterDetails": null
    }
  ]
}
```
