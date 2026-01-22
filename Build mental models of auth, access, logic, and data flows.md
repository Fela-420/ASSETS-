1 MINDSET 
| Day | Focus                                     | Resources & Activities                                                                                                                                                             |
| --- | ----------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | **Account Takeover (ATO) basics**         | Read: [OWASP Authentication Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Authentication_Cheat_Sheet.html) <br> Reflect on how login, MFA, password reset flows work |
| 2   | **Broken Access Control / IDOR concepts** | Read: [OWASP Access Control Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Access_Control_Cheat_Sheet.html) <br> Study example IDOR reports on HackerOne              |
| 3   | **Business Logic Flaws overview**         | Read: [PortSwigger Blog: Business Logic Flaws](https://portswigger.net/web-security/business-logic) <br> Analyze sample bugs from Bugcrowd reports                                 |
| 4   | **SSRF fundamentals**                     | Read: [OWASP SSRF Guide](https://owasp.org/www-community/attacks/Server_Side_Request_Forgery) <br> Watch OWASP YouTube intro videos                                                |
| 5   | **Authentication Bypass basics**          | Read: [OWASP Authentication Bypass](https://owasp.org/www-community/vulnerabilities/Authentication_bypass) <br> Review example bypasses from public bug bounty write-ups           |
| 6   | **Sensitive Data Exposure understanding** | Read: [OWASP Sensitive Data Exposure](https://owasp.org/www-project-top-ten/2017/A3_2017-Sensitive_Data_Exposure) <br> Practice spotting data leaks in test APIs                   |
| 7   | **Review & Reflection**                   | Write summary notes of what you learned. <br> Identify any unclear topics to revisit later.                                                                                        |


Deep Dive into Recon & Mapping
| Day | Focus                                 | Resources & Activities                                                                                                                                                                       |
| --- | ------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 8   | **Account takeover recon deep dive**  | Read: [Account Takeover Hunting Guide (Medium)](https://medium.com/@nyatla/account-takeover-ato-hunting-guide-1a0b9b3b479a) <br> Practice mapping auth flows on demo apps (DVWA, Juice Shop) |
| 9   | **IDOR & access control mapping**     | Read: [PortSwigger: IDOR Fundamentals](https://portswigger.net/web-security/access-control/idor) <br> Study multiple real bounty reports highlighting object IDs and role boundaries         |
| 10  | **Business logic mapping techniques** | Read: [PortSwigger Logic Flaws](https://portswigger.net/web-security/business-logic) <br> Sketch workflows of checkout, subscriptions, or refunds from sample sites                          |
| 11  | **SSRF discovery signals**            | Read: [SSRF Detection Techniques](https://portswigger.net/web-security/ssrf) <br> Practice finding URL-accepting parameters on test apps                                                     |
| 12  | **Authentication bypass indicators**  | Study public bug reports highlighting bypasses <br> Map out auth states on demo apps                                                                                                         |
| 13  | **Sensitive data exposure vectors**   | Practice analyzing API responses from demo APIs <br> Explore tools like Postman or Burp to view data returned                                                                                |
| 14  | **Review recon & mapping notes**      | Summarize what you can identify in apps for each vuln type                                                                                                                                   |

Hands-on Practice & Reporting

| Day | Focus                               | Resources & Activities                                                                                             |
| --- | ----------------------------------- | ------------------------------------------------------------------------------------------------------------------ |
| 15  | **Practice ATO on labs**            | Hack [OWASP Juice Shop](https://owasp.org/www-project-juice-shop/) <br> Try to find auth weaknesses, reset flows   |
| 16  | **IDOR & access control labs**      | Use [DVWA](http://www.dvwa.co.uk/) or [bWAPP](http://www.itsecgames.com/) <br> Find IDOR and access control bugs   |
| 17  | **Business logic labs**             | Try logic flaws on Juice Shop <br> Manipulate order flows or discounts                                             |
| 18  | **SSRF practical labs**             | Use [PortSwigger SSRF Labs](https://portswigger.net/web-security/ssrf/lab-basic-ssrf) <br> Practice injecting URLs |
| 19  | **Auth bypass practice**            | Look for bypasses on labs or CTFs <br> Test session management, token flaws                                        |
| 20  | **Sensitive data exposure testing** | Capture API responses <br> Look for unintended data leaks                                                          |
| 21  | **Report writing practice**         | Pick a previous day’s bug or lab finding <br> Draft a professional, clear bug report                               |
