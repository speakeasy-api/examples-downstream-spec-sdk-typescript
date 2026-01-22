# Example API TypeScript SDK

This SDK is generated from the [spec-repo-downstream-sdks](https://github.com/speakeasy-api/examples/tree/main/spec-repo-downstream-sdks) example.

## Overview

This repository demonstrates a downstream SDK that is automatically generated when changes are made to a central spec repository. The workflow:

1. A PR is created in the spec repo with OpenAPI spec changes
2. The spec repo workflow triggers this repo's `generate-sdk-from-spec.yaml` workflow
3. This workflow generates the SDK and creates a PR for review

## Installation

```bash
npm install @speakeasy-sdks/example-api
```

## Usage

```typescript
import { ExampleAPI } from "@speakeasy-sdks/example-api";

const client = new ExampleAPI();

// List users
const users = await client.users.listUsers();

// Get a specific user
const user = await client.users.getUser({ id: "user-123" });
```

## Related

- [Spec repo example](https://github.com/speakeasy-api/examples/tree/main/spec-repo-downstream-sdks)
- [Python SDK](https://github.com/speakeasy-api/examples-downstream-spec-sdk-python)

<!-- Start Summary [summary] -->
## Summary

Example API: A simple example API to demonstrate spec repo SDK generation workflow
<!-- End Summary [summary] -->

<!-- Start Table of Contents [toc] -->
## Table of Contents
<!-- $toc-max-depth=2 -->
* [Example API TypeScript SDK](#example-api-typescript-sdk)
  * [Overview](#overview)
  * [Installation](#installation)
  * [Usage](#usage)
  * [Related](#related)
  * [SDK Installation](#sdk-installation)
  * [Requirements](#requirements)
  * [SDK Example Usage](#sdk-example-usage)
  * [Available Resources and Operations](#available-resources-and-operations)
  * [Standalone functions](#standalone-functions)
  * [Retries](#retries)
  * [Error Handling](#error-handling)
  * [Server Selection](#server-selection)
  * [Custom HTTP Client](#custom-http-client)
  * [Debugging](#debugging)

<!-- End Table of Contents [toc] -->

<!-- Start SDK Installation [installation] -->
## SDK Installation

> [!TIP]
> To finish publishing your SDK to npm and others you must [run your first generation action](https://www.speakeasy.com/docs/github-setup#step-by-step-guide).


The SDK can be installed with either [npm](https://www.npmjs.com/), [pnpm](https://pnpm.io/), [bun](https://bun.sh/) or [yarn](https://classic.yarnpkg.com/en/) package managers.

### NPM

```bash
npm add https://github.com/speakeasy-api/examples-downstream-spec-sdk-typescript
```

### PNPM

```bash
pnpm add https://github.com/speakeasy-api/examples-downstream-spec-sdk-typescript
```

### Bun

```bash
bun add https://github.com/speakeasy-api/examples-downstream-spec-sdk-typescript
```

### Yarn

```bash
yarn add https://github.com/speakeasy-api/examples-downstream-spec-sdk-typescript
```

> [!NOTE]
> This package is published as an ES Module (ESM) only. For applications using
> CommonJS, use `await import()` to import and use this package.
<!-- End SDK Installation [installation] -->

<!-- Start Requirements [requirements] -->
## Requirements

For supported JavaScript runtimes, please consult [RUNTIMES.md](RUNTIMES.md).
<!-- End Requirements [requirements] -->

<!-- Start SDK Example Usage [usage] -->
## SDK Example Usage

### Example

```typescript
import { ExampleAPI } from "@speakeasy-sdks/example-api";

const exampleAPI = new ExampleAPI();

async function run() {
  const result = await exampleAPI.listUsers();

  console.log(result);
}

run();

```
<!-- End SDK Example Usage [usage] -->

<!-- Start Available Resources and Operations [operations] -->
## Available Resources and Operations

<details open>
<summary>Available methods</summary>

### [ExampleAPI SDK](docs/sdks/exampleapi/README.md)

* [listUsers](docs/sdks/exampleapi/README.md#listusers) - List all users
* [createUser](docs/sdks/exampleapi/README.md#createuser) - Create a user
* [getUser](docs/sdks/exampleapi/README.md#getuser) - Get a user

</details>
<!-- End Available Resources and Operations [operations] -->

<!-- Start Standalone functions [standalone-funcs] -->
## Standalone functions

All the methods listed above are available as standalone functions. These
functions are ideal for use in applications running in the browser, serverless
runtimes or other environments where application bundle size is a primary
concern. When using a bundler to build your application, all unused
functionality will be either excluded from the final bundle or tree-shaken away.

To read more about standalone functions, check [FUNCTIONS.md](./FUNCTIONS.md).

<details>

<summary>Available standalone functions</summary>

- [`createUser`](docs/sdks/exampleapi/README.md#createuser) - Create a user
- [`getUser`](docs/sdks/exampleapi/README.md#getuser) - Get a user
- [`listUsers`](docs/sdks/exampleapi/README.md#listusers) - List all users

</details>
<!-- End Standalone functions [standalone-funcs] -->

<!-- Start Retries [retries] -->
## Retries

Some of the endpoints in this SDK support retries.  If you use the SDK without any configuration, it will fall back to the default retry strategy provided by the API.  However, the default retry strategy can be overridden on a per-operation basis, or across the entire SDK.

To change the default retry strategy for a single API call, simply provide a retryConfig object to the call:
```typescript
import { ExampleAPI } from "@speakeasy-sdks/example-api";

const exampleAPI = new ExampleAPI();

async function run() {
  const result = await exampleAPI.listUsers({
    retries: {
      strategy: "backoff",
      backoff: {
        initialInterval: 1,
        maxInterval: 50,
        exponent: 1.1,
        maxElapsedTime: 100,
      },
      retryConnectionErrors: false,
    },
  });

  console.log(result);
}

run();

```

If you'd like to override the default retry strategy for all operations that support retries, you can provide a retryConfig at SDK initialization:
```typescript
import { ExampleAPI } from "@speakeasy-sdks/example-api";

const exampleAPI = new ExampleAPI({
  retryConfig: {
    strategy: "backoff",
    backoff: {
      initialInterval: 1,
      maxInterval: 50,
      exponent: 1.1,
      maxElapsedTime: 100,
    },
    retryConnectionErrors: false,
  },
});

async function run() {
  const result = await exampleAPI.listUsers();

  console.log(result);
}

run();

```
<!-- End Retries [retries] -->

<!-- Start Error Handling [errors] -->
## Error Handling

[`ExampleAPIError`](./src/models/errors/exampleapierror.ts) is the base class for all HTTP error responses. It has the following properties:

| Property            | Type       | Description                                            |
| ------------------- | ---------- | ------------------------------------------------------ |
| `error.message`     | `string`   | Error message                                          |
| `error.statusCode`  | `number`   | HTTP response status code eg `404`                     |
| `error.headers`     | `Headers`  | HTTP response headers                                  |
| `error.body`        | `string`   | HTTP body. Can be empty string if no body is returned. |
| `error.rawResponse` | `Response` | Raw HTTP response                                      |

### Example
```typescript
import { ExampleAPI } from "@speakeasy-sdks/example-api";
import * as errors from "@speakeasy-sdks/example-api/models/errors";

const exampleAPI = new ExampleAPI();

async function run() {
  try {
    const result = await exampleAPI.listUsers();

    console.log(result);
  } catch (error) {
    if (error instanceof errors.ExampleAPIError) {
      console.log(error.message);
      console.log(error.statusCode);
      console.log(error.body);
      console.log(error.headers);
    }
  }
}

run();

```

### Error Classes
**Primary error:**
* [`ExampleAPIError`](./src/models/errors/exampleapierror.ts): The base class for HTTP error responses.

<details><summary>Less common errors (6)</summary>

<br />

**Network errors:**
* [`ConnectionError`](./src/models/errors/httpclienterrors.ts): HTTP client was unable to make a request to a server.
* [`RequestTimeoutError`](./src/models/errors/httpclienterrors.ts): HTTP request timed out due to an AbortSignal signal.
* [`RequestAbortedError`](./src/models/errors/httpclienterrors.ts): HTTP request was aborted by the client.
* [`InvalidRequestError`](./src/models/errors/httpclienterrors.ts): Any input used to create a request is invalid.
* [`UnexpectedClientError`](./src/models/errors/httpclienterrors.ts): Unrecognised or unexpected error.


**Inherit from [`ExampleAPIError`](./src/models/errors/exampleapierror.ts)**:
* [`ResponseValidationError`](./src/models/errors/responsevalidationerror.ts): Type mismatch between the data returned from the server and the structure expected by the SDK. See `error.rawValue` for the raw value and `error.pretty()` for a nicely formatted multi-line string.

</details>
<!-- End Error Handling [errors] -->

<!-- Start Server Selection [server] -->
## Server Selection

### Override Server URL Per-Client

The default server can be overridden globally by passing a URL to the `serverURL: string` optional parameter when initializing the SDK client instance. For example:
```typescript
import { ExampleAPI } from "@speakeasy-sdks/example-api";

const exampleAPI = new ExampleAPI({
  serverURL: "https://api.example.com",
});

async function run() {
  const result = await exampleAPI.listUsers();

  console.log(result);
}

run();

```
<!-- End Server Selection [server] -->

<!-- Start Custom HTTP Client [http-client] -->
## Custom HTTP Client

The TypeScript SDK makes API calls using an `HTTPClient` that wraps the native
[Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API). This
client is a thin wrapper around `fetch` and provides the ability to attach hooks
around the request lifecycle that can be used to modify the request or handle
errors and response.

The `HTTPClient` constructor takes an optional `fetcher` argument that can be
used to integrate a third-party HTTP client or when writing tests to mock out
the HTTP client and feed in fixtures.

The following example shows how to use the `"beforeRequest"` hook to to add a
custom header and a timeout to requests and how to use the `"requestError"` hook
to log errors:

```typescript
import { ExampleAPI } from "@speakeasy-sdks/example-api";
import { HTTPClient } from "@speakeasy-sdks/example-api/lib/http";

const httpClient = new HTTPClient({
  // fetcher takes a function that has the same signature as native `fetch`.
  fetcher: (request) => {
    return fetch(request);
  }
});

httpClient.addHook("beforeRequest", (request) => {
  const nextRequest = new Request(request, {
    signal: request.signal || AbortSignal.timeout(5000)
  });

  nextRequest.headers.set("x-custom-header", "custom value");

  return nextRequest;
});

httpClient.addHook("requestError", (error, request) => {
  console.group("Request Error");
  console.log("Reason:", `${error}`);
  console.log("Endpoint:", `${request.method} ${request.url}`);
  console.groupEnd();
});

const sdk = new ExampleAPI({ httpClient: httpClient });
```
<!-- End Custom HTTP Client [http-client] -->

<!-- Start Debugging [debug] -->
## Debugging

You can setup your SDK to emit debug logs for SDK requests and responses.

You can pass a logger that matches `console`'s interface as an SDK option.

> [!WARNING]
> Beware that debug logging will reveal secrets, like API tokens in headers, in log messages printed to a console or files. It's recommended to use this feature only during local development and not in production.

```typescript
import { ExampleAPI } from "@speakeasy-sdks/example-api";

const sdk = new ExampleAPI({ debugLogger: console });
```
<!-- End Debugging [debug] -->

<!-- Placeholder for Future Speakeasy SDK Sections -->
