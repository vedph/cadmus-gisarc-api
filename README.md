# Cadmus GISARC API

Quick Docker image build:

    docker build . -t vedph2020/cadmus-gisarc-api:1.0.1 -t vedph2020/cadmus-gisarc-api:latest

(replace with the current version).

This API uses core components from the following Cadmus libraries:

- [general and philology](https://github.com/vedph/cadmus-shell-2)
- [epigraphy](https://github.com/vedph/cadmus-epigraphy)
- [geography](https://github.com/vedph/cadmus-geo)

The GISARC project collects inscriptions from Sicily, so it has only a couple of item types:

- the inscription itself;
- the site where the inscription was found.

## Inscriptions

The inscription ID should be equal to ISiciliy ID, which is the authoritative source for the texts of this project.

a) general:

- external IDs\*: all the IDs linked to the inscription (ISicily and eventually others).
- metadata: general purpose metadata.
- pin links: link to the site containing the inscription, if any. The site must be a site item with a metadata part having a metadatum named `hid` equal to the human-friendly ID we want to use to identify it in order to link it to inscriptions.
- geographic location(s)\*. This is used to pinpoint the inscription on a map. The link to a site is managed via the pin links part.
- date\*.

b) epigraphy:

- support.
- writing.

c) classification:

- categories\*: general thematic tags from a taxonomy.
- index keywords: multiple-language keywords which can be grouped under several sections ("indexes").

d) comment:

- comment: generic comment.
- note: free text note. Might be useful for redactional purposes.

e) references:

- references: short documentary references.
- bibliography.

f) text:

- text: text or a part of it when required.
- apparatus layer: critical apparatus.
- orthography layer: can be used to annotate and categorize linguistic phenomena reflected in orthography.
- ligatures layer: can be used to annotate ligatures in text.
- comment layer: can be used to comment specific words of the text.
- chronology layer: can be used to mark specific words of the text (designating battles, priesthoods, magistrates, etc.) as related to a datation.

## Sites

a) general:

- toponyms\*: the site's toponym(s).
- location\*: geographic location. This is used to pinpoint the site on a map, as a point (representing its conventionally defined center) and eventually also as a region (defined with shapes like polygons).
- metadata\*: the site's metadata. This should at least include a `hid` metadatum whose value is the human-friendly ID used to link inscriptions to sites.
- external IDs.

b) comment:

- comment
- note

c) references:

- references
- bibliography

## History

- 2023-01-04: integrated generic epigraphy and geography parts, thus removing the project-specific core.

### 1.0.1

- 2022-12-21: new Docker image.

### 1.0.0

- 2022-12-21: updated packages.
- 2022-12-20:
  - updated thesauri.
  - updated packages.
- 2022-11-30: updated thesauri.
