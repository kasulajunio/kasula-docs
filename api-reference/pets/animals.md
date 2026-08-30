> For the complete documentation index, see [llms.txt](https://kasula.gitbook.io/kasula-docs/llms.txt). Markdown versions of documentation pages are available by appending `.md` to page URLs; this page is available as [Markdown](https://kasula.gitbook.io/kasula-docs/api-reference/pets/animals.md).

# Animals

## List all animals

> Returns a paginated list of all animals in the store. Use `limit` to control page size and `status` to filter by availability.

```json
{"openapi":"3.0.3","info":{"title":"GitBook Petstore API","version":"1.0.0"},"tags":[{"name":"animals"}],"servers":[{"url":"https://petstore.example.com/v1","description":"Production"},{"url":"https://staging.petstore.example.com/v1","description":"Staging"}],"security":[{"bearerAuth":[]}],"components":{"securitySchemes":{"bearerAuth":{"type":"http","scheme":"bearer","description":"Pass your API key as a Bearer token in the `Authorization` header."}},"schemas":{"PetStatus":{"type":"string","enum":["available","pending","sold"]},"Pets":{"type":"array","items":{"$ref":"#/components/schemas/Pet"}},"Pet":{"allOf":[{"$ref":"#/components/schemas/NewPet"},{"type":"object","required":["id"],"properties":{"id":{"type":"integer","format":"int64","description":"Unique identifier assigned on creation."}}}]},"NewPet":{"type":"object","required":["name","categoryId"],"properties":{"name":{"type":"string","description":"The animal's name."},"categoryId":{"type":"integer","format":"int64","description":"The ID of the category this animal belongs to."},"status":{"$ref":"#/components/schemas/PetStatus"}}},"Error":{"type":"object","required":["code","message","status"],"properties":{"code":{"type":"string","description":"A machine-readable error code."},"message":{"type":"string","description":"A human-readable description of the error."},"status":{"type":"integer","description":"The HTTP status code."}}}},"responses":{"Unauthorized":{"description":"Missing or invalid API key.","content":{"application/json":{"schema":{"$ref":"#/components/schemas/Error"}}}}}},"paths":{"/pets":{"get":{"summary":"List all animals","description":"Returns a paginated list of all animals in the store. Use `limit` to control page size and `status` to filter by availability.","tags":["animals"],"operationId":"listPets","parameters":[{"name":"limit","in":"query","description":"Maximum number of animals to return. Defaults to 20, max 100.","schema":{"type":"integer","minimum":1,"maximum":100,"default":20}},{"name":"status","in":"query","description":"Filter by availability status.","schema":{"$ref":"#/components/schemas/PetStatus"}}],"responses":{"200":{"description":"A paginated list of animals.","content":{"application/json":{"schema":{"$ref":"#/components/schemas/Pets"}}}},"401":{"$ref":"#/components/responses/Unauthorized"}}}}}}
```

## Add an animal

> Adds a new animal to the store. The `name` and `categoryId` fields are required.

```json
{"openapi":"3.0.3","info":{"title":"GitBook Petstore API","version":"1.0.0"},"tags":[{"name":"animals"}],"servers":[{"url":"https://petstore.example.com/v1","description":"Production"},{"url":"https://staging.petstore.example.com/v1","description":"Staging"}],"security":[{"bearerAuth":[]}],"components":{"securitySchemes":{"bearerAuth":{"type":"http","scheme":"bearer","description":"Pass your API key as a Bearer token in the `Authorization` header."}},"schemas":{"NewPet":{"type":"object","required":["name","categoryId"],"properties":{"name":{"type":"string","description":"The animal's name."},"categoryId":{"type":"integer","format":"int64","description":"The ID of the category this animal belongs to."},"status":{"$ref":"#/components/schemas/PetStatus"}}},"PetStatus":{"type":"string","enum":["available","pending","sold"]},"Pet":{"allOf":[{"$ref":"#/components/schemas/NewPet"},{"type":"object","required":["id"],"properties":{"id":{"type":"integer","format":"int64","description":"Unique identifier assigned on creation."}}}]},"Error":{"type":"object","required":["code","message","status"],"properties":{"code":{"type":"string","description":"A machine-readable error code."},"message":{"type":"string","description":"A human-readable description of the error."},"status":{"type":"integer","description":"The HTTP status code."}}}},"responses":{"BadRequest":{"description":"The request body is missing required fields or contains invalid values.","content":{"application/json":{"schema":{"$ref":"#/components/schemas/Error"}}}},"Unauthorized":{"description":"Missing or invalid API key.","content":{"application/json":{"schema":{"$ref":"#/components/schemas/Error"}}}}}},"paths":{"/pets":{"post":{"summary":"Add an animal","description":"Adds a new animal to the store. The `name` and `categoryId` fields are required.","tags":["animals"],"operationId":"createPet","requestBody":{"required":true,"content":{"application/json":{"schema":{"$ref":"#/components/schemas/NewPet"}}}},"responses":{"201":{"description":"Animal added successfully.","content":{"application/json":{"schema":{"$ref":"#/components/schemas/Pet"}}}},"400":{"$ref":"#/components/responses/BadRequest"},"401":{"$ref":"#/components/responses/Unauthorized"}}}}}}
```

## Get an animal

> Returns details for a single animal by ID.\
> \
> {% hint style="danger" %}\
> \*\*This endpoint is deprecated\*\* and will be removed on \*\*5 December 2030\*\*. Use \`GET /pets\` with a \`status\` filter instead.\
> {% endhint %}<br>

```json
{"openapi":"3.0.3","info":{"title":"GitBook Petstore API","version":"1.0.0"},"tags":[{"name":"animals"}],"servers":[{"url":"https://petstore.example.com/v1","description":"Production"},{"url":"https://staging.petstore.example.com/v1","description":"Staging"}],"security":[{"bearerAuth":[]}],"components":{"securitySchemes":{"bearerAuth":{"type":"http","scheme":"bearer","description":"Pass your API key as a Bearer token in the `Authorization` header."}},"schemas":{"Pet":{"allOf":[{"$ref":"#/components/schemas/NewPet"},{"type":"object","required":["id"],"properties":{"id":{"type":"integer","format":"int64","description":"Unique identifier assigned on creation."}}}]},"NewPet":{"type":"object","required":["name","categoryId"],"properties":{"name":{"type":"string","description":"The animal's name."},"categoryId":{"type":"integer","format":"int64","description":"The ID of the category this animal belongs to."},"status":{"$ref":"#/components/schemas/PetStatus"}}},"PetStatus":{"type":"string","enum":["available","pending","sold"]},"Error":{"type":"object","required":["code","message","status"],"properties":{"code":{"type":"string","description":"A machine-readable error code."},"message":{"type":"string","description":"A human-readable description of the error."},"status":{"type":"integer","description":"The HTTP status code."}}}},"responses":{"Unauthorized":{"description":"Missing or invalid API key.","content":{"application/json":{"schema":{"$ref":"#/components/schemas/Error"}}}},"NotFound":{"description":"The requested resource could not be found.","content":{"application/json":{"schema":{"$ref":"#/components/schemas/Error"}}}}}},"paths":{"/pets/{petId}":{"get":{"summary":"Get an animal","description":"Returns details for a single animal by ID.\n\n{% hint style=\"danger\" %}\n**This endpoint is deprecated** and will be removed on **5 December 2030**. Use `GET /pets` with a `status` filter instead.\n{% endhint %}\n","tags":["animals"],"operationId":"getPet","parameters":[{"name":"petId","in":"path","required":true,"description":"The ID of the animal to retrieve.","schema":{"type":"integer","format":"int64"}}],"responses":{"200":{"description":"The requested animal.","content":{"application/json":{"schema":{"$ref":"#/components/schemas/Pet"}}}},"401":{"$ref":"#/components/responses/Unauthorized"},"404":{"$ref":"#/components/responses/NotFound"}},"deprecated":true}}}}
```


---

# Agent Instructions
This documentation is published with GitBook. GitBook is the documentation platform designed so that both humans and AI agents can read, navigate, and reason over technical content effectively. Learn more at gitbook.com.

## Querying This Documentation
If you need additional information that is not directly available in this page, you can query the documentation dynamically by asking a question.

Perform an HTTP GET request on the current page URL with the `ask` query parameter, and the optional `goal` query parameter:

```
GET https://kasula.gitbook.io/kasula-docs/api-reference/pets/animals.md?ask=<question>&goal=<endgoal>
```

`ask` is the immediate question: it should be specific, self-contained, and written in natural language.
`goal` is optional and describes the broader end goal you are ultimately trying to accomplish on behalf of the user. GitBook uses it to tailor the answer towards what is most useful for that goal.

The response will contain a direct answer to the question and relevant excerpts and sources from the documentation.

Use this mechanism when the answer is not explicitly present in the current page, you need clarification or additional context, or you want to retrieve related documentation sections.
