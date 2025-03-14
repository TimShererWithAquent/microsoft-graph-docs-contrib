---
title: "List teamsApp"
description: "List apps from the Microsoft Teams app catalog."
author: "MSFTRickyCastaneda"
ms.localizationpriority: medium
ms.subservice: "teams"
doc_type: apiPageType
ms.date: 10/17/2024
---

# List teamsApp

Namespace: microsoft.graph

List [apps](../resources/teamsapp.md) from the Microsoft Teams app catalog, including apps from the Microsoft Teams store and apps from your organization's app catalog (the tenant app catalog). To get apps from your organization's app catalog only, specify `organization` as the **distributionMethod** in the request.

> [!NOTE]
> In general, the **id** of a **teamsApp** resource is generated by the server. It is not the same as the **id** specified in a Teams app manifest, unless its **distributionMethod** is `store`. For other cases, the **id** provided by the developer as part of the Teams app manifest is stamped as the **externalId** in the **teamsApp** resource.

> [!IMPORTANT]
> * Currently, this API is only supported in the user context and not in the admin view.
> * The Teams Apps that this API returns comply with the app management policies established by the admin.
> * After the Teams apps are published, it typically takes 24-48 hours for the policies to be applied, so some apps might not appear in the API results immediately.
> * For more information, see [App management policies](/microsoftteams/manage-apps#manage-org-wide-app-settings).

[!INCLUDE [national-cloud-support](../../includes/global-us.md)]

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- { "blockType": "permissions", "name": "appcatalogs_list_teamsapps" } -->
[!INCLUDE [permissions-table](../includes/permissions/appcatalogs-list-teamsapps-permissions.md)]

> [!NOTE]
> The Directory.Read.All and Directory.ReadWrite.All permissions are supported only for backward compatibility. We recommend that you update your solutions to use an alternative permission and avoid using these permissions going forward.

## HTTP request

<!-- { "blockType": "ignored" } -->

```http
GET /appCatalogs/teamsApps
```

## Optional query parameters

This method supports the `$filter`, `$select`, and `$expand` [OData query parameters](/graph/query-parameters) to help customize the response.

Using `$expand=AppDefinitions` returns more information about the state of the app, such as the **publishingState**, which reflects the app submission review status and returns whether an app is approved, rejected, or remains under review.

> **Note:** You can filter on any of the fields of the [teamsApp](../resources/teamsapp.md) object to shorten the list of results. You can use any of the following filter operations: Equal, not-equal, and, or, and not.

## Request headers

| Header        | Value                     |
|:--------------|:--------------------------|
|Authorization|Bearer {token}. Required. Learn more about [authentication and authorization](/graph/auth/auth-concepts).|

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a list of [teamsApp](../resources/teamsapp.md) objects in the response body.

## Examples

### Example 1: List all applications specific to the tenant

The following example lists all applications that are specific to your tenant.

#### Request

The following example shows a request.

# [HTTP](#tab/http)
<!-- {
  "blockType": "request",
  "name": "list_teamsapps_filter_distributionMethod"
}-->

```msgraph-interactive
GET https://graph.microsoft.com/v1.0/appCatalogs/teamsApps?$filter=distributionMethod eq 'organization'
```

# [C#](#tab/csharp)
[!INCLUDE [sample-code](../includes/snippets/csharp/list-teamsapps-filter-distributionmethod-csharp-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [CLI](#tab/cli)
[!INCLUDE [sample-code](../includes/snippets/cli/list-teamsapps-filter-distributionmethod-cli-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [Go](#tab/go)
[!INCLUDE [sample-code](../includes/snippets/go/list-teamsapps-filter-distributionmethod-go-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [Java](#tab/java)
[!INCLUDE [sample-code](../includes/snippets/java/list-teamsapps-filter-distributionmethod-java-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [JavaScript](#tab/javascript)
[!INCLUDE [sample-code](../includes/snippets/javascript/list-teamsapps-filter-distributionmethod-javascript-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [PHP](#tab/php)
[!INCLUDE [sample-code](../includes/snippets/php/list-teamsapps-filter-distributionmethod-php-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [PowerShell](#tab/powershell)
[!INCLUDE [sample-code](../includes/snippets/powershell/list-teamsapps-filter-distributionmethod-powershell-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [Python](#tab/python)
[!INCLUDE [sample-code](../includes/snippets/python/list-teamsapps-filter-distributionmethod-python-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

---

<!-- markdownlint-disable MD024 -->

#### Response

The following example shows the response.

<!-- {
  "blockType": "response",
  "@odata.type": "microsoft.graph.teamsApp",
  "truncated": true,
  "isCollection": true
} -->

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "id": "b1c5353a-7aca-41b3-830f-27d5218fe0e5",
      "externalId": "f31b1263-ba99-435a-a679-911d24850d7c",
      "displayName": "Test App",
      "distributionMethod": "organization"
    }
  ]
}
```

### Example 2: List applications with a given ID

The following example lists applications with a given ID.

#### Request

The following example shows a request.

# [HTTP](#tab/http)
<!-- {
  "blockType": "request",
  "name": "list_teamsapp_filter_id"
}-->

```msgraph-interactive
GET https://graph.microsoft.com/v1.0/appCatalogs/teamsApps?$filter=id eq 'b1c5353a-7aca-41b3-830f-27d5218fe0e5'
```

# [C#](#tab/csharp)
[!INCLUDE [sample-code](../includes/snippets/csharp/list-teamsapp-filter-id-csharp-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [CLI](#tab/cli)
[!INCLUDE [sample-code](../includes/snippets/cli/list-teamsapp-filter-id-cli-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [Go](#tab/go)
[!INCLUDE [sample-code](../includes/snippets/go/list-teamsapp-filter-id-go-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [Java](#tab/java)
[!INCLUDE [sample-code](../includes/snippets/java/list-teamsapp-filter-id-java-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [JavaScript](#tab/javascript)
[!INCLUDE [sample-code](../includes/snippets/javascript/list-teamsapp-filter-id-javascript-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [PHP](#tab/php)
[!INCLUDE [sample-code](../includes/snippets/php/list-teamsapp-filter-id-php-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [PowerShell](#tab/powershell)
[!INCLUDE [sample-code](../includes/snippets/powershell/list-teamsapp-filter-id-powershell-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [Python](#tab/python)
[!INCLUDE [sample-code](../includes/snippets/python/list-teamsapp-filter-id-python-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

---

#### Response

The following example shows the response.

<!-- {
  "blockType": "response",
  "@odata.type": "microsoft.graph.teamsApp",
  "truncated": true,
  "isCollection": true
} -->

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "id": "b1c5353a-7aca-41b3-830f-27d5218fe0e5",
      "externalId": "f31b1263-ba99-435a-a679-911d24850d7c",
      "displayName": "Test App",
      "distributionMethod": "organization"
    }
  ]
}
```

### Example 3: Find application based on the Teams app manifest ID

The following example lists applications that match the **id** specified in the Teams app manifest. In the example, the manifest ID of the Teams app is `cf1ba4c7-f94e-4d80-ba90-5594b641a8ee`.

#### Request

The following example shows a request.

# [HTTP](#tab/http)
<!-- {
  "blockType": "request",
  "name": "list_teamsapp_filter_externalid"
}-->

```msgraph-interactive
GET https://graph.microsoft.com/v1.0/appCatalogs/teamsApps?$filter=externalId eq 'cf1ba4c7-f94e-4d80-ba90-5594b641a8ee'
```

# [C#](#tab/csharp)
[!INCLUDE [sample-code](../includes/snippets/csharp/list-teamsapp-filter-externalid-csharp-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [CLI](#tab/cli)
[!INCLUDE [sample-code](../includes/snippets/cli/list-teamsapp-filter-externalid-cli-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [Go](#tab/go)
[!INCLUDE [sample-code](../includes/snippets/go/list-teamsapp-filter-externalid-go-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [Java](#tab/java)
[!INCLUDE [sample-code](../includes/snippets/java/list-teamsapp-filter-externalid-java-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [JavaScript](#tab/javascript)
[!INCLUDE [sample-code](../includes/snippets/javascript/list-teamsapp-filter-externalid-javascript-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [PHP](#tab/php)
[!INCLUDE [sample-code](../includes/snippets/php/list-teamsapp-filter-externalid-php-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [PowerShell](#tab/powershell)
[!INCLUDE [sample-code](../includes/snippets/powershell/list-teamsapp-filter-externalid-powershell-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [Python](#tab/python)
[!INCLUDE [sample-code](../includes/snippets/python/list-teamsapp-filter-externalid-python-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

---

#### Response

The following example shows the response.

<!-- {
  "blockType": "response",
  "@odata.type": "microsoft.graph.teamsApp",
  "truncated": true,
  "isCollection": true
} -->

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#appCatalogs/teamsApps",
    "value": [
        {
            "id": "22f73bbe-f67a-4dea-bd54-54cac718cb2b",
            "externalId": "cf1ba4c7-f94e-4d80-ba90-5594b641a8ee",
            "displayName": "YPA",
            "distributionMethod": "organization"
        }
    ]
}
```

### Example 4: List applications with a given ID, and return the submission review state

The following example lists applications with a given ID, and expands **appDefinitions** to return the **publishingState**, which reflects the app's submission review state. `Submitted` means the review is pending, `published` means the admin approved the app, and `rejected` means the admin rejected the app.

#### Request

The following example shows a request.

# [HTTP](#tab/http)
<!-- {
  "blockType": "request",
  "name": "list_teamsapp_with_filter_expand_appdefinitions"
}-->

```msgraph-interactive
GET https://graph.microsoft.com/v1.0/appCatalogs/teamsApps?$filter=id eq '876df28f-2e78-423b-94a5-44181bd0e225'&$expand=appDefinitions
```

# [C#](#tab/csharp)
[!INCLUDE [sample-code](../includes/snippets/csharp/list-teamsapp-with-filter-expand-appdefinitions-csharp-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [CLI](#tab/cli)
[!INCLUDE [sample-code](../includes/snippets/cli/list-teamsapp-with-filter-expand-appdefinitions-cli-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [Go](#tab/go)
[!INCLUDE [sample-code](../includes/snippets/go/list-teamsapp-with-filter-expand-appdefinitions-go-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [Java](#tab/java)
[!INCLUDE [sample-code](../includes/snippets/java/list-teamsapp-with-filter-expand-appdefinitions-java-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [JavaScript](#tab/javascript)
[!INCLUDE [sample-code](../includes/snippets/javascript/list-teamsapp-with-filter-expand-appdefinitions-javascript-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [PHP](#tab/php)
[!INCLUDE [sample-code](../includes/snippets/php/list-teamsapp-with-filter-expand-appdefinitions-php-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [PowerShell](#tab/powershell)
[!INCLUDE [sample-code](../includes/snippets/powershell/list-teamsapp-with-filter-expand-appdefinitions-powershell-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [Python](#tab/python)
[!INCLUDE [sample-code](../includes/snippets/python/list-teamsapp-with-filter-expand-appdefinitions-python-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

---

#### Response

The following example shows the response.

<!-- {
  "blockType": "response",
  "name": "list_teamsapp_with_filter_expand_appdefinitions",
  "@odata.type": "microsoft.graph.teamsApp",
  "truncated": true,
  "isCollection": true
} -->

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "id": "876df28f-2e78-423b-94a5-44181bd0e225",
      "externalId": "f31b1263-ba99-435a-a679-911d24850d7c",
      "displayName": "Test App",
      "distributionMethod": "Organization",
      "appDefinitions": [
        {
          "id": "NGQyMGNiNDUtZWViYS00ZTEyLWE3YzktMGQ0NDgzYjYxNzU2IyMxLjAuMA==",
          "teamsAppId": "876df28f-2e78-423b-94a5-44181bd0e225",
          "displayName": "Test App",
          "version": "1.0.1",
          "publishingState": "published",
          "shortDescription": "Types Of Cards.",
          "description": "This sample shows the feature where user can send different types of cards using bot.",
          "lastModifiedDateTime": "2020-11-23T21:36:00.9437445Z",
          "createdBy": null 
        }
      ]
    }
  ]
}
```

### Example 5: List the details of only those apps in the catalog that contain a bot

The following example lists only those apps in the catalog that contain a bot.

#### Request

The following example shows a request.

# [HTTP](#tab/http)
<!-- {
  "blockType": "request",
  "name": "list_teamsapp_with_bots"
}-->

```msgraph-interactive
GET https://graph.microsoft.com/v1.0/appCatalogs/teamsApps?$expand=appDefinitions($expand=bot)&$filter=appDefinitions/any(a:a/bot ne null)
```

# [C#](#tab/csharp)
[!INCLUDE [sample-code](../includes/snippets/csharp/list-teamsapp-with-bots-csharp-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [CLI](#tab/cli)
[!INCLUDE [sample-code](../includes/snippets/cli/list-teamsapp-with-bots-cli-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [Go](#tab/go)
[!INCLUDE [sample-code](../includes/snippets/go/list-teamsapp-with-bots-go-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [Java](#tab/java)
[!INCLUDE [sample-code](../includes/snippets/java/list-teamsapp-with-bots-java-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [JavaScript](#tab/javascript)
[!INCLUDE [sample-code](../includes/snippets/javascript/list-teamsapp-with-bots-javascript-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [PHP](#tab/php)
[!INCLUDE [sample-code](../includes/snippets/php/list-teamsapp-with-bots-php-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [PowerShell](#tab/powershell)
[!INCLUDE [sample-code](../includes/snippets/powershell/list-teamsapp-with-bots-powershell-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [Python](#tab/python)
[!INCLUDE [sample-code](../includes/snippets/python/list-teamsapp-with-bots-python-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

---

#### Response

The following example shows the response.

<!-- {
  "blockType": "response",
  "name": "list_teamsapp_with_bots",
  "@odata.type": "Collection(microsoft.graph.teamsApp)",
  "truncated": true
} -->

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#appCatalogs/teamsApps(appDefinitions(bot()))",
  "value": [
    {
      "id": "8a1ed7a3-5c78-46b2-8504-f9da00a1d1a6",
      "externalId": "3CAB7543-216D-47C6-986C-6247670F4663",
      "displayName": "Ducks-3",
      "distributionMethod": "organization",
      "appDefinitions": [
        {
          "@odata.etag": "ImNOTW1CR2V1VzgwczlEblVidU00UHc9PSI=",
          "id": "OGExZWQ3YTMtNWM3OC00NmIyLTg1MDQtZjlkYTAwYTFkMWE2IyMxLjAuOSMjUmVqZWN0ZWQ=",
          "teamsAppId": "8a1ed7a3-5c78-46b2-8504-f9da00a1d1a6",
          "displayName": "Ducks-3",
          "version": "1.0.9",
          "publishingState": "rejected",
          "shortDescription": "quaerat quasi magnam. slight change. 5",
          "description": "Aliquid placeat animi debitis accusamus. Non perferendis ullam. Quis est consequuntur vitae provident. Sunt laudantium id aut. slight change 5",
          "lastModifiedDateTime": "2020-11-23T21:36:00.9437445Z",
          "createdBy": {
            "application": null,
            "device": null,
            "conversation": null,
            "user": {
              "id": "70292a90-d2a7-432c-857e-55db6d8f5cd0",
              "displayName": null,
              "userIdentityType": "aadUser"
            }
          },
          "authorization": {
            "clientAppId": null,
            "requiredPermissionSet": {
              "resourceSpecificPermissions": []
            }
          },
          "bot": {
            "id": "bb9f67a4-893b-48d7-ab17-40ed466c0f16"
          }
        }
      ]
    },
    {
      "id": "30909dee-f7dd-4f89-8b3b-55de2e32489c",
      "externalId": "0ebd3f4d-ca91-495b-a227-a17d298e22cc",
      "displayName": "Self-Install-App-E2E-Tests",
      "distributionMethod": "organization",
      "appDefinitions": [
        {
          "@odata.etag": "IkwzVDlMOTBSSEdTMFducHUyYkpjVmc9PSI=",
          "id": "MzA5MDlkZWUtZjdkZC00Zjg5LThiM2ItNTVkZTJlMzI0ODljIyM2LjAuMCMjU3VibWl0dGVk",
          "teamsAppId": "30909dee-f7dd-4f89-8b3b-55de2e32489c",
          "displayName": "Self-Install-App-E2E-Tests",
          "version": "6.0.0",
          "publishingState": "submitted",
          "shortDescription": "A conversational smart assistant from MSX that surfaces real-time insights.",
          "description": "For MSX Users: A conversational role-based smart assistant that will enable Enterprise sellers (AE, ATS, SSP, TSP) to be more productive by surfacing real-time insights, recommendations, actions and notifications, and by automating repetitive tasks.",
          "lastModifiedDateTime": "2020-08-25T18:40:13.035341Z",
          "createdBy": {
            "application": null,
            "device": null,
            "conversation": null,
            "user": {
              "id": "c071a180-a220-43a1-adaf-e8db95c4a7d6",
              "displayName": null,
              "userIdentityType": "aadUser"
            }
          },
          "authorization": {
            "clientAppId": null,
            "requiredPermissionSet": {
              "resourceSpecificPermissions": []
            }
          },
          "bot": {
            "id": "da7d471b-de7d-4152-8556-1cdf7a564f6c"
          }
        }
      ]
    }
  ]
}
```

### Example 6: List applications with a given ID and return only the resource specific permissions required by the app

The following example lists the apps with a given ID and returns the resource-specific permissions that are associated with it.

#### Request

The following example shows a request.

# [HTTP](#tab/http)
<!-- {
  "blockType": "request",
  "name": "list_teamsapp_with_rsc_permissions"
}-->

```msgraph-interactive
GET  https://graph.microsoft.com/v1.0/appCatalogs/teamsApps?$filter=id+eq+'a5228c26-a9ae-4702-90e0-79a5246d2f7d'&$expand=appDefinitions($select=id,authorization)
```

# [C#](#tab/csharp)
[!INCLUDE [sample-code](../includes/snippets/csharp/list-teamsapp-with-rsc-permissions-csharp-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [CLI](#tab/cli)
[!INCLUDE [sample-code](../includes/snippets/cli/list-teamsapp-with-rsc-permissions-cli-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [Go](#tab/go)
[!INCLUDE [sample-code](../includes/snippets/go/list-teamsapp-with-rsc-permissions-go-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [Java](#tab/java)
[!INCLUDE [sample-code](../includes/snippets/java/list-teamsapp-with-rsc-permissions-java-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [JavaScript](#tab/javascript)
[!INCLUDE [sample-code](../includes/snippets/javascript/list-teamsapp-with-rsc-permissions-javascript-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [PHP](#tab/php)
[!INCLUDE [sample-code](../includes/snippets/php/list-teamsapp-with-rsc-permissions-php-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [PowerShell](#tab/powershell)
[!INCLUDE [sample-code](../includes/snippets/powershell/list-teamsapp-with-rsc-permissions-powershell-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [Python](#tab/python)
[!INCLUDE [sample-code](../includes/snippets/python/list-teamsapp-with-rsc-permissions-python-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

---

#### Response

The following example shows the response.

<!-- {
  "blockType": "response",
  "name": "list_teamsapp_with_rsc_permissions",
  "@odata.type": "Collection(microsoft.graph.teamsApp)",
  "truncated": true
} -->

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#appCatalogs/teamsApps(appDefinitions(id,authorization))",
  "value": [
    {
      "id": "a5228c26-a9ae-4702-90e0-79a5246d2f7d",
      "externalId": "a55ec032-36e9-4b60-b604-34b2fe55abf1",
      "displayName": "teamsDelegatedRscTests",
      "distributionMethod": "organization",
      "appDefinitions@odata.context": "https://graph.microsoft.com/v1.0/$metadata#appCatalogs/teamsApps('a5228c26-a9ae-4702-90e0-79a5246d2f7d')/appDefinitions(id,authorization)",
      "appDefinitions": [
        {
          "id": "YTUyMjhjMjYtYTlhZS00NzAyLTkwZTAtNzlhNTI0NmQyZjdkIyMxLjAuMCMjUHVibGlzaGVk",
          "authorization": {
            "clientAppId": "6ed63604-0ba7-4a28-bb3a-dda03ea18d54",
            "requiredPermissionSet": {
              "resourceSpecificPermissions": [
                {
                  "permissionValue": "Channel.Create.Group",
                  "permissionType": "application"
                },
                {
                  "permissionValue": "Channel.Delete.Group",
                  "permissionType": "application"
                },
                {
                  "permissionValue": "ChannelMeeting.ReadBasic.Group",
                  "permissionType": "delegated"
                }
              ]
            }
          }
        }
      ]
    }
  ]
}
```

## Related content

- [List apps installed in a team](team-list-installedapps.md) <!-- - [List apps installed in a chat](chat-list-installedapps.md) -->
- [List apps installed in the personal scope of a user](userteamwork-list-installedapps.md)
- [Microsoft Graph service-specific throttling limits](/graph/throttling-limits#microsoft-teams-service-limits)
- [Request resource-specific consent for apps](/microsoftteams/platform/graph-api/rsc/resource-specific-consent)

