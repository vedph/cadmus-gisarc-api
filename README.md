# Cadmus GISARC API

🐋 Quick Docker image build:

    docker build . -t vedph2020/cadmus-gisarc-api:3.0.1 -t vedph2020/cadmus-gisarc-api:latest

(replace with the current version).

This API uses core components from the following Cadmus libraries:

- [general and philology](https://github.com/vedph/cadmus-shell-2)
- [epigraphy](https://github.com/vedph/cadmus-epigraphy)
- [geography](https://github.com/vedph/cadmus-geo)

The GISARC project collects inscriptions from Sicily, so it has only a couple of item types:

- the inscription itself;
- the site where the inscription was found.

## Inscriptions

The inscription ID should be equal to ISicily ID, which is the authoritative source for the texts of this project.

(a) **general**:

- external IDs\*: all the IDs linked to the inscription (ISicily and eventually others).
- metadata: general purpose metadata.
- pin links: link to the site containing the inscription, if any. The site must be a site item with a metadata part having a metadatum named `eid` equal to the human-friendly ID we want to use to identify it in order to link it to inscriptions.
- geographic location(s)\*. This is used to pinpoint the inscription on a map. The link to a site is managed via the pin links part.
- date\*.

(b) **epigraphy**:

- support.
- writing.

(c) **classification**:

- categories\*: general thematic tags from a taxonomy.
- categories for periods: chronological periods categories.
- index keywords: multiple-language keywords which can be grouped under several sections ("indexes").

(d) **comment**:

- comment: generic comment.
- note: free text note. Might be useful for redactional purposes.

(e) **references**:

- references: short documentary references.
- bibliography.

(f) **text**:

- text: text or a part of it when required.
- apparatus layer: critical apparatus.
- orthography layer: can be used to annotate and categorize linguistic phenomena reflected in orthography.
- ligatures layer: can be used to annotate ligatures in text.
- comment layer: can be used to comment specific words of the text.
- chronology layer: can be used to mark specific words of the text (designating battles, priesthoods, magistrates, etc.) as related to a datation.

## Sites

(a) **general**:

- toponyms\*: the site's toponym(s).
- location\*: geographic location. This is used to pinpoint the site on a map, as a point (representing its conventionally defined center) and eventually also as a region (defined with shapes like polygons).
- metadata\*: the site's metadata. This should at least include a `eid` metadatum whose value is the human-friendly ID used to link inscriptions to sites.
- external IDs.

(b) **comment**:

- comment
- note

(c) **references**:

- references
- bibliography

## History

### 3.0.1

- 2023-06-12: updated thesauri.
- 2023-06-02: updated packages.
- 2023-05-25: updated thesauri.

### 3.0.0

- 2023-05-24:
  - updated packages (breaking change in general parts introducing [AssertedCompositeId](https://github.com/vedph/cadmus-bricks-shell/blob/master/projects/myrmidon/cadmus-refs-asserted-ids/README.md#asserted-composite-id)).
  - updated thesauri.

### 2.0.5

- 2023-05-18: updated packages and changed DI for `GraphUpdater` (see [here](https://myrmex.github.io/overview/cadmus/dev/history/b-graph/)).
- 2023-05-16: updated packages.

### 2.0.4

- 2023-04-26: updated thesauri.
- 2023-04-22: updated packages.
- 2023-04-13: added pin links fragment to profile.
- 2023-04-12: updated thesauri.

### 2.0.3

- 2023-03-15:
  - updated thesauri.
  - added phenomenon item.

### 2.0.2

- 2023-03-11:
  - updated packages.
  - added formula item to profile.
- 2023-03-02:
  - updated packages.
  - added a second categories part with a `periods` role and changed thesauri accordingly. This way the periods will be stored in their own categories part, distinct from the epigraphic categories part.

### 2.0.1

- 2023-02-11: updated packages.

### 2.0.0

- 2023-02-03: migrated to new components factory. This is a breaking change for backend components, please see [this page](https://myrmex.github.io/overview/cadmus/dev/history/#2023-02-01---backend-infrastructure-upgrade). Anyway, in the end you just have to update your libraries and a single namespace reference. Benefits include:
  - more streamlined component instantiation.
  - more functionality in components factory, including DI.
  - dropped third party dependencies.
  - adopted standard MS technologies for DI.

- 2023-01-04: integrated generic epigraphy and geography parts, thus removing the project-specific core.

### 1.0.1

- 2022-12-21: new Docker image.

### 1.0.0

- 2022-12-21: updated packages.
- 2022-12-20:
  - updated thesauri.
  - updated packages.
- 2022-11-30: updated thesauri.
