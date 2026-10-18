# Raposza Network Operations Feed - data

[Back to the data](README.md)

BaseNet can be wired to this feed with a cron job, so that a local
customization is tested against what the networks are scheduled to run
before it becomes a problem. Pull `versions.yml` on a schedule, compare it
with what your own environment is pinned to, and fail your build when the
two have drifted apart. This is a data feed, not a dashboard.

Machine-generated. Nothing in this repository is edited by hand, and a wrong
publication is corrected by a further publication, never by rewriting history.

Environment: prd.

## Files

- `versions.yml` - the current state, as the web page and `README.md`
  show it. Fetch this one.
- `README.md` - the same data as tables, for a person, with a link
  to the web page. Not a contract: its layout may change without notice.
- `REAL_README.md` - this file.

No history file is kept. The commit log of the data branch is the record of
every state `versions.yml` has held.

## Fields

Where a description below says what upstream states, it is taken from the
Splice release notes; nothing here is inferred from a field name.

`timestamp` is the RAPOSZA TIMESTAMP: when the file was emitted by the
Raposza service. It is not an upstream time, and it is not when any of the
values below it changed.

Under `networks`, per network - the same values, under the same names, as
the web page and `README.md` show:

- `current` - the last CONFIRMED upgrade on the SV Operations Schedule whose
  date has arrived, as `version` and `since`. The schedule states what the
  operators intend, so a date that has arrived is not proof the upgrade ran;
  `svs-on-current` and `reported` are what the network says.
- `svs-on-current` - how many Super Validator nodes report `current` in their
  own roster entry, as `count` `of` all nodes. `count` is `null` where there is
  no `current`.
- `minimum` - the oldest version a validator may run, from the schedule.
  Upstream states it in prose and often to a minor version only, so `"0.7"`
  here means `0.7.x` and no patch digit is invented.
- `next` - the earliest upgrade still ahead, as `version`, `date` and `status`
  (`CONFIRMED` or `TENTATIVE`), all `null` where none is scheduled. An entry
  upstream has cancelled is not published here.
- `reported` - the version the network's own info document states. It can lag
  the network, so it can differ from `current` in either direction.
- `serial-id` - upstream increments it by one for each logical synchronizer
  upgrade, and states that it carries what the migration id used to: release
  names, DNS entries, database names, chain ids and port numbers. If you pin
  any of those, this is the number they follow.
- `migration-id` - upstream states this is now FROZEN at its current value and
  configured once, and that operators keep the value they have. It is
  published because a frozen field that moves would be worth knowing about.
- `successor` and `legacy` - the versions of the synchronizer being upgraded
  to and from. Upstream supports the two coexisting during an upgrade rather
  than cutting over, so both are `null` while none is in flight, and a
  non-null `successor` is the network reporting one that is.
- `super-validators` - every Super Validator node of the network with the
  version it reports, the scan url it answers on, and its `sequencers`: one
  per synchronizer serial, highest first, each with `serial`, `url` and
  `role` - `legacy` below the network's `serial-id`, `successor` above it,
  `null` on it. YOU ARE CONNECTED TO A NODE, NOT TO A NETWORK: a roster
  carrying more than one version is normal during an upgrade. A node upstream
  could not read at the last poll keeps the version last read. Lists are
  empty where nothing is reported, never absent.

`splice-latest` is the highest version the Splice tags endpoint carries. It is
different in kind from everything above: it says a release EXISTS, and says
nothing about any network taking it. A tag carries no date, so this value has
none.

Every version is a QUOTED STRING. Unquoted, `0.7` is a number to every yaml
parser there is. `timestamp`, `since` and `date` are left unquoted so that they
load as a timestamp and dates, `status` and `role` as plain words, and
`migration-id`, `serial-id`, `serial` and the counts as whole numbers.

## Provenance

Where this comes from, how often, and how it is put together. No value here
is typed by a human.

The sources polled, each on its own cadence, as this publication carries
them:

