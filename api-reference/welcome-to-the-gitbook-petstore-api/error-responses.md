> For the complete documentation index, see [llms.txt](https://kasula.gitbook.io/kasula-docs/llms.txt). Markdown versions of documentation pages are available by appending `.md` to page URLs; this page is available as [Markdown](https://kasula.gitbook.io/kasula-docs/api-reference/welcome-to-the-gitbook-petstore-api/error-responses.md).

# Error responses

All errors follow a consistent structure:

```json
{
  "error": {
    "code": "not_found",
    "message": "The requested resource could not be found.",
    "status": 404
  }
}
```

| Status | Meaning                                   |
| ------ | ----------------------------------------- |
| `400`  | Bad request — check your request body     |
| `401`  | Unauthorized — missing or invalid API key |
| `403`  | Forbidden — insufficient permissions      |
| `404`  | Not found                                 |
| `429`  | Rate limited — back off and retry         |
| `500`  | Server error                              |

{% hint style="warning" %}
This API is for demo purposes only — **don't** use it in production.
{% endhint %}


---

# Agent Instructions
This documentation is published with GitBook. GitBook is the documentation platform designed so that both humans and AI agents can read, navigate, and reason over technical content effectively. Learn more at gitbook.com.

## Querying This Documentation
If you need additional information that is not directly available in this page, you can query the documentation dynamically by asking a question.

Perform an HTTP GET request on the current page URL with the `ask` query parameter, and the optional `goal` query parameter:

```
GET https://kasula.gitbook.io/kasula-docs/api-reference/welcome-to-the-gitbook-petstore-api/error-responses.md?ask=<question>&goal=<endgoal>
```

`ask` is the immediate question: it should be specific, self-contained, and written in natural language.
`goal` is optional and describes the broader end goal you are ultimately trying to accomplish on behalf of the user. GitBook uses it to tailor the answer towards what is most useful for that goal.

The response will contain a direct answer to the question and relevant excerpts and sources from the documentation.

Use this mechanism when the answer is not explicitly present in the current page, you need clarification or additional context, or you want to retrieve related documentation sections.
