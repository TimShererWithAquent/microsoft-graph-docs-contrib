---
description: "Automatically generated file. DO NOT MODIFY"
---

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Teams\Item\Members\Remove\RemovePostRequestBody;
use Microsoft\Graph\Beta\Generated\Models\ConversationMember;
use Microsoft\Graph\Beta\Generated\Models\AadUserConversationMember;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new RemovePostRequestBody();
$valuesConversationMember1 = new AadUserConversationMember();
$valuesConversationMember1->setOdataType('microsoft.graph.aadUserConversationMember');
$additionalData = [
	'user@odata.bind' => 'https://graph.microsoft.com/beta/users(\'jacob@contoso.com\')',
];
$valuesConversationMember1->setAdditionalData($additionalData);
$valuesArray []= $valuesConversationMember1;
$valuesConversationMember2 = new AadUserConversationMember();
$valuesConversationMember2->setOdataType('microsoft.graph.aadUserConversationMember');
$additionalData = [
	'user@odata.bind' => 'https://graph.microsoft.com/beta/users(\'alex@contoso.com\')',
];
$valuesConversationMember2->setAdditionalData($additionalData);
$valuesArray []= $valuesConversationMember2;
$requestBody->setValues($valuesArray);


$result = $graphServiceClient->teams()->byTeamId('team-id')->members()->remove()->post($requestBody)->wait();

```