Correct Mental Model

Think in layers:

1 Surface recon
→ subdomains, apps, APIs

2 Flow recon
→ login, reset, checkout, uploads, webhooks

3 Object recon
→ users, orders, files, messages

4 State recon
→ pending, verified, paid, approved

5 Trust recon
→ what the server assumes is true 


Layer One — Surface & Entry Recon

A. Application Surfaces (Where the product exists)
| Surface Type | What to Identify                   |
| ------------ | ---------------------------------- |
| Primary      | Main production website            |
| Secondary    | Alternate domains                  |
| Subdomains   | Functional subdomains (not random) |
| Mobile       | Mobile-specific endpoints          |
| Desktop      | Desktop client backends            |
| APIs         | Public, private, versioned APIs    |

B. Auth & Identity Surfaces
| Surface      | Indicators                           |
| ------------ | ------------------------------------ |
| Login        | Separate login domains               |
| Accounts     | Account management areas             |
| Identity     | SSO / OAuth entry points             |
| Recovery     | Password reset portals               |
| Verification | Email / phone verification endpoints |

C. Environment Variants
| Environment | What to Notice                       |
| ----------- | ------------------------------------ |
| Production  | Live user-facing environment         |
| Staging     | Feature-complete but less restricted |
| Beta        | Experimental flows                   |
| Legacy      | Older UI / API still reachable       |
| Internal    | Employee or admin-facing surfaces    |

D. Functional Surfaces (Logic-Creating Areas)
| Function      | Examples                         |
| ------------- | -------------------------------- |
| Commerce      | Checkout, billing, subscriptions |
| Content       | Uploads, downloads, media        |
| Communication | Messaging, tickets, comments     |
| Automation    | Webhooks, integrations           |
| Data          | Import/export features           |

E. API Characteristics
| Aspect     | What to Identify          |
| ---------- | ------------------------- |
| Versions   | v1, v2, beta              |
| Clients    | Web vs mobile vs partner  |
| Auth Model | Token-based, cookie-based |
| Format     | REST, GraphQL             |
| Exposure   | Public vs restricted      |

F. Role Surfaces
| Role    | What to Look For                    |
| ------- | ----------------------------------- |
| User    | Standard user features              |
| Admin   | Admin dashboards                    |
| Support | Support tooling                     |
| Partner | Partner portals                     |
| Mixed   | Same surface serving multiple roles |

G. High-Value Layer-One Indicators
| Indicator       | Why It Matters                          |
| --------------- | --------------------------------------- |
| Duplicate Logic | Same feature implemented multiple times |
| Hidden Entry    | Functionality not linked in UI          |
| Role Mixing     | One surface handling many roles         |
| Legacy Paths    | Old flows still active                  |
| API Reuse       | One API serving many clients            |
 
