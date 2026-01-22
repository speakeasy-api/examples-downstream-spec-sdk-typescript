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
