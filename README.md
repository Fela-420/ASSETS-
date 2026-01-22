1. Account Takeover (ATO) — What to Find
Account-Related Surfaces
 | Category        | What to Look For                              |
| --------------- | --------------------------------------------- |
| Login           | Login pages, alternate login endpoints        |
| Recovery        | Password reset pages                          |
| Profile Changes | Email change flows, phone number change flows |
| MFA             | MFA / OTP setup pages                         |
| Federation      | OAuth / “Login with” flows                    |
| Sessions        | Session management endpoints                  |

B. Valuable Indicators  

| Indicator Type  | Examples                                      |
| --------------- | --------------------------------------------- |
| Reset Artifacts | Password reset tokens (URLs, params, headers) |
| Verification    | OTP / verification codes                      |
| Sessions        | Long-lived session tokens                     |
| Tokens          | Refresh tokens                                |
| Persistence     | Remember-me cookies                           |

C. Structural Clues

| Area         | Signals                                             |
| ------------ | --------------------------------------------------- |
| Auth Design  | Multiple authentication flows for same account      |
| Legacy       | Old login endpoints still reachable                 |
| Platform     | Mobile and web using same auth backend              |
| Errors       | Different error messages for different login states |
| Verification | Email or phone verification inconsistently enforced |

D. High-Value Findings
| Observation         | Meaning                                              |
| ------------------- | ---------------------------------------------------- |
| Partial Access      | Ability to act as a user without full authentication |
| Weak Re-Auth        | Account state changes without re-authentication      |
| Session Persistence | Sessions survive password changes                    |
| Token Scope         | Tokens not clearly bound to user identity            |

2. Broken Access Control / IDOR — What to Find

A. Identifier Patterns (Core Signals)
| Identifier Type | Examples                                        |
| --------------- | ----------------------------------------------- |
| Numeric         | `id=1`, `user_id=23`                            |
| UUID            | `uuid`, `guid`                                  |
| Commerce        | Order numbers, invoice numbers                  |
| Files           | File IDs                                        |
| Messaging       | Message IDs                                     |
| Transport       | Object references in URLs, headers, JSON bodies |


B. Object-Driven Endpoints
| Object Type | Endpoint Patterns            |
| ----------- | ---------------------------- |
| Users       | `/users/`, `/profiles/`      |
| Commerce    | `/orders/`, `/transactions/` |
| Documents   | `/documents/`, `/files/`     |
| Support     | `/tickets/`, `/messages/`    |

C. Role Boundaries
| Boundary Type | Examples                        |
| ------------- | ------------------------------- |
| Role          | User vs admin vs support        |
| Action        | Read vs write vs delete         |
| Ownership     | Own objects vs shared vs global |

D. High-Value Indicators
| Indicator        | Why It Matters                           |
| ---------------- | ---------------------------------------- |
| Role Reuse       | Same endpoint used by multiple roles     |
| Ownership Fields | Client-supplied ownership attributes     |
| UI Mismatch      | Ownership not visible in UI              |
| Trust            | Backend trusts client-provided IDs       |
| Overexposure     | APIs return more fields than UI displays |

3. Business Logic Flaws — What to Find

A. Money & Value Systems
| System        | Examples                     |
| ------------- | ---------------------------- |
| Payments      | Checkout flows               |
| Subscriptions | Upgrades / downgrades        |
| Promotions    | Trials, coupons, promo codes |
| Credits       | Wallets, balances            |
| Post-Payment  | Refunds                      |
| Incentives    | Loyalty points               |

B. State-Based Workflows
| Workflow Type | Examples                           |
| ------------- | ---------------------------------- |
| Multi-Step    | Sequential processes               |
| Status        | Pending → Approved → Completed     |
| Verification  | Actions tied to verification state |

C. Assumptions to Notice
| Assumption Area | Signal                               |
| --------------- | ------------------------------------ |
| Pricing         | Client controls prices or quantities |
| Flow            | Client controls step order           |
| Reuse           | Same action callable repeatedly      |
| Validation      | No visible server confirmation       |

