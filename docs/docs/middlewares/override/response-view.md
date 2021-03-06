# Override Response view

There is the current implementation of the @@ResponseViewMiddleware@@:

<<< @/packages/common/src/platform-express/middlewares/ResponseViewMiddleware.ts

But for some reason, this implementation isn't enough to meet your needs.

With @@OverrideProvider@@ it's possible to change the default implementation like
this:

<<< @/docs/docs/snippets/middlewares/override-response-view.ts

::: warning
It's not preferable to use inheritance when you override ResponseViewMiddleware middleware. The used method signature may change in future and create a breaking change for your
own implementation.
:::

::: tip
By default, the server imports automatically your middlewares matching with this rule `${rootDir}/middlewares/**/*.ts` (See [componentScan configuration](/configuration.md)).

```
.
├── src
│   ├── controllers
│   ├── services
│   ├── middlewares
│   └── Server.ts
└── package.json
```

If not, just import your middleware in your server or edit the [componentScan configuration](/configuration.md).

```typescript
import {Configuration} from "@tsed/common";
import "./src/other/directory/MyResponseViewMiddleware";

@Configuration({
    ...
})
export class Server {
}
```
:::

