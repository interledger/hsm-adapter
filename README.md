# hsm-adapter

Protobuf definitions for the Interledger HSM Adapter — a gRPC interface for hardware security module (HSM) operations used in payment processing (PIN management, key derivation, cryptogram verification, etc.).

Each concrete implementation (e.g. Atalla AT1000, Thales 10K) is provided by the ASE (Account Serving Entity) and must implement the contracts defined here.

## Services

| Proto                   | Service                   | Description                                                   |
|-------------------------|---------------------------|---------------------------------------------------------------|
| `hsm/adapter/v1`        | `HsmAdapterService`       | Core key-management and cryptographic operations              |
| `hsm/adapter/issuer/v1` | `HsmIssuerAdapterService` | Issuer-side operations: CVV, PIN verification, EMV ARQC/ARPC  |

## Prerequisites

- [Buf CLI](https://buf.build/docs/installation) — `brew install buf`

## Validate / build

```bash
buf build
```

## Lint

```bash
buf lint
```

## Breaking-change detection

```bash
buf breaking --against '.git#branch=main'
```

## Code generation

```bash
buf generate
```

See `buf.gen.yaml` for the configured output plugins (Go, TypeScript, etc.).

## Repository layout

```
hsm-adapter/
├── proto/
│   └── hsm/
│       ├── adapter/
│       │   └── v1/
│       │       └── hsm_adapter.proto
│       └── adapter/issuer/
│           └── v1/
│               └── hsm_issuer_adapter.proto
├── buf.yaml
├── buf.gen.yaml
├── .github/
│   └── workflows/
│       ├── build.yml
│       ├── lint.yml
│       └── release.yml
│   
├── LICENSE
└── README.md
```

## License

[Apache 2.0](LICENSE)
