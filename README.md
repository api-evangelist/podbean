# Podbean (podbean)

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
