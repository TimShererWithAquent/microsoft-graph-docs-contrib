---
description: "Automatically generated file. DO NOT MODIFY"
---

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.communications.calls.item.stop_transcription.stop_transcription_post_request_body import StopTranscriptionPostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = StopTranscriptionPostRequestBody(
	language = "en-us",
)

result = await graph_client.communications.calls.by_call_id('call-id').stop_transcription.post(request_body)


```