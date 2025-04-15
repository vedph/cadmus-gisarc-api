# Cadmus GISARC API

🐋 Quick Docker image build:

    docker build . -t vedph2020/cadmus-gisarc-api:5.0.0 -t vedph2020/cadmus-gisarc-api:latest

(replace with the current version).

This API uses core components from the following Cadmus libraries:

- [general and philology](https://github.com/vedph/cadmus-shell-2)
- [epigraphy](https://github.com/vedph/cadmus-epigraphy)
- [geography](https://github.com/vedph/cadmus-geo)

The GISARC project collects inscriptions from Sicily, so it has only 3 item types:

- the **inscription** itself;
- the **site** where the inscription was found;
- the **formulas** used in inscriptions.

## Inscriptions

The inscription ID should be equal to ISicily ID, which is the authoritative source for the texts of this project.

(a) **general**:

- external IDs\* (`it.vedph.external-ids`): all the IDs linked to the inscription (ISicily and eventually others).
- metadata (`it.vedph.metadata`): general purpose metadata.
- pin links (`it.vedph.pin-links`): link to the site containing the inscription, if any. The site must be a site item with a metadata part having a metadatum named `eid` equal to the human-friendly ID we want to use to identify it in order to link it to inscriptions.
- geographic location(s)\* (`it.vedph.geo.asserted-locations`). This is used to pinpoint the inscription on a map. The link to a site is managed via the pin links part.
- date\* (`it.vedph.historical-date`).

(b) **epigraphy**:

- support (`it.vedph.epigraphy.support`).
- writing (`it.vedph.epigraphy.writing`).

(c) **classification**:

- categories\* (`it.vedph.categories:categories`): general thematic tags from a taxonomy.
- categories for periods (`it.vedph.categories:periods`): chronological periods categories.
- index keywords (`it.vedph.index-keywords`): multiple-language keywords which can be grouped under several sections ("indexes").

(d) **comment**:

- comment (`it.vedph.comment`): generic comment.
- note (`it.vedph.note`): free text note. Might be useful for redactional purposes.

(e) **references**:

- references (`it.vedph.doc-references`): short documentary references.
- bibliography (`it.vedph.bibliography`).

(f) **text**:

- text (`it.vedph.token-text`): text or a part of it when required.
- apparatus layer (`fr.it.vedph.apparatus`): critical apparatus.
- orthography layer (`fr.it.vedph.orthography`): can be used to annotate and categorize linguistic phenomena reflected in orthography.
- ligatures layer (`fr.it.vedph.epigraphy.ligatures`): can be used to annotate ligatures in text.
- comment layer (`fr.it.vedph.comment`): can be used to comment specific words of the text.
- chronology layer (`fr.it.vedph.chronology`): can be used to mark specific words of the text (designating battles, priesthoods, magistrates, etc.) as related to a datation.
- pin links layer (`fr.it.vedph.pin-links`)

## Sites

(a) **general**:

- toponyms\* (`it.vedph.geo.asserted-toponyms`): the site's toponym(s).
- location\* (`it.vedph.geo.asserted-locations`): geographic location. This is used to pinpoint the site on a map, as a point (representing its conventionally defined center) and eventually also as a region (defined with shapes like polygons).
- metadata\* (`it.vedph.metadata`): the site's metadata. This should at least include a `eid` metadatum whose value is the human-friendly ID used to link inscriptions to sites.
- external IDs (`it.vedph.external-ids`).

(b) **comment**:

- comment (`it.vedph.comment`)
- note (`it.vedph.note`)

(c) **references**:

- references (`it.vedph.doc-references`)
- bibliography (`it.vedph.bibliography`)

## Formulas

(a) **formula**:

- formula patterns (`it.vedph.epigraphy.formula-patterns`)

(b) **classification**:

- external IDs (`it.vedph.external-ids`).
- metadata (`it.vedph.metadata`)
- categories (`it.vedph.categories:formular`)
- keywords (`it.vedph.index-keywords`)

(c) **placement**:

- date (`it.vedph.historical-date`)

(d) **general**:

- note (`it.vedph.note`)
- comment (`it.vedph.comment`)

(e) **references**:

- references (`it.vedph.doc-references`)
- bibliography (`it.vedph.bibliography`)

## History

- 2025-04-15: updated packages.
- 2025-01-05: updated packages.

### 6.0.0

- 2024-11-29: ⚠️ upgraded to .NET 9.
- 2024-09-07: updated packages.
- 2024-05-24: updated packages.
- 2024-05-22: updated packages.
- 2024-02-01:
  - updated packages.
  - refactored logging.

### 5.0.0

- 2023-11-19: ⚠️ upgraded to .NET 8.
- 2023-11-08: updated thesauri.
- 2023-11-07: updated packages.

### 4.0.0

- 2023-06-17: **breaking changes** for index/graph refactoring. See the [documentation page](https://myrmex.github.io/overview/cadmus/dev/history/b-rdbms).

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
