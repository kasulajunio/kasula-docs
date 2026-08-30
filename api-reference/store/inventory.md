> For the complete documentation index, see [llms.txt](https://kasula.gitbook.io/kasula-docs/llms.txt). Markdown versions of documentation pages are available by appending `.md` to page URLs; this page is available as [Markdown](https://kasula.gitbook.io/kasula-docs/api-reference/store/inventory.md).

# Inventory

## List inventory

> Returns current stock levels for all pets in the store.

```json
{"openapi":"3.0.3","info":{"title":"GitBook Petstore API","version":"1.0.0"},"tags":[{"name":"inventory"}],"servers":[{"url":"https://petstore.example.com/v1","description":"Production"},{"url":"https://staging.petstore.example.com/v1","description":"Staging"}],"security":[{"bearerAuth":[]}],"components":{"securitySchemes":{"bearerAuth":{"type":"http","scheme":"bearer","description":"Pass your API key as a Bearer token in the `Authorization` header."}},"schemas":{"InventoryItem":{"type":"object","required":["petId","quantity","status"],"properties":{"petId":{"type":"integer","format":"int64","description":"The ID of the animal this entry tracks."},"quantity":{"type":"integer","description":"Current stock count."},"status":{"$ref":"#/components/schemas/PetStatus"}}},"PetStatus":{"type":"string","enum":["available","pending","sold"]},"Error":{"type":"object","required":["code","message","status"],"properties":{"code":{"type":"string","description":"A machine-readable error code."},"message":{"type":"string","description":"A human-readable description of the error."},"status":{"type":"integer","description":"The HTTP status code."}}}},"responses":{"Unauthorized":{"description":"Missing or invalid API key.","content":{"application/json":{"schema":{"$ref":"#/components/schemas/Error"}}}}}},"paths":{"/inventory":{"get":{"summary":"List inventory","description":"Returns current stock levels for all pets in the store.","tags":["inventory"],"operationId":"listInventory","responses":{"200":{"description":"An array of inventory entries.","content":{"application/json":{"schema":{"type":"array","items":{"$ref":"#/components/schemas/InventoryItem"}}}}},"401":{"$ref":"#/components/responses/Unauthorized"}}}}}}
```

## Update stock level

> Updates the stock quantity for a specific pet. Use this to record new arrivals, returns, or manual adjustments.\
> \
> {% hint style="warning" %}\
> This endpoint is \*\*experimental\*\* \u2014 the request shape may change before it reaches stable.\
> {% endhint %}<br>

```json
{"openapi":"3.0.3","info":{"title":"GitBook Petstore API","version":"1.0.0"},"tags":[{"name":"inventory"}],"servers":[{"url":"https://petstore.example.com/v1","description":"Production"},{"url":"https://staging.petstore.example.com/v1","description":"Staging"}],"security":[{"bearerAuth":[]}],"components":{"securitySchemes":{"bearerAuth":{"type":"http","scheme":"bearer","description":"Pass your API key as a Bearer token in the `Authorization` header."}},"schemas":{"InventoryUpdate":{"type":"object","required":["quantity"],"properties":{"quantity":{"type":"integer","description":"The new stock count."}}},"InventoryItem":{"type":"object","required":["petId","quantity","status"],"properties":{"petId":{"type":"integer","format":"int64","description":"The ID of the animal this entry tracks."},"quantity":{"type":"integer","description":"Current stock count."},"status":{"$ref":"#/components/schemas/PetStatus"}}},"PetStatus":{"type":"string","enum":["available","pending","sold"]},"Error":{"type":"object","required":["code","message","status"],"properties":{"code":{"type":"string","description":"A machine-readable error code."},"message":{"type":"string","description":"A human-readable description of the error."},"status":{"type":"integer","description":"The HTTP status code."}}}},"responses":{"BadRequest":{"description":"The request body is missing required fields or contains invalid values.","content":{"application/json":{"schema":{"$ref":"#/components/schemas/Error"}}}},"Unauthorized":{"description":"Missing or invalid API key.","content":{"application/json":{"schema":{"$ref":"#/components/schemas/Error"}}}},"NotFound":{"description":"The requested resource could not be found.","content":{"application/json":{"schema":{"$ref":"#/components/schemas/Error"}}}}}},"paths":{"/inventory/{petId}":{"patch":{"summary":"Update stock level","description":"Updates the stock quantity for a specific pet. Use this to record new arrivals, returns, or manual adjustments.\n\n{% hint style=\"warning\" %}\nThis endpoint is **experimental** \u2014 the request shape may change before it reaches stable.\n{% endhint %}\n","tags":["inventory"],"operationId":"updateInventory","parameters":[{"name":"petId","in":"path","required":true,"description":"The ID of the pet to update stock for.","schema":{"type":"integer","format":"int64"}}],"requestBody":{"required":true,"content":{"application/json":{"schema":{"$ref":"#/components/schemas/InventoryUpdate"}}}},"responses":{"200":{"description":"Updated inventory entry.","content":{"application/json":{"schema":{"$ref":"#/components/schemas/InventoryItem"}}}},"400":{"$ref":"#/components/responses/BadRequest"},"401":{"$ref":"#/components/responses/Unauthorized"},"404":{"$ref":"#/components/responses/NotFound"}}}}}}
```


---

# Agent Instructions
This documentation is published with GitBook. GitBook is the documentation platform designed so that both humans and AI agents can read, navigate, and reason over technical content effectively. Learn more at gitbook.com.

## Querying This Documentation
If you need additional information that is not directly available in this page, you can query the documentation dynamically by asking a question.

Perform an HTTP GET request on the current page URL with the `ask` query parameter, and the optional `goal` query parameter:

```
GET https://kasula.gitbook.io/kasula-docs/api-reference/store/inventory.md?ask=<question>&goal=<endgoal>
```

`ask` is the immediate question: it should be specific, self-contained, and written in natural language.
`goal` is optional and describes the broader end goal you are ultimately trying to accomplish on behalf of the user. GitBook uses it to tailor the answer towards what is most useful for that goal.

The response will contain a direct answer to the question and relevant excerpts and sources from the documentation.

Use this mechanism when the answer is not explicitly present in the current page, you need clarification or additional context, or you want to retrieve related documentation sections.
