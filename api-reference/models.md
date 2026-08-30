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
