<!-- Start SDK Example Usage [usage] -->
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