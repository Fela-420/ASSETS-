COMPLETE API CAPTURE CHECKLIST (POSTMAN PROXY)
1. Authentication & Session

Do all of these:

Login (valid credentials)

Login (invalid password)

Login (invalid username)

Login with empty fields

Logout

Session timeout (stay idle, then act)

Use expired token

Use revoked token

Refresh token

Multiple logins from different tabs

📌 Captures:

Auth APIs

Token handling

Error responses

2. User Account Flows

For each user role:

View profile

Edit profile

Upload profile picture

Change password

Change email

Enable / disable settings

Delete account (if allowed)

Try:

Empty fields

Max length input

Invalid format (email, phone)

Special characters

3. Navigation (Every Page)

Open every page and sub-page:

Dashboard

Settings

Reports

History / Logs

Notifications

Help / Support

Hidden menus (hamburger / dropdowns)

Open pages:

Directly via URL

After logout (should fail)

4. Buttons & Actions

Click every button, including:

Save

Update

Cancel

Reset

Enable / Disable

Export / Download

Upload

Retry / Refresh

Click buttons:

Twice quickly

With no data

With invalid data

5. Forms (Very Important)

For every form:

Submit valid data

Submit empty form

Submit partial data

Submit max values

Submit invalid types

Submit duplicate data

Example tests:

Long strings

Negative numbers

Zero values

Special characters (' " < >)

6. Error Generation (Critical for Hidden APIs)

Force errors intentionally:

Invalid IDs in URL

Access page without permission

Modify URL parameters

Expired session

Remove required headers

Remove auth token

Change HTTP method (GET → POST)

📌 Error handling APIs often expose hidden logic.

7. Role-Based Testing (Must Do)

Repeat everything above for:

Normal user

Admin

Support / Manager (if exists)

Read-only user

Also test:

Admin APIs with user token

User APIs with admin token

8. Search, Filter & Pagination

For all lists:

Search valid keyword

Search invalid keyword

Empty search

Large page size

Page = 0, -1, very large number

Sort ascending / descending

These often call separate APIs.

9. File Handling

If supported:

Upload valid file

Upload invalid file type

Upload large file

Upload empty file

Download file

Cancel upload midway

10. Notifications & Background Calls

Trigger:

Notifications

Emails

Alerts

WebSocket reconnects

Auto refresh (leave page open)

Hidden APIs appear here.

11. URL & Parameter Tampering

Manually modify:

IDs

User IDs

Order IDs

Role flags

Boolean values

Observe responses.

12. Mobile / Responsive Mode (If Applicable)

Switch browser to mobile view

Use site again

Some APIs differ for mobile