D. High-Value Indicators
| Indicator        | Meaning                            |
| ---------------- | ---------------------------------- |
| Early Completion | Final states reachable prematurely |
| Reusability      | Coupons / credits reusable         |
| Weak Validation  | State changes without checks       |
| UI Trust         | Backend trusts UI flow             |
| Visibility       | Prices / plans visible in requests |

4. SSRF — What to Find

A. URL-Accepting Features
| Feature      | Examples                |
| ------------ | ----------------------- |
| Imports      | Import from URL         |
| Media        | Fetch image from URL    |
| Automation   | Webhooks                |
| Documents    | PDF generation from URL |
| Metadata     | Link preview generation |
| Integrations | API integrations        |
| Feeds        | Feed readers            |

B. Network Interaction Clues
| Clue      | Meaning                           |
| --------- | --------------------------------- |
| Fetching  | Server fetches external resources |
| Storage   | URLs stored server-side           |
| Jobs      | Background fetch processes        |
| Callbacks | Webhook callbacks                 |

C. Input Locations
| Location   | Examples       |
| ---------- | -------------- |
| Params     | URL parameters |
| Payload    | JSON fields    |
| Headers    | Custom headers |
| Files      | File metadata  |
| Navigation | Redirect URLs  |

D. High-Value Indicators
| Indicator       | Why Important                            |
| --------------- | ---------------------------------------- |
| Arbitrary Fetch | Backend accesses arbitrary URLs          |
| Errors          | Internal or cloud-related error messages |
| Timing          | Response timing differences              |
| Behavior        | Fetch behavior differs from client       |

5. Authentication Bypass — What to Find

A. Auth Boundaries
| Boundary      | Examples                            |
| ------------- | ----------------------------------- |
| Session State | Different behavior logged in vs out |
| Timing        | APIs called before login completes  |
| Onboarding    | Setup or onboarding endpoints       |
| Recovery      | Password reset endpoints            |
| Verification  | Account verification endpoints      |


B. Trust Indicators

| Indicator | Examples                               |
| --------- | -------------------------------------- |
| Headers   | Headers controlling auth               |
| Cookies   | Login state cookies                    |
| Tokens    | Tokens in URL or JSON                  |
| Flags     | `is_authenticated`, `verified`, `role` |

C. Structural Clues
| Clue       | Meaning                           |
| ---------- | --------------------------------- |
| Redundancy | Multiple auth methods per account |
| Platform   | Mobile vs web differences         |
| Legacy     | Old endpoints still active        |
| State      | Partial auth states accepted      |

D. High-Value Findings
| Finding             | Impact                              |
| ------------------- | ----------------------------------- |
| Missing Enforcement | Sensitive actions without full auth |
| Client-Side Only    | Auth enforced only in UI            |
| Trust               | Backend trusts client auth flags    |
| Gaps                | Endpoints missing auth entirely     |

6. Sensitive Data Exposure — What to Find

A. Data Types
| Data      | Examples                |
| --------- | ----------------------- |
| Identity  | Email, phone, full name |
| Location  | Addresses               |
| Secrets   | API keys, tokens        |
| Internals | Internal IDs            |
| Payments  | Payment metadata        |
| System    | Logs                    |

B. Exposure Locations
| Location | Examples                   |
| -------- | -------------------------- |
| APIs     | API responses              |
| Errors   | Error messages             |
| Debug    | Debug endpoints            |
| Files    | Export / download features |
| Mobile   | Mobile APIs                |
| Legacy   | Old or unused endpoints    |

C. Structural Clues
| Clue          | Meaning                     |
| ------------- | --------------------------- |
| Verbosity     | Over-verbose responses      |
| Unused Fields | Fields not used by UI       |
| Flags         | Hidden debug flags          |
| Versions      | Older APIs expose more data |

 D. High-Value Indicators
 | Indicator  | Severity                      |
| ---------- | ----------------------------- |
| Cross-User | Data of other users           |
| No Auth    | Data without authentication   |
| Internal   | System details exposed        |
| Secrets    | Secrets embedded in responses |


