> For the complete documentation index, see [llms.txt](https://kasula.gitbook.io/kasula-docs/llms.txt). Markdown versions of documentation pages are available by appending `.md` to page URLs; this page is available as [Markdown](https://kasula.gitbook.io/kasula-docs/api-reference/pets/categories.md).

# Categories

## List categories

> Returns all categories available for classifying pets (e.g. dog, cat, rabbit).

```json
{"openapi":"3.0.3","info":{"title":"GitBook Petstore API","version":"1.0.0"},"tags":[{"name":"categories"}],"servers":[{"url":"https://petstore.example.com/v1","description":"Production"},{"url":"https://staging.petstore.example.com/v1","description":"Staging"}],"security":[{"bearerAuth":[]}],"components":{"securitySchemes":{"bearerAuth":{"type":"http","scheme":"bearer","description":"Pass your API key as a Bearer token in the `Authorization` header."}},"schemas":{"Category":{"allOf":[{"$ref":"#/components/schemas/NewCategory"},{"type":"object","required":["id"],"properties":{"id":{"type":"integer","format":"int64","description":"Unique identifier assigned on creation."}}}]},"NewCategory":{"type":"object","required":["name"],"properties":{"name":{"type":"string","description":"The category name (e.g. Dog, Cat, Rabbit)."},"description":{"type":"string","description":"A short description of the category."}}},"Error":{"type":"object","required":["code","message","status"],"properties":{"code":{"type":"string","description":"A machine-readable error code."},"message":{"type":"string","description":"A human-readable description of the error."},"status":{"type":"integer","description":"The HTTP status code."}}}},"responses":{"Unauthorized":{"description":"Missing or invalid API key.","content":{"application/json":{"schema":{"$ref":"#/components/schemas/Error"}}}}}},"paths":{"/categories":{"get":{"summary":"List categories","description":"Returns all categories available for classifying pets (e.g. dog, cat, rabbit).","tags":["categories"],"operationId":"listCategories","responses":{"200":{"description":"An array of categories.","content":{"application/json":{"schema":{"type":"array","items":{"$ref":"#/components/schemas/Category"}}}}},"401":{"$ref":"#/components/responses/Unauthorized"}}}}}}
```

## Create a category

> Adds a new category for classifying pets.

```json
{"openapi":"3.0.3","info":{"title":"GitBook Petstore API","version":"1.0.0"},"tags":[{"name":"categories"}],"servers":[{"url":"https://petstore.example.com/v1","description":"Production"},{"url":"https://staging.petstore.example.com/v1","description":"Staging"}],"security":[{"bearerAuth":[]}],"components":{"securitySchemes":{"bearerAuth":{"type":"http","scheme":"bearer","description":"Pass your API key as a Bearer token in the `Authorization` header."}},"schemas":{"NewCategory":{"type":"object","required":["name"],"properties":{"name":{"type":"string","description":"The category name (e.g. Dog, Cat, Rabbit)."},"description":{"type":"string","description":"A short description of the category."}}},"Category":{"allOf":[{"$ref":"#/components/schemas/NewCategory"},{"type":"object","required":["id"],"properties":{"id":{"type":"integer","format":"int64","description":"Unique identifier assigned on creation."}}}]},"Error":{"type":"object","required":["code","message","status"],"properties":{"code":{"type":"string","description":"A machine-readable error code."},"message":{"type":"string","description":"A human-readable description of the error."},"status":{"type":"integer","description":"The HTTP status code."}}}},"responses":{"BadRequest":{"description":"The request body is missing required fields or contains invalid values.","content":{"application/json":{"schema":{"$ref":"#/components/schemas/Error"}}}},"Unauthorized":{"description":"Missing or invalid API key.","content":{"application/json":{"schema":{"$ref":"#/components/schemas/Error"}}}}}},"paths":{"/categories":{"post":{"summary":"Create a category","description":"Adds a new category for classifying pets.","tags":["categories"],"operationId":"createCategory","requestBody":{"required":true,"content":{"application/json":{"schema":{"$ref":"#/components/schemas/NewCategory"}}}},"responses":{"201":{"description":"Category created successfully.","content":{"application/json":{"schema":{"$ref":"#/components/schemas/Category"}}}},"400":{"$ref":"#/components/responses/BadRequest"},"401":{"$ref":"#/components/responses/Unauthorized"}}}}}}
```


---

# Agent Instructions
This documentation is published with GitBook. GitBook is the documentation platform designed so that both humans and AI agents can read, navigate, and reason over technical content effectively. Learn more at gitbook.com.

## Querying This Documentation
If you need additional information that is not directly available in this page, you can query the documentation dynamically by asking a question.

Perform an HTTP GET request on the current page URL with the `ask` query parameter, and the optional `goal` query parameter:

```
GET https://kasula.gitbook.io/kasula-docs/api-reference/pets/categories.md?ask=<question>&goal=<endgoal>
```

`ask` is the immediate question: it should be specific, self-contained, and written in natural language.
`goal` is optional and describes the broader end goal you are ultimately trying to accomplish on behalf of the user. GitBook uses it to tailor the answer towards what is most useful for that goal.

The response will contain a direct answer to the question and relevant excerpts and sources from the documentation.

Use this mechanism when the answer is not explicitly present in the current page, you need clarification or additional context, or you want to retrieve related documentation sections.
