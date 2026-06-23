# Shared Map State

The clients should not have to understand databases. The map now saves through one simple API:

```text
/api/map-state
```

The easiest shared storage for this prototype is **Cloudflare KV**. Think of it as one shared JSON save slot for the map. Everyone who logs in reads and writes the same saved marker and annotation data.

## Simple Setup

1. In Cloudflare, create a KV namespace, for example `usc-asbuilt-maps`.
2. In the Cloudflare Pages project, add a KV binding:

```text
Binding name: ASBUILT_MAPS
KV namespace: usc-asbuilt-maps
```

3. Redeploy the Pages project from `main`.
4. Open the map. After saving, the status pill should say `Shared saved`.

That is the simple version. No SQL table, no client setup, no user-facing database.

## Fallback

The API also supports D1 with binding `ASBUILT_DB`, using `migrations/0001_map_states.sql`, but KV should be the first choice for the current map because the map is just one shared JSON document.

The existing Cloudflare Access protection should stay in front of the app so only approved users can call the save API.
