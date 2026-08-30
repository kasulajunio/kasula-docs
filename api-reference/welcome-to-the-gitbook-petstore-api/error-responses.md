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
