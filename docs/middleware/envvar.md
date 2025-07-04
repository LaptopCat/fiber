---
id: envvar
---

# EnvVar

EnvVar middleware for [Fiber](https://github.com/gofiber/fiber) that can be used to expose environment variables with various options.

## Signatures

```go
func New(config ...Config) fiber.Handler
```

## Examples

Import the middleware package that is part of the Fiber web framework

```go
import (
    "github.com/gofiber/fiber/v3"
    "github.com/gofiber/fiber/v3/middleware/envvar"
)
```

After you initiate your Fiber app, you can use the following possibilities:

```go
// Initialize default config (exports no variables)
app.Use("/expose/envvars", envvar.New())

// Or extend your config for customization
app.Use("/expose/envvars", envvar.New(
    envvar.Config{
        ExportVars: map[string]string{"testKey": "", "testDefaultKey": "testDefaultVal"},
    }),
)
```

:::note
You will need to provide a path to use the envvar middleware.
:::

## Response

Http response contract:

```json
{
  "vars": {
    "someEnvVariable": "someValue",
    "anotherEnvVariable": "anotherValue",
  }
}

```

## Config

| Property    | Type                | Description                                                                  | Default |
|:------------|:--------------------|:-----------------------------------------------------------------------------|:--------|
| ExportVars  | `map[string]string` | ExportVars specifies the environment variables that should be exported. | `nil` |

## Default Config

```go
Config{}
// Exports no environment variables
```
