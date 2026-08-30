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
