# keyvalidation

KeyValidation gRPC service extracted from the Sovereignite monorepo. It
implements the `KeyValidation` service from the Sovereignite API
(`github.com/sovereignite/signal/v1`): `ValidateKey` and `IssueJWT`. The service
currently runs fail-closed while design decision D-007 remains unresolved —
`ValidateKey` returns `Valid: false` for every request and `IssueJWT` refuses
all token issuance.

The package lives at the module root (`github.com/sovereignite/harbormaster`)
so other modules can import it; the `cmd/keyvalidation` binary serves it over
gRPC.

## Build & test

```sh
go build ./...
go test ./...
```

The only dependency is the generated Sovereignite API bindings, wired to the
sibling `../api` module via a `replace` directive.
