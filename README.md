# manyrows-go

Go libraries for integrating with [manyrows](https://app.manyrows.com).

## auth

HTTP middleware and helpers for manyrows authentication.

```go
import "github.com/manyrows/manyrows-go/auth"
```

### Middleware

Validates bearer tokens by calling the manyrows `/a/me` endpoint and stores the workspace account ID in the request context.

```go
r.Use(auth.Middleware(manyrowsBaseURL, workspaceSlug, appID))
```

### AccountIDFromContext

Extracts the account ID from the request context. Returns `false` if not present.

```go
accountID, ok := auth.AccountIDFromContext(r.Context())
```

### MustAccountID

Same as `AccountIDFromContext` but panics if the account ID is absent. Use in handlers behind `Middleware`.

```go
accountID := auth.MustAccountID(r.Context())
```
