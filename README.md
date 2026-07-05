# Podbean (podbean)

Podbean is a podcast hosting, distribution, and monetization platform for creators, businesses, and networks. Its public REST API (base `https://api.podbean.com/v1`) uses OAuth 2.0 and lets third-party apps and integrations manage a user's podcast programmatically - read podcast profiles, list and publish/update/delete episodes, authorize media file uploads, embed players via oEmbed, and pull download, engagement, and advertising analytics reports.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/podbean/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/podbean/refs/heads/main/apis.yml)

## Access Model

The Podbean API is a **public, documented REST API** with **OAuth 2.0** authentication. Any developer can register an app at [developers.podbean.com](https://developers.podbean.com/) to obtain a Client ID and Client Secret. There are three ways to get a token:

- **Authorization Code** - a third-party app redirects the user through the Login Dialog (`GET /v1/dialog/oauth`), then exchanges the returned code for an access token at `POST /v1/oauth/token`. Used to act on behalf of another Podbean user's podcast.
- **Client Credentials** - an app managing **its own** podcast requests a token directly from `POST /v1/oauth/token` with `grant_type=client_credentials`.
- **Multiple Podcasts token** - agencies and networks that manage many podcasts obtain per-podcast tokens via `POST /v1/oauth/multiplePodcastsToken`.

Tokens can be inspected with `POST /v1/oauth/debugToken` and (for authorization-code apps) refreshed via the refresh-token grant. All API calls are made over HTTPS to `https://api.podbean.com/v1`.

## Tags

- Podcasting
- Podcast Hosting
- Media
- Audio
- Episodes
- Analytics
- Monetization

## Timestamps

- **Created:** 2026-07-05
- **Modified:** 2026-07-05

## APIs

### Podbean Podcasts API

Read the authorized podcast's profile and settings, and - via the Multiple Podcasts token flow - enumerate the podcasts an agency or network app is authorized to manage.

- **Human URL:** [https://developers.podbean.com/podbean-api-docs/](https://developers.podbean.com/podbean-api-docs/)
- **Base URL:** `https://api.podbean.com/v1`

#### Tags

- Podcasts
- Channels
- Account

#### Properties

- [Documentation](https://developers.podbean.com/podbean-api-docs/)
- [API Reference](https://developers.podbean.com/podbean-api-docs/#api-Podcast)
- [OpenAPI](openapi/podbean-openapi.yml)
- [Postman Collection](collections/podbean.postman_collection.json)
- [Open Collection](collections/podbean.opencollection.json)

### Podbean Episodes API

List, read, publish, update, and delete podcast episodes. Publishing references a `media_key` (and optional `logo_key`) returned by the file upload authorization flow, so the API can push new audio or video episodes end to end.

- **Human URL:** [https://developers.podbean.com/podbean-api-docs/#api-Episode](https://developers.podbean.com/podbean-api-docs/#api-Episode)
- **Base URL:** `https://api.podbean.com/v1`

#### Tags

- Episodes
- Publishing
- Content

#### Properties

- [API Reference](https://developers.podbean.com/podbean-api-docs/#api-Episode)
- [Documentation](https://help.podbean.com/support/solutions/articles/25000008051-publishing-a-new-podcast-episode-via-podbean-api)
- [OpenAPI](openapi/podbean-openapi.yml)
- [Postman Collection](collections/podbean.postman_collection.json)
- [Open Collection](collections/podbean.opencollection.json)

### Podbean Media Files API

Authorize an upload to obtain a presigned URL and a file key, PUT the media or image file directly to that URL, and list previously uploaded media files. The file key is then passed to the Episodes API when publishing.

- **Human URL:** [https://developers.podbean.com/podbean-api-docs/#api-File_upload](https://developers.podbean.com/podbean-api-docs/#api-File_upload)
- **Base URL:** `https://api.podbean.com/v1`

#### Tags

- Media
- File Upload
- Storage

#### Properties

- [API Reference](https://developers.podbean.com/podbean-api-docs/#api-File_upload)
- [OpenAPI](openapi/podbean-openapi.yml)
- [Postman Collection](collections/podbean.postman_collection.json)
- [Open Collection](collections/podbean.opencollection.json)

### Podbean Analytics API

Pull podcast performance data - download reports, listener engagement reports, and advertising reports - for reporting dashboards and external analytics tools such as Dataddo.

- **Human URL:** [https://developers.podbean.com/podbean-api-docs/#api-Analytic](https://developers.podbean.com/podbean-api-docs/#api-Analytic)
- **Base URL:** `https://api.podbean.com/v1`

#### Tags

- Analytics
- Reports
- Downloads

#### Properties

- [API Reference](https://developers.podbean.com/podbean-api-docs/#api-Analytic)
- [OpenAPI](openapi/podbean-openapi.yml)
- [Postman Collection](collections/podbean.postman_collection.json)
- [Open Collection](collections/podbean.opencollection.json)

### Podbean oEmbed API

Standard oEmbed endpoint that returns embeddable player markup and metadata for a Podbean podcast or episode URL, for use in websites, CMSs, and rich link previews. No authentication required.

- **Human URL:** [https://developers.podbean.com/apidoc/widget](https://developers.podbean.com/apidoc/widget)
- **Base URL:** `https://api.podbean.com/v1`

#### Tags

- oEmbed
- Embed
- Player

#### Properties

- [Documentation](https://developers.podbean.com/apidoc/widget)
- [API Reference](https://developers.podbean.com/podbean-api-docs/#api-oEmbed)
- [OpenAPI](openapi/podbean-openapi.yml)
- [Postman Collection](collections/podbean.postman_collection.json)
- [Open Collection](collections/podbean.opencollection.json)

## Common Properties

- [GitHub Organization](https://github.com/podbean)
- [LinkedIn](https://www.linkedin.com/company/podbean)
- [Website](https://www.podbean.com)
- [Documentation](https://developers.podbean.com/podbean-api-docs/)
- [Plans](plans/podbean-plans-pricing.yml)
- [Rate Limits](rate-limits/podbean-rate-limits.yml)
- [Fin Ops](finops/podbean-finops.yml)
- [Sign Up](https://developers.podbean.com/)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
