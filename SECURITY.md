# Request limits

Selected actions use an atomic D1 cooldown shared by browser tabs and Worker instances. The interval starts when a valid operation acquires its slot. A failed operation releases its own slot; an older failure cannot clear a newer slot. Limits are scoped to the authenticated account, except password recovery, which uses a hashed normalized address and the same response for existing and missing accounts.

| Action | Minimum interval | Scope |
| --- | --- | --- |
| Support, review and privacy requests | 60 seconds | Account |
| Account data export | 60 seconds | Account |
| Profile photo upload | 30 seconds | Account |
| Tutor publication/update | 30 seconds | Account and subject |
| Password recovery email | 60 seconds | Hashed address |

Existing hourly, authentication, grade-entry and IP ceilings remain in place. Authenticated POST and DELETE operations also share a 120-request/minute burst ceiling. The existing ten-minute grade-entry interval and its import-day exception are unchanged. Tutor withdrawal and photo deletion do not inherit publication/upload cooldowns. Logout bypasses the authentication-attempt budget while retaining origin validation and the general request gate.

429 responses include Retry-After and JSON retryAfter/retryAt metadata. The client shows remaining seconds and prevents repeated network requests for the same method/path until the wait expires (tutor publication is additionally scoped to its subject). Local waits are cleared after authentication changes and account deletion; a new enrolment clears an obsolete local grade-entry wait. Error responses and user data are not persisted in browser storage. Exports use the normal request/error flow and download JSON without leaving the app.

Validation uses the real API handlers and SQLite for exact expiry, account/action isolation, duplicate support requests, concurrent acquisition, failed writes/uploads, stale-lease cleanup, tutor withdrawal, uniform recovery responses and mail-delivery failures. Client checks cover Retry-After formats, expiry, method separation, account changes and study report keepalive. No external mail is sent by tests.

Tutor offers retain the database unique index on (user_id, subject). Publication upserts the authenticated owner’s existing row and retains its ID and original creation time. Client IDs/owner fields cannot redirect the update. The editor loads current own offer values and requires publication consent again; switching subjects loads that subject’s offer or a fresh draft.

First name and surname share a server-controlled nameChangedAt field and a 30-day interval. Username edits retain their existing separate 30-day interval. Unchanged locked values remain valid in a profile submission, and client-supplied timestamps are ignored. The requested username was checked against the live account/profile records and is occupied by another profile; no reassignment or pending new account override was added.
