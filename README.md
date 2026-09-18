# Raposza Network Operations Feed - data

BaseNet can be wired to this feed with a cron job, so that a local
customization is tested against what the networks are scheduled to run
before it becomes a problem. Pull `versions.txt` or `feed.json` on a schedule, compare it
with what your own environment is pinned to, and fail your build when the
two have drifted apart. This is a data feed, not a dashboard.

Machine-generated. Nothing in this repository is edited by hand, and a wrong
publication is corrected by a further publication, never by rewriting history.

Environment: prd.

## Files

- `feed.json` - the published dataset, one document.
- `versions.txt` - the same facts for a person, four lines.
- `README.md` - this file.

## Provenance

Where this comes from, how often, and how it is put together. No value here
is typed by a human.

The sources polled, each on its own cadence, as this publication carries
them:

- `canton-foundation-configs` - Canton Foundation, authority OFFICIAL, polled every 300 s
- `canton-foundation-configs-runtime` - Canton Foundation, authority OFFICIAL, polled every 300 s
- `canton-foundation-cips` - Canton Foundation, authority GOVERNANCE, polled every 3600 s
- `canton-foundation-sv-operations-schedule` - Canton Foundation, authority OFFICIAL, polled every 300 s
- `canton-foundation-binaries` - Canton Foundation, authority OFFICIAL, polled every 900 s
- `splice-release-notes` - Splice project, authority OFFICIAL_PROJECT, polled every 900 s
- `splice-tags` - Splice project, authority OFFICIAL_PROJECT, polled every 900 s

Every retrieved body is stored content-addressed by its sha256 and never
overwritten, beside one journal line per attempt recording when the attempt
ran and what it found. An identical body is not stored twice, and an attempt
that retrieved nothing still leaves a line, so a source that is quiet and a
poller that has stopped are different things in the record.

Two sources are read into records. Each typed record of the SV Operations
Schedule becomes one event, keyed by the record's own upstream id; each tag
of the Splice repository becomes one event, keyed by the tag name. Every
later body that moves a field of one of those records makes a revision and a
change record. A record that disappears from a later body is marked
withdrawn rather than cancelled, because upstream marks a cancellation and
keeps the record, and a body that upstream merely re-sorted changes nothing.
Every published event names the source, the observation and the normalizer it
came from.

EVERY NETWORK VERSION HERE IS SCHEDULED, NOT RUNNING. No source this feed
reads reports what a network is currently running, so what you get is what
the operators have said they intend to do, and a date that has arrived is not
evidence that it happened. Per network, `versions.txt` shows the latest
scheduled version whose date has arrived and the minimum version in force;
the minimum is often stated upstream to a minor version only, so `0.7` there
means `0.7.x`. The last line is different in kind: it is the highest version
the tags endpoint carries, which says a release EXISTS and says nothing about
any network taking it. A tag carries no date, so these records have none.

## Stability

The Canton networks are still evolving fast. We try our best to keep the
interface and the schema stable and coherent, but if something changes
upstream we may have to change them too.

`metadata.content` states what the values in this file are: OBSERVED when
they were derived from banked observations, EMPTY when this environment has
banked none, and UNAVAILABLE when the index could not be read.

## Freshness

`metadata.publicationId` and `metadata.createdAt` identify the publication.
They move on every publication, so this repository is committed only when the
rest of the document changes: no commit here means nothing changed, and the
stamps you read are those of the last change, not of the last check.

## Branches

- `main` - the data. One commit per real change, never rewritten.
- `heartbeat` - liveness only. A timestamp and the publisher's uptime in
  hours, committed on a fixed interval whether anything changed or not, so
  that a silent data branch can be told apart from a writer that has stopped.
  It carries no data. Read nothing into its contents beyond the fact that the
  writer was alive at that moment.

## Content of this publication

`metadata.content` is `OBSERVED`.