- `canton-foundation-configs` - Canton Foundation, authority OFFICIAL, polled every 300 s
  [https://github.com/canton-foundation/configs.git](https://github.com/canton-foundation/configs.git)
- `canton-foundation-configs-runtime` - Canton Foundation, authority OFFICIAL, polled every 300 s
  [https://github.com/canton-foundation/configs-runtime.git](https://github.com/canton-foundation/configs-runtime.git)
- `canton-foundation-cips` - Canton Foundation, authority GOVERNANCE, polled every 3600 s
  [https://github.com/canton-foundation/cips.git](https://github.com/canton-foundation/cips.git)
- `canton-foundation-sv-operations-schedule` - Canton Foundation, authority OFFICIAL, polled every 300 s
  [https://sv-cal.canton.foundation/schedule.json](https://sv-cal.canton.foundation/schedule.json)
- `canton-foundation-binaries` - Canton Foundation, authority OFFICIAL, polled every 900 s
  [https://github.com/canton-foundation/binaries.git](https://github.com/canton-foundation/binaries.git)
- `splice-release-notes` - Splice project, authority OFFICIAL_PROJECT, polled every 900 s
  [https://github.com/canton-network/splice/releases.atom](https://github.com/canton-network/splice/releases.atom)
- `splice-tags` - Splice project, authority OFFICIAL_PROJECT, polled every 900 s
  [https://api.github.com/repos/canton-network/splice/tags?per_page=100](https://api.github.com/repos/canton-network/splice/tags?per_page=100)
- `cf-docs-splice-release-notes` - Canton Network, authority OFFICIAL, polled every 900 s
  [https://github.com/canton-network/cf-docs.git](https://github.com/canton-network/cf-docs.git)
- `sync-global-info-mainnet` - Global Synchronizer Foundation, authority OFFICIAL, polled every 300 s
  [https://docs.global.canton.network.sync.global/info](https://docs.global.canton.network.sync.global/info)
- `sync-global-sv-versions-mainnet` - Global Synchronizer Foundation, authority OFFICIAL, polled every 300 s
  [https://docs.global.canton.network.sync.global/versions](https://docs.global.canton.network.sync.global/versions)
- `sync-global-dso-mainnet` - Global Synchronizer Foundation, authority OFFICIAL, polled every 300 s
  [https://docs.global.canton.network.sync.global/dso](https://docs.global.canton.network.sync.global/dso)
- `sync-global-info-testnet` - Global Synchronizer Foundation, authority OFFICIAL, polled every 300 s
  [https://docs.test.global.canton.network.sync.global/info](https://docs.test.global.canton.network.sync.global/info)
- `sync-global-sv-versions-testnet` - Global Synchronizer Foundation, authority OFFICIAL, polled every 300 s
  [https://docs.test.global.canton.network.sync.global/versions](https://docs.test.global.canton.network.sync.global/versions)
- `sync-global-dso-testnet` - Global Synchronizer Foundation, authority OFFICIAL, polled every 300 s
  [https://docs.test.global.canton.network.sync.global/dso](https://docs.test.global.canton.network.sync.global/dso)
- `sync-global-info-devnet` - Global Synchronizer Foundation, authority OFFICIAL, polled every 300 s
  [https://docs.dev.global.canton.network.sync.global/info](https://docs.dev.global.canton.network.sync.global/info)
- `sync-global-sv-versions-devnet` - Global Synchronizer Foundation, authority OFFICIAL, polled every 300 s
  [https://docs.dev.global.canton.network.sync.global/versions](https://docs.dev.global.canton.network.sync.global/versions)
- `sync-global-dso-devnet` - Global Synchronizer Foundation, authority OFFICIAL, polled every 300 s
  [https://docs.dev.global.canton.network.sync.global/dso](https://docs.dev.global.canton.network.sync.global/dso)

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
committed on: a commit is made when one of the values above it changes, or
when something `README.md` shows changes. No commit means nothing changed,
and the timestamp you read is the one of the last change rather than of the
last check. The heartbeat branch is what says the writer is still running.
A new release of the service that rewords these two files commits once with
no value moved.

## Branches

- `main` - the data. One commit per change, ordinary history, nothing rewritten.
- `heartbeat` - liveness only. A timestamp and the publisher's uptime in
  hours, committed on a fixed interval whether anything changed or not, so
  that a silent data branch can be told apart from a writer that has stopped.
  It carries no data. Read nothing into its contents beyond the fact that the
  writer was alive at that moment.
