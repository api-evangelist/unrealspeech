# Unreal Speech (unrealspeech)

Unreal Speech is a low-cost, high-scale text-to-speech (TTS) API for turning text into natural-sounding speech. It exposes a small REST surface - a low-latency HTTP streaming endpoint, a synchronous speech endpoint that returns an MP3 plus per-word or per-sentence timestamps, and an asynchronous synthesis tasks endpoint for long-form audio up to 500,000 characters. Requests are authenticated with a Bearer API key issued from the dashboard, and pricing is metered per character with a free monthly allowance.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/unrealspeech/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/unrealspeech/refs/heads/main/apis.yml)

## Access Model

Unreal Speech is a hosted, commercial API - there is no self-hosted or open-source server for the speech engine itself. To use it you:

1. Create an account and get an API key from the [dashboard](https://app.unrealspeech.com).
2. Send requests to the REST base URL with an `Authorization: Bearer <API_KEY>` header and a JSON body.
3. Are billed per synthesized character, with a free monthly allowance (about 250K characters / ~6 hours of audio) before any paid plan or overage applies.

Open-source SDKs (Python, Node.js, React Native) wrap the same REST endpoints; they are convenience clients, not a self-hostable service.

**Base URL:** `https://api.v7.unrealspeech.com`

**Authentication:** Bearer API key - `Authorization: Bearer <API_KEY>` - obtained from the dashboard.

> Note on versioning: the base host carries a version segment that has advanced over time (the published Python SDK references `api.v6.unrealspeech.com` while the live API reference documents `api.v7.unrealspeech.com`). The paths (`/speech`, `/stream`, `/synthesisTasks`) are stable across versions. Confirm the current host in the [API reference](https://docs.unrealspeech.com/) before integrating.

## Tags

- Text to Speech
- TTS
- Speech Synthesis
- Audio
- Voice
- AI

## Timestamps

- **Created:** 2026-07-11
- **Modified:** 2026-07-11

## APIs

### Unreal Speech Speech API

Synchronous text-to-speech for medium-length text (up to 3,000 characters). Returns an MP3 audio URL plus word- or sentence-level timestamp URLs, with selectable voice, bitrate, speed, and pitch.

- **Human URL:** [https://docs.unrealspeech.com/reference/speech](https://docs.unrealspeech.com/reference/speech)
- **Base URL:** `https://api.v7.unrealspeech.com`
- **Endpoint:** `POST /speech`

### Unreal Speech Stream API

Low-latency HTTP streaming synthesis for short text (up to 1,000 characters), returning audio bytes directly in the response - typically in around 0.3 seconds - for time-sensitive uses like chatbots and voice agents. This is HTTP chunked streaming, not a WebSocket.

- **Human URL:** [https://docs.unrealspeech.com/reference/stream](https://docs.unrealspeech.com/reference/stream)
- **Base URL:** `https://api.v7.unrealspeech.com`
- **Endpoint:** `POST /stream`

### Unreal Speech Synthesis Tasks API

Asynchronous synthesis for long-form audio (up to 500,000 characters, e.g. audiobooks and articles). Submit text and immediately receive a TaskId, then poll the task to retrieve status and the output audio URI(s); supports an optional callback URL.

- **Human URL:** [https://docs.unrealspeech.com/reference/synthesistasks](https://docs.unrealspeech.com/reference/synthesistasks)
- **Base URL:** `https://api.v7.unrealspeech.com`
- **Endpoints:** `POST /synthesisTasks`, `GET /synthesisTasks`

## Voices

Documented voices: Scarlett, Dan, Liv, Will, Amy. Output is MP3 (also PCM/mu-law codecs on `/stream`), with selectable bitrate (up to 320k), speed (-1.0 to 1.0), and pitch (0.5 to 1.5).

## Common Properties

- [GitHub Organization](https://github.com/unrealspeech)
- [LinkedIn](https://www.linkedin.com/company/unrealspeech)
- [Website](https://unrealspeech.com)
- [Documentation](https://docs.unrealspeech.com)
- [Plans](plans/unrealspeech-plans-pricing.yml)
- [Rate Limits](rate-limits/unrealspeech-rate-limits.yml)
- [Fin Ops](finops/unrealspeech-finops.yml)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
