# ExampleAPI SDK

## Overview

Example API: A simple example API to demonstrate spec repo SDK generation workflow

### Available Operations

* [listUsers](#listusers) - List all users
* [createUser](#createuser) - Create a user
* [getUser](#getuser) - Get a user

## listUsers

Returns a list of users

### Example Usage

<!-- UsageSnippet language="typescript" operationID="listUsers" method="get" path="/users" -->
```typescript
import { ExampleAPI } from "@speakeasy-sdks/example-api";

const exampleAPI = new ExampleAPI();

async function run() {
  const result = await exampleAPI.listUsers();

  console.log(result);
}

run();
```

### Standalone function

The standalone function version of this method:

```typescript
import { ExampleAPICore } from "@speakeasy-sdks/example-api/core.js";
import { listUsers } from "@speakeasy-sdks/example-api/funcs/listUsers.js";

// Use `ExampleAPICore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const exampleAPI = new ExampleAPICore();

async function run() {
  const res = await listUsers(exampleAPI);
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("listUsers failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[models.User[]](../../models/.md)\>**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| errors.ExampleAPIDefaultError | 4XX, 5XX                      | \*/\*                         |

## createUser

Creates a new user

### Example Usage

<!-- UsageSnippet language="typescript" operationID="createUser" method="post" path="/users" -->
```typescript
import { ExampleAPI } from "@speakeasy-sdks/example-api";

const exampleAPI = new ExampleAPI();

async function run() {
  const result = await exampleAPI.createUser({
    email: "Aglae92@gmail.com",
    name: "<value>",
  });

  console.log(result);
}

run();
```

### Standalone function

The standalone function version of this method:

```typescript
import { ExampleAPICore } from "@speakeasy-sdks/example-api/core.js";
import { createUser } from "@speakeasy-sdks/example-api/funcs/createUser.js";

// Use `ExampleAPICore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const exampleAPI = new ExampleAPICore();

async function run() {
  const res = await createUser(exampleAPI, {
    email: "Aglae92@gmail.com",
    name: "<value>",
  });
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("createUser failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [models.CreateUserRequest](../../models/createuserrequest.md)                                                                                                                  | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[models.User](../../models/user.md)\>**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| errors.ExampleAPIDefaultError | 4XX, 5XX                      | \*/\*                         |

## getUser

Returns a single user by ID

### Example Usage

<!-- UsageSnippet language="typescript" operationID="getUser" method="get" path="/users/{id}" -->
```typescript
import { ExampleAPI } from "@speakeasy-sdks/example-api";

const exampleAPI = new ExampleAPI();

async function run() {
  const result = await exampleAPI.getUser("<id>");

  console.log(result);
}

run();
```

### Standalone function

The standalone function version of this method:

```typescript
import { ExampleAPICore } from "@speakeasy-sdks/example-api/core.js";
import { getUser } from "@speakeasy-sdks/example-api/funcs/getUser.js";

// Use `ExampleAPICore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const exampleAPI = new ExampleAPICore();

async function run() {
  const res = await getUser(exampleAPI, "<id>");
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("getUser failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `id`                                                                                                                                                                           | *string*                                                                                                                                                                       | :heavy_check_mark:                                                                                                                                                             | N/A                                                                                                                                                                            |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[models.User](../../models/user.md)\>**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| errors.ExampleAPIDefaultError | 4XX, 5XX                      | \*/\*                         |