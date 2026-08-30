> For the complete documentation index, see [llms.txt](https://kasula.gitbook.io/kasula-docs/llms.txt). Markdown versions of documentation pages are available by appending `.md` to page URLs; this page is available as [Markdown](https://kasula.gitbook.io/kasula-docs/api-reference/models.md).

# Models

## The PetStatus object

```json
{"openapi":"3.0.3","info":{"title":"GitBook Petstore API","version":"1.0.0"},"components":{"schemas":{"PetStatus":{"type":"string","enum":["available","pending","sold"]}}}}
```

## The NewPet object

```json
{"openapi":"3.0.3","info":{"title":"GitBook Petstore API","version":"1.0.0"},"components":{"schemas":{"NewPet":{"type":"object","required":["name","categoryId"],"properties":{"name":{"type":"string","description":"The animal's name."},"categoryId":{"type":"integer","format":"int64","description":"The ID of the category this animal belongs to."},"status":{"$ref":"#/components/schemas/PetStatus"}}},"PetStatus":{"type":"string","enum":["available","pending","sold"]}}}}
```

## The Pet object

```json
{"openapi":"3.0.3","info":{"title":"GitBook Petstore API","version":"1.0.0"},"components":{"schemas":{"Pet":{"allOf":[{"$ref":"#/components/schemas/NewPet"},{"type":"object","required":["id"],"properties":{"id":{"type":"integer","format":"int64","description":"Unique identifier assigned on creation."}}}]},"NewPet":{"type":"object","required":["name","categoryId"],"properties":{"name":{"type":"string","description":"The animal's name."},"categoryId":{"type":"integer","format":"int64","description":"The ID of the category this animal belongs to."},"status":{"$ref":"#/components/schemas/PetStatus"}}},"PetStatus":{"type":"string","enum":["available","pending","sold"]}}}}
```

## The Pets object

```json
{"openapi":"3.0.3","info":{"title":"GitBook Petstore API","version":"1.0.0"},"components":{"schemas":{"Pets":{"type":"array","items":{"$ref":"#/components/schemas/Pet"}},"Pet":{"allOf":[{"$ref":"#/components/schemas/NewPet"},{"type":"object","required":["id"],"properties":{"id":{"type":"integer","format":"int64","description":"Unique identifier assigned on creation."}}}]},"NewPet":{"type":"object","required":["name","categoryId"],"properties":{"name":{"type":"string","description":"The animal's name."},"categoryId":{"type":"integer","format":"int64","description":"The ID of the category this animal belongs to."},"status":{"$ref":"#/components/schemas/PetStatus"}}},"PetStatus":{"type":"string","enum":["available","pending","sold"]}}}}
```

## The NewCategory object

```json
{"openapi":"3.0.3","info":{"title":"GitBook Petstore API","version":"1.0.0"},"components":{"schemas":{"NewCategory":{"type":"object","required":["name"],"properties":{"name":{"type":"string","description":"The category name (e.g. Dog, Cat, Rabbit)."},"description":{"type":"string","description":"A short description of the category."}}}}}}
```

## The Category object

```json
{"openapi":"3.0.3","info":{"title":"GitBook Petstore API","version":"1.0.0"},"components":{"schemas":{"Category":{"allOf":[{"$ref":"#/components/schemas/NewCategory"},{"type":"object","required":["id"],"properties":{"id":{"type":"integer","format":"int64","description":"Unique identifier assigned on creation."}}}]},"NewCategory":{"type":"object","required":["name"],"properties":{"name":{"type":"string","description":"The category name (e.g. Dog, Cat, Rabbit)."},"description":{"type":"string","description":"A short description of the category."}}}}}}
```

## The Order object

```json
{"openapi":"3.0.3","info":{"title":"GitBook Petstore API","version":"1.0.0"},"components":{"schemas":{"Order":{"type":"object","properties":{"id":{"type":"integer","format":"int64","description":"Unique order identifier."},"petId":{"type":"integer","format":"int64","description":"The ID of the animal in this order."},"quantity":{"type":"integer","description":"Number of units ordered."},"shipDate":{"type":"string","format":"date-time","description":"Expected or actual ship date in ISO 8601 format."},"complete":{"type":"boolean","description":"Whether the order has been fulfilled."}}}}}}
```

## The InventoryItem object

```json
{"openapi":"3.0.3","info":{"title":"GitBook Petstore API","version":"1.0.0"},"components":{"schemas":{"InventoryItem":{"type":"object","required":["petId","quantity","status"],"properties":{"petId":{"type":"integer","format":"int64","description":"The ID of the animal this entry tracks."},"quantity":{"type":"integer","description":"Current stock count."},"status":{"$ref":"#/components/schemas/PetStatus"}}},"PetStatus":{"type":"string","enum":["available","pending","sold"]}}}}
```

## The InventoryUpdate object

```json
{"openapi":"3.0.3","info":{"title":"GitBook Petstore API","version":"1.0.0"},"components":{"schemas":{"InventoryUpdate":{"type":"object","required":["quantity"],"properties":{"quantity":{"type":"integer","description":"The new stock count."}}}}}}
```

## The Error object

```json
{"openapi":"3.0.3","info":{"title":"GitBook Petstore API","version":"1.0.0"},"components":{"schemas":{"Error":{"type":"object","required":["code","message","status"],"properties":{"code":{"type":"string","description":"A machine-readable error code."},"message":{"type":"string","description":"A human-readable description of the error."},"status":{"type":"integer","description":"The HTTP status code."}}}}}}
```


---

# Agent Instructions
This documentation is published with GitBook. GitBook is the documentation platform designed so that both humans and AI agents can read, navigate, and reason over technical content effectively. Learn more at gitbook.com.

## Querying This Documentation
If you need additional information that is not directly available in this page, you can query the documentation dynamically by asking a question.

Perform an HTTP GET request on the current page URL with the `ask` query parameter, and the optional `goal` query parameter:

```
GET https://kasula.gitbook.io/kasula-docs/api-reference/models.md?ask=<question>&goal=<endgoal>
```

`ask` is the immediate question: it should be specific, self-contained, and written in natural language.
`goal` is optional and describes the broader end goal you are ultimately trying to accomplish on behalf of the user. GitBook uses it to tailor the answer towards what is most useful for that goal.

The response will contain a direct answer to the question and relevant excerpts and sources from the documentation.

Use this mechanism when the answer is not explicitly present in the current page, you need clarification or additional context, or you want to retrieve related documentation sections.
