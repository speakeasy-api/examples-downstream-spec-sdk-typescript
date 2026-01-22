# User

## Example Usage

```typescript
import { User } from "@speakeasy-sdks/example-api/models";

let value: User = {
  id: "<id>",
  email: "Carissa_Lehner@yahoo.com",
  name: "<value>",
};
```

## Fields

| Field                                                                                         | Type                                                                                          | Required                                                                                      | Description                                                                                   |
| --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- |
| `id`                                                                                          | *string*                                                                                      | :heavy_check_mark:                                                                            | Unique identifier for the user                                                                |
| `email`                                                                                       | *string*                                                                                      | :heavy_check_mark:                                                                            | User's email address                                                                          |
| `name`                                                                                        | *string*                                                                                      | :heavy_check_mark:                                                                            | User's full name                                                                              |
| `createdAt`                                                                                   | [Date](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date) | :heavy_minus_sign:                                                                            | When the user was created                                                                     |