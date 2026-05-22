# Realtime (realtime)

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
