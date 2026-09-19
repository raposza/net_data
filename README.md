# Raposza Network Operations Feed - data

BaseNet can be wired to this feed with a cron job, so that a local
customization is tested against what the networks are scheduled to run
before it becomes a problem. Pull `versions.yml` on a schedule, compare it
with what your own environment is pinned to, and fail your build when the
two have drifted apart. This is a data feed, not a dashboard.

Machine-generated. Nothing in this repository is edited by hand, and a wrong
publication is corrected by a further publication, never by rewriting history.

Environment: prd.

## Files

- `versions.yml` - the current state. Fetch this one.
- `history.yml` - every state it has held, newest first.
- `README.md` - this file.

## Fields

Where a description below says what upstream states, it is taken from the
Splice release notes; nothing here is inferred from a field name.

`timestamp` is the RAPOSZA TIMESTAMP: when the file was emitted by the
Raposza service. It is not an upstream time, and it is not when any of the
values below it changed.

Under `networks`, per network:

- `current` - the version the network reports it is RUNNING. It is what the
  synchronizer answers, not what the calendar plans, so it can differ from
  `scheduled` in either direction: a network that moved early carries a
  version no schedule entry has reached yet.
- `sv-version` - the Super Validator application version reported beside it.
  A different thing from the synchronizer version, equal to it most of the
  time, and the difference is the whole story when there is one.
- `minimum` - the minimum version in force, from the operations schedule.
  Upstream states it in prose and often to a minor version only, so `"0.7"`
  here means `0.7.x` and no patch digit is invented.
- `scheduled` - the next upgrade still ahead, as `date` and `version`, or
  `null` where none is scheduled. An entry that upstream has cancelled is not
  published here; one it lists as tentative is.
- `serial-id` - upstream increments it by one for each logical synchronizer
  upgrade, and states that it carries what the migration id used to: release
  names, DNS entries, database names, chain ids and port numbers. If you pin
  any of those, this is the number they follow.
- `migration-id` - upstream states this is now FROZEN at its current value and
  configured once, and that operators keep the value they have. It is
  published because a frozen field that moves would be worth knowing about.
- `chain-id-suffix` - part of the synchronizer identity, as reported.
- `successor` and `legacy` - the versions of the synchronizer being upgraded
  to and from. Upstream supports the two coexisting during an upgrade rather
  than cutting over, so both are `null` while none is in flight, and a
  non-null `successor` is the network reporting one that is.
- `super-validators` - every Super Validator node of the network with the
  version it reports and the url it answers on. YOU ARE CONNECTED TO A NODE,
  NOT TO A NETWORK: a roster carrying more than one version is normal during
  an upgrade, and `current` alone cannot tell you whether yours has moved.
  The list is empty where no roster is reported, never absent.

`splice-latest` is the highest version the Splice tags endpoint carries. It is
different in kind from the three above: it says a release EXISTS, and says
nothing about any network taking it. A tag carries no date, so this value has
none.

Every version is a QUOTED STRING. Unquoted, `0.7` is a number to every yaml
parser there is. `timestamp` and `date` are left unquoted so that they load as
a timestamp and a date, and `migration-id` and `serial-id` are left unquoted
because upstream states them as numbers.

`history.yml` is a list under one `history:` key, newest first. Each entry is a
full snapshot of `versions.yml` as it stood, its timestamp included, so the
first entry always states what `versions.yml` states now. An entry is added when a
value changes and at no other time, so consecutive entries are never equal.

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
- `sync-global-info-mainnet` - Global Synchronizer Foundation, authority OFFICIAL, polled every 300 s
- `sync-global-sv-versions-mainnet` - Global Synchronizer Foundation, authority OFFICIAL, polled every 300 s
- `sync-global-info-testnet` - Global Synchronizer Foundation, authority OFFICIAL, polled every 300 s
- `sync-global-sv-versions-testnet` - Global Synchronizer Foundation, authority OFFICIAL, polled every 300 s
- `sync-global-info-devnet` - Global Synchronizer Foundation, authority OFFICIAL, polled every 300 s
- `sync-global-sv-versions-devnet` - Global Synchronizer Foundation, authority OFFICIAL, polled every 300 s

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
The full event catalogue, with the source, the observation and the normalizer
behind each event, is served by the api; it is not in this repository.

## Stability

The Canton networks are still evolving fast. We try our best to keep the
interface and the schema stable and coherent, but if something changes
upstream we may have to change them too.

These files are written only from banked observations. An environment that
has observed nothing writes nothing at all, so a value here is never a
placeholder and an empty field is never an outage.

## Freshness

`timestamp` moves on every publication, so it is not what this repository is
committed on: a commit is made when one of the values above it changes. No
commit means nothing changed, and the timestamp you read is the one of the
last change rather than of the last check. The heartbeat branch is what says
the writer is still running.

## Branches

- `main` - the data. One commit per change, ordinary history, nothing rewritten.
- `heartbeat` - liveness only. A timestamp and the publisher's uptime in
  hours, committed on a fixed interval whether anything changed or not, so
  that a silent data branch can be told apart from a writer that has stopped.
  It carries no data. Read nothing into its contents beyond the fact that the
  writer was alive at that moment.
