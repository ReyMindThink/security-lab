# Asset Inventory

Status: draft (Phase 1, step 1.3). Component level only. This file contains no findings.

## Ringkasan (Bahasa Indonesia)
- Daftar komponen dua backend target pada commit yang dikunci di scope-and-consent.md.
- Dibuat dari package.json, pencarian teks pada pendaftaran route, dan nama file. Isi file belum dibaca penuh. Jumlah endpoint adalah batas bawah.
- Dokumen ini tidak memuat temuan atau detail kerentanan.

## Method
Sources: package.json, a text search of route registrations
(router.get/post/put/patch/delete/use), file names in the source tree, and the
model declarations in the Prisma schema. File contents were not reviewed in full.
Endpoint counts are a lower bound: routes registered in other ways are not
counted. Roles, services and model names are taken from file names and route
guards and are not verified.

## PassGo backend (gadicandra/PassGo, branch staging, commit e2bfb20)

Stack: Node.js, Express 5, TypeScript, Mongoose 8, zod 4.

Relevant dependencies (name and range from package.json): jsonwebtoken ^9.0.2,
bcryptjs ^3.0.2, helmet ^8.1.0, cors ^2.8.6, cookie-parser ^1.4.7,
express-rate-limit ^8.1.0, multer ^2.0.2, file-type ^21.0.0, sharp ^0.34.3,
exceljs ^4.4.0, qrcode ^1.5.4, @supabase/supabase-js ^2.57.4,
midtrans-client ^1.4.3, nodemailer ^7.0.6, pino ^9.9.0.

Scripts: dev, build, start, test, typecheck, db:seed. No postinstall script.

### API surface
Prefix /api/v1. At least 58 registered endpoints (lower bound, see Method):

| Group | Count | Content |
|---|---|---|
| auth | 9 | register, login, refresh, logout, logout-all, email verification (request, confirm), password reset (request, confirm) |
| events | 26 | CRUD, publish, cancel, poster, staff, ticket types, check-ins, attendees and export, reports |
| me | 4 | profile, password, assigned events |
| orders | 7 | create, list, get, cancel, ticket email, payment sync, refund |
| payments | 1 | payment gateway notification endpoint |
| tickets | 4 | list, get, update, reissue |
| users | 4 | list, create, get, update |
| audit-logs | 1 | list |
| health | 2 | liveness, readiness |

Route groups registered in other ways, and static file serving, are not counted.

### Roles and middleware
Roles: ORGANIZER, ATTENDEE, and event staff access. Middleware: authenticate,
optionalAuthenticate, authorize, event access check, buyer-or-organizer check,
cookie guard, helmet, JSON body limit, request context, error handler.
Supporting services: idempotency, ETag/If-Match handling, audit logging, order
expiry.

### External integrations
Document database, payment gateway, object storage, email.

### Data models
Mongoose model files: auth, event, order, system, ticket (from file names).

## PatunganKu backend (ReyMindThink/PatunganKu, branch main, commit 0d7098b)

Stack: Node.js, Express 5, JavaScript, Prisma 7 with the MSSQL adapter, zod 4.

Relevant dependencies (name and range from package.json): @azure/storage-blob
^12.34.0, @prisma/adapter-mssql ^7.10.0, @prisma/client ^7.10.0, bcryptjs
^3.0.3, cors ^2.8.6, dotenv ^18.0.3, jsonwebtoken ^9.0.3, multer ^2.4.0,
zod ^4.6.5. Dev: nodemon, prisma.

Scripts: dev, start, test, postinstall (runs prisma generate).

### API surface
Prefix /api. At least 16 registered endpoints (lower bound, see Method):

| Group | Count | Content |
|---|---|---|
| auth | 3 | register, login, current user |
| groups | 4 | create, join, list, detail |
| transactions | 2 | create, list (under a group) |
| receipts | 2 | upload, verify (per transaction) |
| balances | 1 | group balances |
| payments | 3 | create, list, decide (under a group) |
| health | 1 | liveness |

### Middleware
Authentication guard (JWT), request validation (zod), file upload (multer),
CORS with origin from configuration, central error handler.

### External integrations
SQL Server database, object storage, AI API used for receipt verification.

### Data models
Prisma models (6): User, Group, GroupMember, Transaction, TransactionSplit,
PaymentConfirmation.