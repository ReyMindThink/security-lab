# Test Environment

Status: PLAN (Phase 1, step 1.4). Nothing in this file is claimed to be running.
The "Verification" section stays empty until the environment is built and checked.

## Ringkasan (Bahasa Indonesia)
- Rancangan lingkungan uji lokal untuk dua backend target. Semua komponen baru dan terpisah dari layanan lain di komputer ini.
- Semua port hanya di 127.0.0.1. Tidak ada tunnel dan tidak ada lalu lintas ke layanan luar.
- Dokumen ini rencana. Bagian "Verification" diisi setelah lingkungan benar-benar dibangun dan diperiksa.

## Principles
- Every test component has its own name, port, network and volume. Existing
  containers, volumes, networks and database services on this machine are not
  used, reused or modified.
- Every published port is bound to 127.0.0.1.
- Test containers run on a dedicated Docker network created for the test.
- No tunnel and no setup that exposes the test instance to the internet.
- Automated scanners and manual tests target only the local addresses below.

## Planned components
| Component | Used by | Plan | Planned binding |
|---|---|---|---|
| Document database | PassGo | MongoDB container, single-node replica set if the code needs it | 127.0.0.1:27018 |
| SQL database | PatunganKu | SQL Server container, with a non-sa login created for the test | 127.0.0.1:11433 |
| Storage emulator | PatunganKu | Azurite container | 127.0.0.1:10010-10011 |
| Mail catcher | PassGo | Mailpit container | 127.0.0.1:8025 (web), 127.0.0.1:1025 (SMTP) |
| Payment gateway | PassGo | local mock, or disabled | none |
| Object storage | PassGo | the application local-disk storage mode | none |
| AI API | PatunganKu | local mock, or disabled | none |

## Credentials and data
- Database credentials for the test are generated for the test, kept in an
  ignored file under private/, and never pasted into chat or committed.
- No real third-party keys. The storage emulator uses its publicly documented
  development account, which is not a real credential.
- Synthetic data only. Nothing is copied from the teams databases or backups.

## Open decisions
- Where the application process runs: on the host, or in a container on the test network.
- Whether PassGo needs a replica set (confirm by reading the code).
- Image versions are pinned when the environment is built.

## Teardown
Test containers, the test network and the test volumes are removed by name,
without touching anything else on the machine.

## Verification
Not yet built.