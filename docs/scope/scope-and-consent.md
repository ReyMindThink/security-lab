# Scope and Consent

Status: active since 2026-10-24. It applies to everything in this repository.

## Ringkasan (Bahasa Indonesia)
- Target: backend PassGo (branch staging, commit e2bfb20) dan PatunganKu (branch main, commit 0d7098b), hanya di komputer lokal.
- Tidak menyentuh instance yang sudah dideploy, layanan pihak ketiga, atau kredensial yang ditemukan.
- Izin tertulis dari semua anggota kedua tim (23 Oktober 2026), mencakup pengujian dan publikasi temuan setelah diperbaiki.
- Temuan dilaporkan ke pemilik kode lebih dulu dan baru dipublikasikan setelah diperbaiki.
- Kontribusi penulis pada kedua proyek diungkap secara jujur di bagian "Own contribution".

## Targets
| Target | Repository | Branch | Pinned commit | Environment |
|---|---|---|---|---|
| PassGo backend | gadicandra/PassGo | staging | e2bfb20 | local only |
| PatunganKu backend | ReyMindThink/PatunganKu | main | 0d7098b | local only |

Tests run against read-only clones that are kept outside version control. Every
finding states the commit it applies to. If a target moves, the commit is
re-pinned and the change is recorded here.

## In scope
- Reading and analysing the code: static analysis, dependency, secret and
  configuration review.
- Dynamic and manual testing of a locally running copy of each backend, using
  local databases and local mock services created for the test.
- Writing and testing fixes as pull requests, only after the code owners agree.

## Out of scope (never contacted)
- Any deployed or hosted instance of either application, including addresses
  found in the repositories.
- Any third-party or cloud service used by the applications: cloud databases,
  payment gateways (including sandboxes), object storage, AI APIs, email services.
- Credentials found in repositories or documentation. They are not tried anywhere.
- Other people's systems, accounts, and networks.
- Tunnels or any setup that exposes a local test instance to the internet.

## Rules for the test environment
- Local database containers created for testing only. No connection strings or
  .env files from the teams' working copies are copied into the clones.
- External integrations are replaced by local mocks or left disabled.
- No API keys of any kind in the test environment.
- Automated scanners run only against the local instance, never against a hostname.

## Consent
Written consent was given in each team's group chat on 2026-10-23 by all members
of both teams. It covers (1) testing as described above and (2) publishing
findings after they are fixed. The evidence is kept privately outside this
repository. SHA-256 of the evidence file:
5E06A101AD9E3215ADEA461FAA4DC39DF7E1FE24E147A2CA5E71CEBDFE466B14
Teammates are referred to by GitHub username only.

## Handling of findings
- Findings in code owned by others are reported privately to the code owners first.
- They are published here only after the owners confirm a fix, and never include
  secrets or details that would work against a deployed instance.
- Unfixed findings stay in a private, untracked folder.

## Own contribution
Counted by non-merge commits at the pinned commits: in PassGo, 5 of 65 are by the
repository author (about 8%); in PatunganKu, at least 51 of 58 (about 88%).
Commit counts are not a measure of code share. PatunganKu is therefore closer to
a self-review, and PassGo is closer to a review of other people's work.

## Changes to someone else's code
Every change to code owned by the teams is flagged to its author first, made on
a branch of a clone or fork, and offered as a pull request. Nothing is pushed to
a team repository directly.