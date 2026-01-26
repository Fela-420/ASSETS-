Authorization Matrix → IDOR / BOLA (Bug Bounty Mapping)
1️⃣ Authorization Matrix (Hacker Translation)
Matrix Concept	What It Means in Bug Bounty
Role	Logged-in user type (user, admin, seller, org member)
Service	API endpoint
URI parameter ({id})	Object ID (userId, orderId, messageId)
Allowed roles	Who should access the object
Test POV	“What happens if I try this as someone else?”

IDOR / BOLA happens when:
Endpoint access exists without verifying object ownership or relationship.

Example

Request	Result	Bug
DELETE /messages/1 (anonymous)	200 OK	Broken Access Control → IDOR (if 1 belongs to another user)
2️⃣ Bug Bounty Testing Workflow (Step-by-Step)
Step	Action	What to Verify	Bug If True
1	Access object as owner	200 OK, object belongs to you	Baseline
2	Change object ID only	Access to other user’s object	IDOR
3	Downgrade auth (no/low token)	Action still allowed	Vertical BAC
4	Swap HTTP method	Other methods bypass controls	Method bypass

Example

Method	Endpoint	Result
GET	/api/orders/123	403
DELETE	/api/orders/123	200 ❌
3️⃣ REST / API-Only Automation Logic
Component	Purpose
Multiple users	Cross-user object testing
Known object IDs	Ownership validation
Role tokens	Horizontal & vertical testing
Replay tooling	Automation & scale

Automation Logic

Loop	Test
Endpoint	All APIs
Token	All roles
Object ID	Owned vs not owned
Result	200 OK where 403 expected → IDOR

Burp Setup

Tool	Use
Repeater	Manual confirmation
Intruder	IDs + tokens
Logger++	Detect unexpected 200
4️⃣ Common Authorization Matrix Failures (Real Bug Bounty Wins)
#	Mistake	What Goes Wrong	Bug Type
1	Endpoint-only protection	No ownership check	BOLA
2	Role check only	No relationship validation	Horizontal IDOR
3	GET secured only	PUT/DELETE open	High-impact BAC
4	Frontend-only controls	API still works	BAC
5	New APIs not in matrix	Mobile/internal exposed	Fresh IDOR
6	Filtering ≠ authorization	User-controlled parameters	Param IDOR

Examples

Pattern	Issue
if user.role == "USER"	Missing object.user_id == user.id
/api/orders?user_id=me	Accepts /api/orders?user_id=1234
5️⃣ Bug Bounty Mental Checklist (Daily Use)
Question	Why It Matters
Can I change an ID?	Object-level control
Can I use another user’s token?	Horizontal IDOR
Can I remove the token?	Missing auth
Can I change HTTP method?	Method bypass
Can I hit mobile/internal APIs?	Shadow endpoints
Do responses differ (403 vs 200)?	Authorization failure
