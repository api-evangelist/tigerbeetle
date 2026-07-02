# TigerBeetle (tigerbeetle)

TigerBeetle is an open-source (Apache 2.0) distributed financial accounting and transactions database, purpose-built for high-throughput, mission-critical double-entry bookkeeping and online transaction processing (OLTP). It is **not** an HTTP/REST API and ships **no OpenAPI** definition. Applications talk to a TigerBeetle cluster over a **custom binary wire protocol on TCP (default port 3000)** using official client libraries for .NET, Go, Java, Node.js, Python, Ruby, and Rust. Accounts and transfers are fixed-size, cache-line-aligned 128-byte structs sent in batches for zero-deserialization performance. TigerBeetle is self-hostable as a replicated cluster; a fully managed enterprise service is also offered via `sales@tigerbeetle.com`.

The "API" documented here is therefore a set of **client operations**, not URL endpoints: `create_accounts`, `create_transfers`, `lookup_accounts`, `lookup_transfers`, `get_account_transfers`, `get_account_balances`, `query_accounts`, and `query_transfers`. There are no REST base URLs, no OpenAPI/AsyncAPI files, and no WebSocket surface - none exist to model honestly.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/tigerbeetle/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/tigerbeetle/refs/heads/main/apis.yml)

## Tags

- Financial
- Accounting
- Transactions
- Database
- Double-Entry
- Ledger
- OLTP
- Distributed
- Open Source
- Binary Protocol

## Timestamps

- **Created:** 2026-07-02
- **Modified:** 2026-07-02

## Access Model

- **Transport:** Custom binary request/response wire protocol over TCP (default port 3000). Not HTTP, not WebSocket.
- **Clients:** Official libraries for .NET, Go, Java, Node.js, Python, Ruby, and Rust connect to a cluster and register a session.
- **Data types:** 128-byte `Account` and 128-byte `Transfer` records, batched for throughput and zero deserialization.
- **No HTTP gateway:** There is no REST endpoint, OpenAPI, SSE, or WebSocket surface to describe.

## APIs

### TigerBeetle Accounts API

Client-library operations for managing 128-byte double-entry accounts - `create_accounts` (establish immutable accounts on a ledger with debit/credit constraint flags), `lookup_accounts` (fetch by 128-bit id), and `query_accounts` (filter by ledger, code, and user_data). Binary wire-protocol operations, not HTTP endpoints.

- **Human URL:** [https://docs.tigerbeetle.com/reference/account/](https://docs.tigerbeetle.com/reference/account/)

#### Tags

- Accounts
- Ledger
- Double-Entry

#### Properties

- [Documentation](https://docs.tigerbeetle.com/reference/account/)
- [API Reference — create_accounts](https://docs.tigerbeetle.com/reference/requests/create_accounts/)
- [API Reference — lookup_accounts](https://docs.tigerbeetle.com/reference/requests/lookup_accounts/)
- [API Reference — query_accounts](https://docs.tigerbeetle.com/reference/requests/query_accounts/)

### TigerBeetle Transfers API

Client-library operations for moving funds between accounts as immutable 128-byte double-entry transfers - `create_transfers` (single-phase plus two-phase pending / post-pending / void-pending transfers, linked transfers, balancing transfers, and timeouts), `lookup_transfers`, and `query_transfers`. Delivered over the binary TCP wire protocol via the official clients.

- **Human URL:** [https://docs.tigerbeetle.com/reference/transfer/](https://docs.tigerbeetle.com/reference/transfer/)

#### Tags

- Transfers
- Two-Phase
- Pending
- Double-Entry

#### Properties

- [Documentation](https://docs.tigerbeetle.com/reference/transfer/)
- [API Reference — create_transfers](https://docs.tigerbeetle.com/reference/requests/create_transfers/)
- [API Reference — lookup_transfers](https://docs.tigerbeetle.com/reference/requests/lookup_transfers/)
- [API Reference — query_transfers](https://docs.tigerbeetle.com/reference/requests/query_transfers/)

### TigerBeetle Account Balances API

The `get_account_balances` operation returns the historical balances of an account over time (for accounts created with the `history` flag), each a point-in-time `AccountBalance` record of pending and posted debits and credits. A binary wire-protocol operation via the official clients.

- **Human URL:** [https://docs.tigerbeetle.com/reference/account-balance/](https://docs.tigerbeetle.com/reference/account-balance/)

#### Tags

- Balances
- History
- Ledger

#### Properties

- [Documentation](https://docs.tigerbeetle.com/reference/account-balance/)
- [API Reference — get_account_balances](https://docs.tigerbeetle.com/reference/requests/get_account_balances/)

### TigerBeetle Account Filter Queries API

Query surface for retrieving the transfers and balances tied to a single account. `get_account_transfers` takes an `AccountFilter` (account_id, timestamp range, limit, direction, flags) to page through an account's transfers, and the same filter drives `get_account_balances`. `QueryFilter` powers the broader `query_accounts` / `query_transfers` searches. Binary wire-protocol operations via the official clients.

- **Human URL:** [https://docs.tigerbeetle.com/reference/account-filter/](https://docs.tigerbeetle.com/reference/account-filter/)

#### Tags

- Queries
- Filters
- Transfers

#### Properties

- [Documentation — AccountFilter](https://docs.tigerbeetle.com/reference/account-filter/)
- [Documentation — QueryFilter](https://docs.tigerbeetle.com/reference/query-filter/)
- [API Reference — get_account_transfers](https://docs.tigerbeetle.com/reference/requests/get_account_transfers/)

## Common Properties

- [GitHub Organization](https://github.com/tigerbeetle)
- [LinkedIn](https://www.linkedin.com/company/tigerbeetle)
- [Website](https://tigerbeetle.com/)
- [Documentation](https://docs.tigerbeetle.com/)
- [Plans](plans/tigerbeetle-plans-pricing.yml)
- [Fin Ops](finops/tigerbeetle-finops.yml)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
