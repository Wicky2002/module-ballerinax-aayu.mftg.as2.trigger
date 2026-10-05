# Sanitations for the Aayu MFTG AsyncAPI specification

The spec was migrated from `asyncapi-triggers/asyncapi/aayu.mftg.as2/asyncapi.yml` (AsyncAPI 2.1.0) to AsyncAPI 3.0.0.

## Changes

1. Upgraded the document to AsyncAPI 3.0.0. The three `subscribe` channels became one `messages` channel with an `operations` block of `action: receive`.
2. `x-ballerina-event-type` moved from the message to the 3.0.0 message entry; event identifiers are unchanged (`eventType` in the body).
3. `info.externalDocs` now sits under `info`, where 3.0.0 expects it.
4. Aligned with the vendor webhook reference (https://aayutechnologies.com/docs/product/mft-gateway/integrations/webhook-integration/), checked 2026-10-05: added the `MESSAGE.SEND.INCOMPLETE` event, and renamed/added payload fields to match the documented payloads (`messageId`, `messageIdentifier`, `partnerIdentifier`, `stationIdentifier`, `service`, `timestamp`; `sentAt` on failures). The monorepo spec used older `*AS2ID` names and a `subject` field the docs do not show, and had a `tenantId.` typo in its required list.

## Not changed

- Signature: the vendor signs the payload with an RSA key pair (pkcs1-sha256) in the `mftg-wh-signature` header. That is asymmetric, so it cannot be declared with the current HMAC-style `x-ballerina-auth`; not declared yet.
- SFTP events use the same webhook but differ (no station fields; failure type is `MESSAGE.SEND.FAILURE`). Spec stays AS2 only to match the package name.
- The documented AS2 received example spells `Attachments` capitalised, probably a doc typo; `attachments` is optional for received events.
- Payload schemas are otherwise as in the monorepo.

Author: Dinuka Wickramasinghe
