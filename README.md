# Realtime (realtime)

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

A topic catalog of realtime APIs, protocols, providers, and patterns. Realtime distinguishes itself from streaming by being **interactive and typically bidirectional** — channels, presence, signaling, and message envelopes flowing in both directions between clients and servers — where streaming is one-way firehose delivery.

This index documents the major realtime protocols (WebSocket, Server-Sent Events, WebRTC, MQTT, CoAP, gRPC streaming, GraphQL Subscriptions, WebTransport), hosted realtime providers (Ably, Pusher, PubNub, LiveKit, Daily, Agora, Twilio, Vonage, Amazon IVS, Cloudflare Realtime), open-source frameworks (Socket.IO, Phoenix Channels, Centrifugo), and push notification systems (OneSignal, FCM, APNs, Web Push, Pushwoosh).

**URL:** [https://github.com/api-evangelist/realtime](https://github.com/api-evangelist/realtime)

## Tags

Realtime, WebSocket, WebRTC, Server-Sent Events, MQTT, Push Notifications, Pub Sub, Presence, Signaling, Topic

## Timestamps

- **Created:** 2026-05-22
- **Modified:** 2026-05-22

## Realtime vs Streaming

Both push data on a long-lived connection, but the shape of the conversation is different:

| Dimension | Realtime | Streaming |
|---|---|---|
| Direction | Interactive, often bidirectional | One-way firehose |
| Unit of work | Channel / topic / room | Stream / log |
| Member model | First-class presence | None |
| Typical payload | Discrete event with envelope | Continuous record sequence |
| Typical providers | Ably, Pusher, PubNub, LiveKit | Kafka, Kinesis, Pub/Sub, Pulsar |

When the application needs **who is here**, **who said what**, **who is talking to whom** — that is realtime. When the application needs **every event that happened, in order, durably** — that is streaming.

## Protocol Choice Tradeoffs

| Protocol | Direction | Carrier | Best at | Watch out for |
|---|---|---|---|---|
| WebSocket | Bidirectional | TCP | General-purpose realtime web | Proxy/load-balancer config, no built-in fanout |
| Server-Sent Events | Server-to-client | HTTP | LLM token streams, dashboards | One-way only, six-connection-per-origin limit in browsers |
| WebRTC | Peer-to-peer | UDP/SRTP/SCTP | Audio, video, low-latency data | Signaling not standardized, NAT/TURN complexity |
| MQTT | Bidirectional | TCP | IoT, constrained devices | Topic design discipline required |
| CoAP | Server-to-client (Observe) | UDP | Battery-constrained IoT | Smaller ecosystem than MQTT |
| gRPC Streaming | Bidirectional | HTTP/2 | Service-to-service realtime | Browser support requires gRPC-Web/Connect |
| GraphQL Subscriptions | Server-to-client | WebSocket or SSE | Reactive UIs already on GraphQL | Subscription semantics under-specified |
| WebTransport | Bidirectional | HTTP/3 / QUIC | High-throughput streams + datagrams | Browser support still maturing |

## Hosted Realtime Provider Comparison

Categorized by primary purpose:

**Pub/Sub channels (data plane):** Ably, PubNub, Pusher Channels, Centrifugo (self-hosted), Phoenix Channels (embedded in Elixir apps), Socket.IO (Node.js framework).

**WebRTC media (audio/video/data):** LiveKit, Daily, Agora.io, Twilio Video / Live, Vonage Video API, Amazon Interactive Video Service, Cloudflare Realtime.

**Push notifications (out-of-band engagement):** OneSignal, Pushwoosh, Firebase Cloud Messaging, Apple Push Notification Service, Web Push API.

Selection axes that matter in practice:

- **Latency target** — most pub/sub providers advertise sub-100ms; PubNub markets sub-30ms ("Send a message via API and have it delivered anywhere in less than 30 ms").
- **Fanout cost model** — billed per message, per connection-minute, per peak-concurrent-connections, or per channel. Determines unit economics for broadcast vs chat use cases.
- **Persistence and replay** — Ably and PubNub retain history natively; Pusher Channels does not.
- **Presence semantics** — Ably and Pusher expose presence as first-class; Phoenix Presence implements CRDT-based distributed presence.
- **Auth model** — short-lived JWT (Ably, LiveKit), API key + signed token request (Pusher), API key + access manager (PubNub), or mTLS (IoT brokers).
- **WebRTC media topology** — SFU (LiveKit, Daily, Cloudflare Realtime SFU) versus mesh (small rooms) versus MCU (server-mixed composite).

## APIs Catalogued

The `apis.yml` indexes the following entries, grouped by category:

**Protocols and Standards** — WebSocket, Server-Sent Events, WebRTC, MQTT, CoAP, gRPC Streaming, GraphQL Subscriptions, WebTransport.

**Hosted Pub/Sub Providers** — Ably, PubNub, Pusher.

**Hosted WebRTC Providers** — LiveKit, Daily, Agora.io, Twilio Video / Live, Vonage Video API, Amazon IVS, Cloudflare Realtime.

**Open-Source Frameworks** — Socket.IO, Phoenix Channels, Centrifugo.

**Push Notifications** — OneSignal, Firebase Cloud Messaging, Apple Push Notification Service, Web Push API, Pushwoosh.

## Artifacts

### JSON Schemas

The `json-schema/` folder defines the canonical envelope shapes for realtime data:

- [Realtime Channel](json-schema/realtime-channel.json) — channel/topic/room with protocol, persistence, presence, access, and encryption properties.
- [Realtime Message Envelope](json-schema/realtime-message-envelope.json) — published-message envelope generalizing Ably, Pusher, PubNub, MQTT 5, Socket.IO, and CloudEvents-over-WebSocket.
- [Realtime Subscription](json-schema/realtime-subscription.json) — client subscription with filter, rewind, and QoS.
- [Realtime Presence](json-schema/realtime-presence.json) — presence record for enter/leave/update events on a channel.

### JSON-LD Context

- [realtime-context.jsonld](json-ld/realtime-context.jsonld) — JSON-LD context mapping the realtime vocabulary to schema.org, MQTT, WebSocket, WebRTC, and SSE specifications.

### Vocabulary

- [realtime-vocabulary.yml](vocabulary/realtime-vocabulary.yml) — terms (channel, topic, namespace, subscription, presence, peer, signaling, ICE, STUN, TURN, SDP, data channel, QoS, retention, rewind, capability, push notification), protocols, providers, and actions.

### Examples

Representative payloads under `examples/`:

- [Channel — pub/sub](examples/realtime-channel-pubsub-example.json)
- [Channel — MQTT topic](examples/realtime-channel-mqtt-topic-example.json)
- [Channel — WebRTC room](examples/realtime-channel-webrtc-room-example.json)
- [Message — chat](examples/realtime-message-chat-example.json)
- [Message — sensor telemetry](examples/realtime-message-sensor-telemetry-example.json)
- [Message — presence event](examples/realtime-message-presence-event-example.json)
- [Subscription — GraphQL subscription](examples/realtime-subscription-graphql-example.json)
- [Message — WebRTC signaling offer](examples/realtime-webrtc-signaling-offer-example.json)
- [Message — push notification](examples/realtime-push-notification-example.json)

## Common Properties

- [Portal](https://github.com/api-evangelist/realtime)
- [GitHub](https://github.com/api-evangelist/realtime)
- [JSONSchema — Channel](json-schema/realtime-channel.json)
- [JSONSchema — Message Envelope](json-schema/realtime-message-envelope.json)
- [JSONSchema — Subscription](json-schema/realtime-subscription.json)
- [JSONSchema — Presence](json-schema/realtime-presence.json)
- [JSON-LD Context](json-ld/realtime-context.jsonld)
- [Vocabulary](vocabulary/realtime-vocabulary.yml)

## Maintainers

**FN:** Kin Lane

**Email:** kin@apievangelist.com
