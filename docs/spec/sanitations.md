# Sanitations for the Aayu MFTG AsyncAPI specification

The spec was migrated from `asyncapi-triggers/asyncapi/aayu.mftg.as2/asyncapi.yml` (AsyncAPI 2.1.0) to AsyncAPI 3.0.0.

## Changes

1. Upgraded the document to AsyncAPI 3.0.0. The three `subscribe` channels became one `messages` channel with an `operations` block of `action: receive`.
2. `x-ballerina-event-type` moved from the message to the 3.0.0 message entry; event identifiers are unchanged (`eventType` in the body).
3. `info.externalDocs` now sits under `info`, where 3.0.0 expects it.
4. `MessageFailedEvent` listed `tenantId.` (trailing dot) as a required property, which matches no property. Corrected to `tenantId`.

## Not changed

- Webhook signature verification is not declared, because the vendor documentation does not describe a signing scheme. To be confirmed with the vendor.
- Payload schemas are otherwise as in the monorepo.

Author: Dinuka Wickramasinghe
