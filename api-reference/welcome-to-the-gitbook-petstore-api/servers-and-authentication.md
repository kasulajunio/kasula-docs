> For the complete documentation index, see [llms.txt](https://kasula.gitbook.io/kasula-docs/llms.txt). Markdown versions of documentation pages are available by appending `.md` to page URLs; this page is available as [Markdown](https://kasula.gitbook.io/kasula-docs/api-reference/welcome-to-the-gitbook-petstore-api/servers-and-authentication.md).

# Servers & Authentication

#### Servers

{% tabs %}
{% tab title="Production" %}
**Base URL** `https://petstore.example.com/v1`
{% endtab %}

{% tab title="Staging" %}
**Base URL** `https://staging.petstore.example.com/v1`
{% endtab %}
{% endtabs %}

{% hint style="info" %}
Both servers are available in the **Try it** panel on each endpoint page. Use the server switcher in the top-right of the panel to toggle between Production and Staging without leaving the docs.
{% endhint %}

#### Authentication

All requests must include your API key in the `Authorization` header:

```
Authorization: Bearer YOUR_API_KEY
```

{% hint style="info" %}
Generate an API key from your [account dashboard](https://petstore.example.com/dashboard/keys). Keys are scoped to a single workspace.
{% endhint %}


---

# Agent Instructions
This documentation is published with GitBook. GitBook is the documentation platform designed so that both humans and AI agents can read, navigate, and reason over technical content effectively. Learn more at gitbook.com.

## Querying This Documentation
If you need additional information that is not directly available in this page, you can query the documentation dynamically by asking a question.

Perform an HTTP GET request on the current page URL with the `ask` query parameter, and the optional `goal` query parameter:

```
GET https://kasula.gitbook.io/kasula-docs/api-reference/welcome-to-the-gitbook-petstore-api/servers-and-authentication.md?ask=<question>&goal=<endgoal>
```

`ask` is the immediate question: it should be specific, self-contained, and written in natural language.
`goal` is optional and describes the broader end goal you are ultimately trying to accomplish on behalf of the user. GitBook uses it to tailor the answer towards what is most useful for that goal.

The response will contain a direct answer to the question and relevant excerpts and sources from the documentation.

Use this mechanism when the answer is not explicitly present in the current page, you need clarification or additional context, or you want to retrieve related documentation sections.
