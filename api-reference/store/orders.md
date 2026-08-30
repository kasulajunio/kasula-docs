> For the complete documentation index, see [llms.txt](https://kasula.gitbook.io/kasula-docs/llms.txt). Markdown versions of documentation pages are available by appending `.md` to page URLs; this page is available as [Markdown](https://kasula.gitbook.io/kasula-docs/api-reference/store/orders.md).

# Orders

## List orders

> Returns all orders placed in the store. Does not currently support filtering or pagination.\
> \
> {% hint style="info" %}\
> Filtering and pagination are planned for v2. Subscribe to the \[changelog]\(<https://petstore.example.com/changelog>) for updates.\
> {% endhint %}<br>

```json
{"openapi":"3.0.3","info":{"title":"GitBook Petstore API","version":"1.0.0"},"tags":[{"name":"orders"}],"servers":[{"url":"https://petstore.example.com/v1","description":"Production"},{"url":"https://staging.petstore.example.com/v1","description":"Staging"}],"security":[{"bearerAuth":[]}],"components":{"securitySchemes":{"bearerAuth":{"type":"http","scheme":"bearer","description":"Pass your API key as a Bearer token in the `Authorization` header."}},"schemas":{"Order":{"type":"object","properties":{"id":{"type":"integer","format":"int64","description":"Unique order identifier."},"petId":{"type":"integer","format":"int64","description":"The ID of the animal in this order."},"quantity":{"type":"integer","description":"Number of units ordered."},"shipDate":{"type":"string","format":"date-time","description":"Expected or actual ship date in ISO 8601 format."},"complete":{"type":"boolean","description":"Whether the order has been fulfilled."}}},"Error":{"type":"object","required":["code","message","status"],"properties":{"code":{"type":"string","description":"A machine-readable error code."},"message":{"type":"string","description":"A human-readable description of the error."},"status":{"type":"integer","description":"The HTTP status code."}}}},"responses":{"Unauthorized":{"description":"Missing or invalid API key.","content":{"application/json":{"schema":{"$ref":"#/components/schemas/Error"}}}}}},"paths":{"/store/orders":{"get":{"summary":"List orders","description":"Returns all orders placed in the store. Does not currently support filtering or pagination.\n\n{% hint style=\"info\" %}\nFiltering and pagination are planned for v2. Subscribe to the [changelog](https://petstore.example.com/changelog) for updates.\n{% endhint %}\n","tags":["orders"],"operationId":"listOrders","responses":{"200":{"description":"An array of orders.","content":{"application/json":{"schema":{"type":"array","items":{"$ref":"#/components/schemas/Order"}}}}},"401":{"$ref":"#/components/responses/Unauthorized"}}}}}}
```

## Cancel an order

> Cancels an order by ID. Only orders with a status of \`pending\` can be cancelled — orders that have already shipped cannot be reversed.

```json
{"openapi":"3.0.3","info":{"title":"GitBook Petstore API","version":"1.0.0"},"tags":[{"name":"orders"}],"servers":[{"url":"https://petstore.example.com/v1","description":"Production"},{"url":"https://staging.petstore.example.com/v1","description":"Staging"}],"security":[{"bearerAuth":[]}],"components":{"securitySchemes":{"bearerAuth":{"type":"http","scheme":"bearer","description":"Pass your API key as a Bearer token in the `Authorization` header."}},"responses":{"Unauthorized":{"description":"Missing or invalid API key.","content":{"application/json":{"schema":{"$ref":"#/components/schemas/Error"}}}},"NotFound":{"description":"The requested resource could not be found.","content":{"application/json":{"schema":{"$ref":"#/components/schemas/Error"}}}}},"schemas":{"Error":{"type":"object","required":["code","message","status"],"properties":{"code":{"type":"string","description":"A machine-readable error code."},"message":{"type":"string","description":"A human-readable description of the error."},"status":{"type":"integer","description":"The HTTP status code."}}}}},"paths":{"/store/orders/{orderId}":{"delete":{"summary":"Cancel an order","description":"Cancels an order by ID. Only orders with a status of `pending` can be cancelled — orders that have already shipped cannot be reversed.","tags":["orders"],"operationId":"cancelOrder","parameters":[{"name":"orderId","in":"path","required":true,"description":"The ID of the order to cancel.","schema":{"type":"integer","format":"int64"}}],"responses":{"204":{"description":"Order cancelled successfully."},"401":{"$ref":"#/components/responses/Unauthorized"},"404":{"$ref":"#/components/responses/NotFound"},"409":{"description":"Order cannot be cancelled — it has already shipped."}}}}}}
```


---

# Agent Instructions
This documentation is published with GitBook. GitBook is the documentation platform designed so that both humans and AI agents can read, navigate, and reason over technical content effectively. Learn more at gitbook.com.

## Querying This Documentation
If you need additional information that is not directly available in this page, you can query the documentation dynamically by asking a question.

Perform an HTTP GET request on the current page URL with the `ask` query parameter, and the optional `goal` query parameter:

```
GET https://kasula.gitbook.io/kasula-docs/api-reference/store/orders.md?ask=<question>&goal=<endgoal>
```

`ask` is the immediate question: it should be specific, self-contained, and written in natural language.
`goal` is optional and describes the broader end goal you are ultimately trying to accomplish on behalf of the user. GitBook uses it to tailor the answer towards what is most useful for that goal.

The response will contain a direct answer to the question and relevant excerpts and sources from the documentation.

Use this mechanism when the answer is not explicitly present in the current page, you need clarification or additional context, or you want to retrieve related documentation sections.
