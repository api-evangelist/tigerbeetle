# TigerBeetle (tigerbeetle)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

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
