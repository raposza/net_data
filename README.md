# Raposza Network Operations Feed

**The web page: [https://net.raposza.com/](https://net.raposza.com/)** - this
README carries part of it, for readers who cannot reach it. The planned events
of the coming weeks, the log of what changed, and the freshness of each source
are on the page only.

**Read [REAL_README.md](REAL_README.md) before you build on this data** - what every field
means, where it comes from, and what is guaranteed.

What is deployed on the Canton Network, what is scheduled, and which Super
Validator node runs what. Machine-generated from public sources; nothing here
is edited by hand. The same values are in [`versions.yml`](versions.yml) for machines.

## Latest Splice release

**0.9.3**

The highest version the Splice tags endpoint carries. A release existing is
not a network running it; what each network runs is below.

## Networks

Current is the last confirmed upgrade on the SV Operations Schedule whose date
has arrived; the schedule states what the operators intend, so a date that has
arrived is not proof the upgrade ran. SVs on it counts the Super Validator
nodes whose own roster entry reports that version. Minimum is the oldest
version a validator may run. Next and Due are the earliest upgrade still
ahead, confirmed or not. Reported is the version the network's own info
document states.

| Network | Current (scheduled) | SVs on it | Since | Minimum | Next | Due | Reported |
| --- | --- | --- | --- | --- | --- | --- | --- |
| DevNet | 0.9.2 | 2 / 14 | 2026-10-19 | 0.8 | 0.9.3 | 2026-10-21 | 0.9.3 |
| TestNet | 0.9.1 | 1 / 13 | 2026-10-19 | 0.8 | 0.9.3 | 2026-10-21 | 0.9.3 |
| MainNet | 0.8.4 | 1 / 13 | 2026-10-12 | 0.8 | 0.9.3 | 2026-10-21 | 0.9.3 |

## Super Validators

The hosts each Super Validator node publishes, as the network's own DSO
document states them. Scan is the node's public read endpoint. A participant
connects to a sequencer, and the sequencer changes at every synchronizer
serial: while an upgrade is in flight a node lists one per serial, highest
first. A serial below the one the network reports as current is marked
legacy, and one above it successor.

### DevNet

14 nodes, serial 5: 12 on 0.9.3, 2 on 0.9.2.

| Super Validator | Version | Scan | Sequencers |
| --- | --- | --- | --- |
| C7-Technology-Services-Limited | 0.9.3 | scan.sv-1.dev.global.canton.network.c7.digital | 6: sequencer-6.sv-1.dev.global.canton.network.c7.digital *(successor)*<br>5: sequencer-5.sv-1.dev.global.canton.network.c7.digital |
| Cumberland-1 | 0.9.3 | scan.sv-1.dev.global.canton.network.cumberland.io | 6: sequencer-6.sv-1.dev.global.canton.network.cumberland.io *(successor)*<br>5: sequencer-5.sv-1.dev.global.canton.network.cumberland.io |
| Cumberland-2 | 0.9.3 | scan.sv-2.dev.global.canton.network.cumberland.io | 6: sequencer-6.sv-2.dev.global.canton.network.cumberland.io *(successor)*<br>5: sequencer-5.sv-2.dev.global.canton.network.cumberland.io |
| DA-Helm-Test-Node | 0.9.3 | scan.sv.dev.global.canton.network.digitalasset.com | 6: sequencer-6.sv.dev.global.canton.network.digitalasset.com *(successor)*<br>5: sequencer-5.sv.dev.global.canton.network.digitalasset.com |
| Digital-Asset-1 | 0.9.3 | scan.sv-1.dev.global.canton.network.digitalasset.com | 6: sequencer-6.sv-1.dev.global.canton.network.digitalasset.com *(successor)*<br>5: sequencer-5.sv-1.dev.global.canton.network.digitalasset.com |
| Digital-Asset-2 | 0.9.3 | scan.sv-2.dev.global.canton.network.digitalasset.com | 6: sequencer-6.sv-2.dev.global.canton.network.digitalasset.com *(successor)*<br>5: sequencer-5.sv-2.dev.global.canton.network.digitalasset.com |
| Five-North-1 | 0.9.3 | scan.sv-1.dev.global.canton.network.fivenorth.io | 6: sequencer-6.sv-1.dev.global.canton.network.fivenorth.io *(successor)*<br>5: sequencer-5.sv-1.dev.global.canton.network.fivenorth.io |
| Global-Synchronizer-Foundation | 0.9.3 | scan.sv-1.dev.global.canton.network.sync.global | 6: sequencer-6.sv-1.dev.global.canton.network.sync.global *(successor)*<br>5: sequencer-5.sv-1.dev.global.canton.network.sync.global |
| Liberty-City-Ventures-1 | 0.9.3 | scan.sv-1.dev.global.canton.network.lcv.mpch.io | 6: sequencer-6.sv-1.dev.global.canton.network.lcv.mpch.io *(successor)*<br>5: sequencer-5.sv-1.dev.global.canton.network.lcv.mpch.io |
| MPC-Holding-Inc | 0.9.3 | scan.sv-1.dev.global.canton.network.mpch.io | 6: sequencer-6.sv-1.dev.global.canton.network.mpch.io *(successor)*<br>5: sequencer-5.sv-1.dev.global.canton.network.mpch.io |
| Orb-1-LP-1 | 0.9.2 | scan.sv-1.dev.global.canton.network.orb1lp.mpch.io | 6: sequencer-6.sv-1.dev.global.canton.network.orb1lp.mpch.io *(successor)*<br>5: sequencer-5.sv-1.dev.global.canton.network.orb1lp.mpch.io |
| Proof-Group-1 | 0.9.3 | scan.sv-1.dev.global.canton.network.proofgroup.xyz | 6: sequencer-6.sv-1.dev.global.canton.network.proofgroup.xyz *(successor)*<br>5: sequencer-5.sv-1.dev.global.canton.network.proofgroup.xyz |
| SV-Nodeops-Limited | 0.9.2 | scan.sv.dev.global.canton.network.sv-nodeops.com | 6: sequencer-6.sv.dev.global.canton.network.sv-nodeops.com *(successor)*<br>5: sequencer-5.sv.dev.global.canton.network.sv-nodeops.com |
| Tradeweb-Markets-1 | 0.9.3 | scan.sv-1.dev.global.canton.network.tradeweb.com | 6: sequencer-6.sv-1.dev.global.canton.network.tradeweb.com *(successor)*<br>5: sequencer-5.sv-1.dev.global.canton.network.tradeweb.com |

### TestNet

13 nodes, serial 3: 11 on 0.9.3, 1 on 0.9.1, 1 on 0.9.0.

| Super Validator | Version | Scan | Sequencers |
| --- | --- | --- | --- |
| C7-Technology-Services-Limited | 0.9.3 | scan.sv-1.test.global.canton.network.c7.digital | 3: sequencer-3.sv-1.test.global.canton.network.c7.digital<br>2: sequencer-2.sv-1.test.global.canton.network.c7.digital *(legacy)* |
| Cumberland-1 | 0.9.3 | scan.sv-1.test.global.canton.network.cumberland.io | 3: sequencer-3.sv-1.test.global.canton.network.cumberland.io<br>2: sequencer-2.sv-1.test.global.canton.network.cumberland.io *(legacy)* |
| Cumberland-2 | 0.9.3 | scan.sv-2.test.global.canton.network.cumberland.io | 3: sequencer-3.sv-2.test.global.canton.network.cumberland.io<br>2: sequencer-2.sv-2.test.global.canton.network.cumberland.io *(legacy)* |
| Digital-Asset-1 | 0.9.3 | scan.sv-1.test.global.canton.network.digitalasset.com | 3: sequencer-3.sv-1.test.global.canton.network.digitalasset.com<br>2: sequencer-2.sv-1.test.global.canton.network.digitalasset.com *(legacy)* |
| Digital-Asset-2 | 0.9.3 | scan.sv-2.test.global.canton.network.digitalasset.com | 3: sequencer-3.sv-2.test.global.canton.network.digitalasset.com<br>2: sequencer-2.sv-2.test.global.canton.network.digitalasset.com *(legacy)* |
| Five-North-1 | 0.9.3 | scan.sv-1.test.global.canton.network.fivenorth.io | 3: sequencer-3.sv-1.test.global.canton.network.fivenorth.io<br>2: sequencer-2.sv-1.test.global.canton.network.fivenorth.io *(legacy)* |
| Global-Synchronizer-Foundation | 0.9.3 | scan.sv-1.test.global.canton.network.sync.global | 3: sequencer-3.sv-1.test.global.canton.network.sync.global<br>2: sequencer-2.sv-1.test.global.canton.network.sync.global *(legacy)* |
| Liberty-City-Ventures-1 | 0.9.3 | scan.sv-1.test.global.canton.network.lcv.mpch.io | 3: sequencer-3.sv-1.test.global.canton.network.lcv.mpch.io<br>2: sequencer-2.sv-1.test.global.canton.network.lcv.mpch.io *(legacy)* |
| MPC-Holding-Inc | 0.9.3 | scan.sv-1.test.global.canton.network.mpch.io | 3: sequencer-3.sv-1.test.global.canton.network.mpch.io<br>2: sequencer-2.sv-1.test.global.canton.network.mpch.io *(legacy)* |
| Orb-1-LP-1 | 0.9.3 | scan.sv-1.test.global.canton.network.orb1lp.mpch.io | 3: sequencer-3.sv-1.test.global.canton.network.orb1lp.mpch.io<br>2: sequencer-2.sv-1.test.global.canton.network.orb1lp.mpch.io *(legacy)* |
| Proof-Group-1 | 0.9.3 | scan.sv-1.test.global.canton.network.proofgroup.xyz | 3: sequencer-3.sv-1.test.global.canton.network.proofgroup.xyz<br>2: sequencer-2.sv-1.test.global.canton.network.proofgroup.xyz *(legacy)* |
| SV-Nodeops-Limited | 0.9.1 | scan.sv.test.global.canton.network.sv-nodeops.com | 3: sequencer-3.sv.test.global.canton.network.sv-nodeops.com<br>2: sequencer-2.sv.test.global.canton.network.sv-nodeops.com *(legacy)* |
| Tradeweb-Markets-1 | 0.9.0 | scan.sv.test.global.canton.network.tradeweb.com | 3: sequencer-3.sv.test.global.canton.network.tradeweb.com<br>2: sequencer-2.sv.test.global.canton.network.tradeweb.com *(legacy)* |

### MainNet

13 nodes, serial 6: 11 on 0.9.3, 1 on 0.9.0, 1 on 0.8.4.

| Super Validator | Version | Scan | Sequencers |
| --- | --- | --- | --- |
| C7-Technology-Services-Limited | 0.9.3 | scan.sv-1.global.canton.network.c7.digital | 6: sequencer-6.sv-1.global.canton.network.c7.digital<br>5: sequencer-5.sv-1.global.canton.network.c7.digital *(legacy)* |
| Cumberland-1 | 0.9.3 | scan.sv-1.global.canton.network.cumberland.io | 6: sequencer-6.sv-1.global.canton.network.cumberland.io<br>5: sequencer-5.sv-1.global.canton.network.cumberland.io *(legacy)* |
| Cumberland-2 | 0.9.3 | scan.sv-2.global.canton.network.cumberland.io | 6: sequencer-6.sv-2.global.canton.network.cumberland.io<br>5: sequencer-5.sv-2.global.canton.network.cumberland.io *(legacy)* |
| Digital-Asset-1 | 0.9.3 | scan.sv-1.global.canton.network.digitalasset.com | 6: sequencer-6.sv-1.global.canton.network.digitalasset.com<br>5: sequencer-5.sv-1.global.canton.network.digitalasset.com *(legacy)* |
| Digital-Asset-2 | 0.9.3 | scan.sv-2.global.canton.network.digitalasset.com | 6: sequencer-6.sv-2.global.canton.network.digitalasset.com<br>5: sequencer-5.sv-2.global.canton.network.digitalasset.com *(legacy)* |
| Five-North-1 | 0.9.3 | scan.sv-1.global.canton.network.fivenorth.io | 6: sequencer-6.sv-1.global.canton.network.fivenorth.io<br>5: sequencer-5.sv-1.global.canton.network.fivenorth.io *(legacy)* |
| Global-Synchronizer-Foundation | 0.9.3 | scan.sv-1.global.canton.network.sync.global | 6: sequencer-6.sv-1.global.canton.network.sync.global<br>5: sequencer-5.sv-1.global.canton.network.sync.global *(legacy)* |
| Liberty-City-Ventures-1 | 0.9.3 | scan.sv-1.global.canton.network.lcv.mpch.io | 6: sequencer-6.sv-1.global.canton.network.lcv.mpch.io<br>5: sequencer-5.sv-1.global.canton.network.lcv.mpch.io *(legacy)* |
| MPC-Holding-Inc | 0.9.3 | scan.sv-1.global.canton.network.mpch.io | 6: sequencer-6.sv-1.global.canton.network.mpch.io<br>5: sequencer-5.sv-1.global.canton.network.mpch.io *(legacy)* |
| Orb-1-LP-1 | 0.9.3 | scan.sv-1.global.canton.network.orb1lp.mpch.io | 6: sequencer-6.sv-1.global.canton.network.orb1lp.mpch.io<br>5: sequencer-5.sv-1.global.canton.network.orb1lp.mpch.io *(legacy)* |
| Proof-Group-1 | 0.9.3 | scan.sv-1.global.canton.network.proofgroup.xyz | 6: sequencer-6.sv-1.global.canton.network.proofgroup.xyz<br>5: sequencer-5.sv-1.global.canton.network.proofgroup.xyz *(legacy)* |
| SV-Nodeops-Limited | 0.9.0 | scan.sv.global.canton.network.sv-nodeops.com | 6: sequencer-6.sv.global.canton.network.sv-nodeops.com<br>5: sequencer-5.sv.global.canton.network.sv-nodeops.com *(legacy)* |
| Tradeweb-Markets-1 | 0.8.4 | scan.sv-1.global.canton.network.tradeweb.com | 6: sequencer-6.sv-1.global.canton.network.tradeweb.com<br>5: sequencer-5.sv-1.global.canton.network.tradeweb.com *(legacy)* |

## Sources

| Source | Publisher | Authority | Polled every |
| --- | --- | --- | --- |
| [canton-foundation-configs](<https://github.com/canton-foundation/configs.git>) | Canton Foundation | OFFICIAL | 300 s |
| [canton-foundation-configs-runtime](<https://github.com/canton-foundation/configs-runtime.git>) | Canton Foundation | OFFICIAL | 300 s |
| [canton-foundation-cips](<https://github.com/canton-foundation/cips.git>) | Canton Foundation | GOVERNANCE | 3600 s |
| [canton-foundation-sv-operations-schedule](<https://sv-cal.canton.foundation/schedule.json>) | Canton Foundation | OFFICIAL | 300 s |
| [canton-foundation-binaries](<https://github.com/canton-foundation/binaries.git>) | Canton Foundation | OFFICIAL | 900 s |
| [splice-release-notes](<https://github.com/canton-network/splice/releases.atom>) | Splice project | OFFICIAL\_PROJECT | 900 s |
| [splice-tags](<https://api.github.com/repos/canton-network/splice/tags?per_page=100>) | Splice project | OFFICIAL\_PROJECT | 900 s |
| [cf-docs-splice-release-notes](<https://github.com/canton-network/cf-docs.git>) | Canton Network | OFFICIAL | 900 s |
| [sync-global-info-mainnet](<https://docs.global.canton.network.sync.global/info>) | Global Synchronizer Foundation | OFFICIAL | 300 s |
| [sync-global-sv-versions-mainnet](<https://docs.global.canton.network.sync.global/versions>) | Global Synchronizer Foundation | OFFICIAL | 300 s |
| [sync-global-dso-mainnet](<https://docs.global.canton.network.sync.global/dso>) | Global Synchronizer Foundation | OFFICIAL | 300 s |
| [sync-global-info-testnet](<https://docs.test.global.canton.network.sync.global/info>) | Global Synchronizer Foundation | OFFICIAL | 300 s |
| [sync-global-sv-versions-testnet](<https://docs.test.global.canton.network.sync.global/versions>) | Global Synchronizer Foundation | OFFICIAL | 300 s |
| [sync-global-dso-testnet](<https://docs.test.global.canton.network.sync.global/dso>) | Global Synchronizer Foundation | OFFICIAL | 300 s |
| [sync-global-info-devnet](<https://docs.dev.global.canton.network.sync.global/info>) | Global Synchronizer Foundation | OFFICIAL | 300 s |
| [sync-global-sv-versions-devnet](<https://docs.dev.global.canton.network.sync.global/versions>) | Global Synchronizer Foundation | OFFICIAL | 300 s |
| [sync-global-dso-devnet](<https://docs.dev.global.canton.network.sync.global/dso>) | Global Synchronizer Foundation | OFFICIAL | 300 s |

---

Values as of 2026-10-20T18:32:25Z.
A commit is made only when something shown here changes, so this is when a
value last moved, not when the feed last checked. The `heartbeat` branch says
the writer is alive.
