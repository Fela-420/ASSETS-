# ASSETS-
1. Account Takeover (ATO)

What you’re looking to FIND (signals & surfaces)

A. Account-Related Surfaces

Login pages

Password reset pages

Email change flows

Phone number change flows

MFA / OTP setup pages

OAuth / “Login with” flows

Session management endpoints

B. Valuable Indicators

Password reset tokens (URLs, params, headers)

OTP / verification codes

Long-lived session tokens

Refresh tokens

Remember-me cookies

C. Structural Clues

Multiple authentication flows for the same account

Legacy login endpoints still live

Mobile and web auth using the same backend

Different error messages for different login states

Email or phone verification not consistently enforced

D. High-Value Findings

Ability to act as a user without full authentication

Account state changes without re-authentication

Sessions that survive password changes

Tokens that don’t appear user-bound

2. Broken Access Control / IDOR

What you’re looking to FIND

A. Identifier Patterns (Core IDOR Signals)

Numeric IDs (id=1, user_id=23)

UUIDs (uuid, guid)

Order numbers

Invoice numbers

File IDs

Message IDs

Object references in URLs, headers, or JSON bodies

B. Object-Driven Endpoints

/users/

/profiles/

/orders/

/documents/

/tickets/

/messages/

/files/

/transactions/

C. Role Boundaries

User vs admin vs support

Read vs write vs delete

Own objects vs shared objects vs global objects

D. High-Value Indicators

Same endpoint used by multiple roles

Client-supplied ownership fields

Object ownership not shown explicitly in UI

Backend trusting IDs provided by the client

APIs returning more fields than shown in UI

3. Business Logic Flaws

What you’re looking to FIND

A. Money & Value Systems

Checkout flows

Subscription upgrades/downgrades

Trials

Coupons / promo codes

Wallets / credits / balances

Refunds

Loyalty points

B. State-Based Workflows

Multi-step processes

Status-driven actions

“Pending → Approved → Completed” flows

Verification-dependent actions

C. Assumptions to Notice

Client controls prices, quantities, or plans

Client controls timing or order of steps

Same action callable multiple times

No visible server confirmation of state

D. High-Value Indicators

Ability to reach final states early

Reusable value tokens (coupons, credits)

State changes without corresponding checks

Backend trusting UI sequence

Price or plan values visible in requests

4. SSRF (Server-Side Request Forgery)

What you’re looking to FIND

A. URL-Accepting Features

Import from URL

Fetch image from URL

Webhooks

PDF generation from URL

Link preview generation

API integrations

Feed readers

B. Network Interaction Clues

Server fetches external resources

URLs stored server-side

Background jobs fetching data

Callbacks or webhooks

C. Input Locations

URL parameters

JSON fields

Headers

File metadata

Redirect URLs

D. High-Value Indicators

Backend accesses arbitrary URLs

Internal or cloud-related error messages

Response timing differences

Fetch behavior not mirrored client-side

5. Authentication Bypass

What you’re looking to FIND

A. Auth Boundaries

Endpoints that behave differently when logged in vs logged out

APIs called before login completes

Setup or onboarding endpoints

Password reset endpoints

Account verification endpoints

B. Trust Indicators

Headers controlling auth state

Cookies that indicate login

Tokens passed via URL or JSON

Flags like is_authenticated, verified, role

C. Structural Clues

Multiple auth methods for same account

Mobile and web auth differences

Legacy endpoints still functional

Partial auth states accepted

D. High-Value Findings

Sensitive actions without full authentication

Auth enforced only client-side

Backend trusts client auth flags

Endpoints missing auth checks entirely

6. Sensitive Data Exposure

What you’re looking to FIND

A. Data Types

Email addresses

Phone numbers

Full names

Addresses

API keys

Tokens

Internal IDs

Payment metadata

Logs

B. Exposure Locations

API responses

Error messages

Debug endpoints

Export/download features

Mobile APIs

Old or unused endpoints

C. Structural Clues

Over-verbose responses

Fields not used by UI

Hidden debug flags

Versioned APIs exposing more data

D. High-Value Indicators

Data belonging to other users

Data accessible without auth

Internal system details

Secrets embedded in responses
