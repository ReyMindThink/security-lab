# Security Policy and Ethical Scope

## Purpose
This repository documents a personal learning lab in application security,
detection engineering, and IoT security. It contains write-ups, scripts,
configurations, and detection rules written by the repository owner.

## Authorized scope
- Only systems that I own, or for which I hold written permission from the
  owner, are tested.
- Code owned by teammates is tested only after written consent from its
  owners, and only in local or staging environments, never in production.
- Cloud provider penetration-testing policies are read before any scan of
  cloud-hosted resources.
- No scanning, reconnaissance, or exploitation of third-party systems.
  Bug bounty work is outside the scope of this repository.

## Data handling
- Secrets, tokens, keys, connection strings, and .env files are never
  committed. Anything exposed by mistake is treated as leaked and rotated.
- Honeypot data is sanitized before publication: IP addresses are masked or
  aggregated and URLs are defanged (for example hxxps://contoh[.]com).
- Malware samples are never committed. Only hashes and metadata are kept, and
  samples are handled only inside an isolated sandbox.
- Firmware dumps that contain keys are never committed.

## Vulnerability disclosure
- Findings in teammates' code are reported to the code owners first and are
  published only after they are fixed. Unfixed vulnerabilities are not
  published.
- If you find a problem in this repository itself (for example an exposed
  secret), please use GitHub private vulnerability reporting (the "Report a
  vulnerability" option on the Security tab) instead of a public issue.

## Disclaimer
This material is for education only and comes with no warranty (see LICENSE).
Nothing here authorizes anyone to attack a system. Unauthorized access may be
illegal, including under UU ITE in Indonesia.

---

# Kebijakan Keamanan dan Ruang Lingkup Etika

## Tujuan
Repositori ini mendokumentasikan lab belajar pribadi di bidang keamanan
aplikasi, detection engineering, dan keamanan IoT.

## Ruang lingkup yang diizinkan
- Hanya sistem milik sendiri, atau yang pemiliknya memberi izin tertulis,
  yang diuji.
- Kode milik rekan tim diuji hanya setelah ada persetujuan tertulis dari
  pemiliknya, dan hanya di lingkungan lokal atau staging, bukan produksi.
- Kebijakan penetration testing penyedia cloud dibaca sebelum memindai
  sumber daya di cloud.
- Tidak ada pemindaian, recon, atau eksploitasi sistem pihak ketiga. Bug
  bounty di luar ruang lingkup repositori ini.

## Penanganan data
- Secret, token, kunci, connection string, dan file .env tidak pernah
  di-commit. Yang terlanjur terpapar dianggap bocor dan dirotasi.
- Data honeypot disanitasi sebelum dipublikasikan: IP dimasking atau
  diagregasi, URL ditulis defanged.
- Sampel malware tidak pernah di-commit. Hanya hash dan metadata yang
  disimpan, dan sampel hanya ditangani di sandbox terisolasi.
- Dump firmware yang berisi kunci tidak pernah di-commit.

## Pengungkapan kerentanan
- Temuan pada kode rekan tim dilaporkan ke pemiliknya dulu dan baru
  dipublikasikan setelah diperbaiki. Kerentanan yang belum diperbaiki tidak
  dipublikasikan.
- Jika menemukan masalah pada repositori ini (misalnya secret yang terpapar),
  gunakan fitur private vulnerability reporting GitHub, bukan issue publik.

## Penafian
Materi ini untuk pendidikan dan tanpa jaminan (lihat LICENSE). Tidak ada
bagian di sini yang memberi izin menyerang sistem mana pun. Akses tanpa izin
dapat melanggar hukum, termasuk UU ITE di Indonesia.