> For the complete documentation index, see [llms.txt](https://kasula.gitbook.io/kasula-docs/llms.txt). Markdown versions of documentation pages are available by appending `.md` to page URLs; this page is available as [Markdown](https://kasula.gitbook.io/kasula-docs/api-reference/welcome-to-the-gitbook-petstore-api.md).

# Welcome to the GitBook Petstore API

This GitBook API documentation template serves as a starting point for creating clear, interactive, and user-friendly API documentation.

Use this template to explore best practices in structuring your docs, showcasing endpoints, and guiding users through your API. Everything here can be adapted to fit your own product.

#### How this demo works

This reference is automatically generated from an OpenAPI spec uploaded to this GitBook space. GitBook reads the spec and creates a page for each tag, with interactive endpoint blocks for every operation — no manual authoring required.

A few things worth noticing as you explore:

* **Page groups** — tags with no endpoints (like *Store* and *Pets*) become navigation sections automatically, keeping related endpoints grouped without any extra configuration.
* **Auto-split pages** — `##` headings inside `info.description` are automatically split into separate pages in the navigation, which is how this welcome section is structured.
* **Stability badges** — some endpoints are marked `experimental` or `beta` using the `x-stability` extension. You'll see these highlighted on the endpoint itself.
* **Deprecation warnings** — `GET /pets/{petId}` is marked deprecated with a sunset date, surfaced as a warning banner on that endpoint's page.
* **Code samples** — each endpoint includes hand-written examples in cURL, JavaScript, and Python via `x-codeSamples`, supplementing the auto-generated snippets.
* **Try it panel** — most endpoints have a live testing panel on the right. `GET /store/orders` has it disabled via `x-hideTryItPanel` to show that control is per-endpoint.

To use this template for your own API, replace the spec with your own OpenAPI file and adjust the `info.description` to match your product.


---

# Agent Instructions
This documentation is published with GitBook. GitBook is the documentation platform designed so that both humans and AI agents can read, navigate, and reason over technical content effectively. Learn more at gitbook.com.

## Querying This Documentation
If you need additional information that is not directly available in this page, you can query the documentation dynamically by asking a question.

Perform an HTTP GET request on the current page URL with the `ask` query parameter, and the optional `goal` query parameter:

```
GET https://kasula.gitbook.io/kasula-docs/api-reference/welcome-to-the-gitbook-petstore-api.md?ask=<question>&goal=<endgoal>
```

`ask` is the immediate question: it should be specific, self-contained, and written in natural language.
`goal` is optional and describes the broader end goal you are ultimately trying to accomplish on behalf of the user. GitBook uses it to tailor the answer towards what is most useful for that goal.

The response will contain a direct answer to the question and relevant excerpts and sources from the documentation.

Use this mechanism when the answer is not explicitly present in the current page, you need clarification or additional context, or you want to retrieve related documentation sections.
