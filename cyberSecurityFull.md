# Cyber Security

## OWASP Top 10

- The OWASP Top 10 is a short list of the ways web applications usually fail. It is a checklist, not a certification.
- Broken access control: the UI hides a button and the API does not check the role.
- Injection: user text is stitched into a query, a command, or a page.
- Cryptographic failures: passwords stored raw, or TLS skipped.
- Identification failures: weak login, no rate limit, tokens that live forever.
- I use the list as a review of one route: who may call it, what is concatenated, what is logged, what is limited.
- OWASP is a fire inspection list. You walk the building with it. You do not frame it and call the building safe.
- careful: Reciting ten names and being unable to point at a route.
- Which item have you actually closed?
- Access control on the API, not only in React. Password hashing with bcrypt. Short JWTs and refresh rotation. Rate limits. Validation at the edge. I name the ones in the code, not the whole poster.

```
for each route: auth, role, validation, query style, log redaction, rate limit
```

- homework
```
for each route: auth, role, validation, query style, log redaction, rate limit
```

## SQL injection

- SQL injection happens when a program builds a query by gluing user text into the SQL string, so the text can change the meaning of the query.
- The impact is reading or changing rows the person should not touch.
- The fix is to send the SQL and the values separately. The database binds the value as data.
- Prisma and a parameterised query do this. A template string of SQL you concatenate does not.
- A database user with only the rights it needs limits the damage of any remaining bug.
- The query is a sentence with a blank. The user may fill the blank. They may not be handed the pen that writes the rest of the sentence.
- careful: Trusting that a front-end check made the text safe.
- Is Prisma enough?
- The normal client methods are parameterised. The hole is a raw query you build with string concatenation. I do not concatenate. I use the tagged form or the query builder.

```typescript
await db.$queryRaw`SELECT * FROM users WHERE email = ${email}`;
-- the value is bound. It is not pasted into the sentence.
```

- homework
```typescript
await db.$queryRaw`SELECT * FROM users WHERE email = ${email}`;
-- the value is bound. It is not pasted into the sentence.
```

## XSS

- Cross-site scripting is when someone else's text runs as script in a user's browser.
- The impact is the attacker acting as the user in that browser: reading the page, and calling your API as them.
- React escapes text in JSX. The dangerous path is rendering HTML on purpose.
- Do not use dangerouslySetInnerHTML for a comment, a vessel name, or a chat line.
- A content security policy is a second net: the browser refuses script that did not come from a place you named.
- XSS is letting a stranger write on the classroom board in the teacher's handwriting.
- careful: A rich-text feature with no sanitiser, or a 'temporary' escape hatch that stays.
- Where does XSS meet your tokens?
- If a script runs on our origin, it can call our API with the user's session. A token in localStorage is also readable by that script. Escaping untrusted text is the first control. A strict content security policy is the next.

```tsx
<p>{comment}</p>
// text is escaped
// do not inject raw HTML for user content
```

- homework
```tsx
<p>{comment}</p>
// text is escaped
// do not inject raw HTML for user content
```

## CSRF

- Cross-site request forgery is another site causing the browser to send a request that already has your cookie.
- Cookies are attached by the browser. A hostile page can submit a form to your origin if the cookie is sent.
- SameSite=Lax or Strict stops many of those sends.
- A CSRF token is a second value the hostile page cannot read, checked on the server.
- A JWT you set in an Authorization header is not attached automatically, so a plain form post does not carry it. That is why this bug shows up when you move the session into a cookie.
- CSRF is someone else filling in a form on your behalf because the browser kindly attaches your membership card.
- careful: Switching to cookies and keeping the rest of the design unchanged.
- Do we have CSRF today?
- If the access token is a header the JavaScript must set, a foreign form does not have it. If we move to a cookie session, I add SameSite and a CSRF token in the same change. I do not do the cookie first and the token later.

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
```

- homework
```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
```

## CORS

- CORS is the browser's rule about which other origins may read a response from your API.
- The browser sends Origin. Your API answers with the origins it allows.
- CORS is not access control. A non-browser client ignores it.
- Reflecting whatever Origin the request sent, with credentials, lets any website call your API as the user.
- Allow the web origin and the local development origin. Do not allow a star together with credentials.
- CORS is a guest list for browsers. It is not the lock on the door. Tools that are not browsers do not look at the list.
- careful: Allowing every origin because the Expo app or a local tool failed once.
- I set CORS to star. Am I safe?
- You have not opened the database. You have told every website it may read responses, and you must not combine that with credentialed cookies. Authorisation is still the guard.

```http
Access-Control-Allow-Origin: https://vms.arrobin.com
Access-Control-Allow-Credentials: true
```

- homework
```http
Access-Control-Allow-Origin: https://vms.arrobin.com
Access-Control-Allow-Credentials: true
```

## SSRF

- Server-side request forgery is when the server fetches a URL that the user supplied, and the user points that fetch at a place the server can see and the user cannot.
- The impact is the server being used as a confused client, toward internal addresses or cloud management addresses.
- The fix is an allowlist of hosts and schemes, and a refusal of private and link-local addresses.
- A webhook test button, an image import, or a 'fetch this video URL' feature is the usual shape.
- Resolve the name and check the address before the request, and do not follow a redirect onto a private address.
- SSRF is sending the intern to an address the visitor wrote down. The intern can enter rooms the visitor cannot. So you only accept addresses on a list.
- careful: A feature that fetches any URL the client posts, described as a convenience.
- Where could this appear in our apps?
- An import-by-URL for a video or a team logo. The safe version uploads the bytes, or fetches only from a host we chose. I do not give the server a blank URL.

```
allow only https
allow only hosts you named
refuse addresses that are internal to the network
```

- homework
```
allow only https
allow only hosts you named
refuse addresses that are internal to the network
```

## HTTPS and TLS

- HTTPS is HTTP inside TLS. TLS protects the bytes on the path and checks the server name.
- A certificate must match the domain and be inside its dates, and the chain must reach a root the client trusts.
- Redirect HTTP to HTTPS. Set the header that tells browsers to stay on HTTPS.
- TLS does not make a weak password strong, and it does not fix a missing role check.
- Inside the machine, nginx may talk to Node over plain HTTP on localhost. The public hop is the one that must be TLS.
- TLS is a sealed envelope addressed to a name you checked. The letter can still be foolish.
- careful: A certificate you never renew, so the site breaks on a Saturday.
- Is HTTP between nginx and Node a problem?
- On localhost, the bytes do not cross a network an attacker is on. The public connection is TLS. I would not send that internal hop across a cloud network in the clear.

```nginx
listen 443 ssl;
return 301 https://$host$request_uri;  # on port 80
```

- homework
```nginx
listen 443 ssl;
return 301 https://$host$request_uri;  # on port 80
```

## Hashing and encryption

- A hash is one way. Encryption is reversible if you have the key. They are not interchangeable.
- Hash a password. You never need the original back. You compare hashes.
- Encrypt a TOTP secret or a stored token if you must read it later, and keep the key outside the database.
- TLS encrypts the path. It is not the same as encrypting a column.
- A fast hash such as SHA-256 is right for a file checksum and wrong for a password, because people can guess quickly.
- A hash is a fingerprint. Encryption is a locked box you can unlock. You do not unlock a fingerprint, and you do not fingerprint a box you need to open.
- careful: SHA-256 of the password and calling it done.
- Why not encrypt passwords so we can email them back?
- Because then anyone who reads the key reads every password. We store a slow hash. We send a reset link. We never send the old password.

```
password -> bcrypt (one way)
totp secret -> encrypt, because you must read it to check a code
file -> sha256 if you only need to detect a change
```

- homework
```
password -> bcrypt (one way)
totp secret -> encrypt, because you must read it to check a code
file -> sha256 if you only need to detect a change
```

## Password hashing

- A password hash is slow on purpose, and it includes a salt so two users with the same password do not look the same.
- bcrypt with a cost of 12 is what you can defend today.
- The salt is inside the bcrypt string. You do not invent a second scheme beside it.
- The cost must be high enough to slow guessing and low enough that login is still a moment.
- A breached table of bcrypt hashes is still serious. Rate-limit login. Do not store the password anywhere else 'for debugging'.
- bcrypt is a lock that takes a deliberate moment to open, and every door has a different key blank.
- careful: A cost of 4 because tests were slow, left in production. Lower the cost in tests, not in production.
- Why a salt?
- So an attacker cannot hash a common password once and compare it to every row. Each row has its own salt, stored with the hash by bcrypt.

```typescript
import { hash, compare } from "bcrypt";
const stored = await hash(password, 12);
const ok = await compare(password, stored);
```

- homework
```typescript
import { hash, compare } from "bcrypt";
const stored = await hash(password, 12);
const ok = await compare(password, stored);
```

## Secure sessions

- A secure session is a random id in a cookie the script cannot read, backed by a row you can delete.
- HttpOnly, Secure, SameSite, and a short lifetime.
- The id is long and random. It is not the user id.
- Logout deletes the row. A password change deletes the other sessions.
- Regenerate the id when the user logs in, so a pre-login cookie cannot be forced on them.
- The cookie is a cloakroom ticket. Stealing the ticket is useful only until you tear up the stub in the book.
- careful: A session id that is a predictable number.
- How do you kick a stolen phone?
- Delete that session row, or delete every session for the user. A JWT access token still lives until it expires, which is why the access token is short and the refresh token is the row you delete.

```http
Set-Cookie: sid=<random>; HttpOnly; Secure; SameSite=Lax
```

- homework
```http
Set-Cookie: sid=<random>; HttpOnly; Secure; SameSite=Lax
```

## JWT security

- A JWT is safe only as far as the signature, the expiry, and the way you store it.
- Verify the signature and the algorithm. Do not accept a token that says the algorithm is none.
- Check exp. Keep the lifetime short.
- The payload is readable. No passwords, no TOTP secrets.
- Put the user id and the roles. Re-read a sensitive role from the database if you must revoke it before the token expires.
- A JWT is a signed note with a date. Anyone can read the note. Nobody should be able to change it, and a note from last year is rubbish.
- careful: Decoding without verifying, or trusting the algorithm field from the token itself.
- The user was demoted. The token still says admin. What now?
- The access token lies until exp. For a demotion that matters, I check the role in the database on sensitive routes, or I keep the access token to a few minutes. The refresh token is already a row I can delete.

```typescript
verify(token, secret, { algorithms: ["HS256"] })
```

- homework
```typescript
verify(token, secret, { algorithms: ["HS256"] })
```

## OAuth security

- OAuth goes wrong when the redirect, the state, or the secret is loose.
- The redirect URI is an exact allowlist. An attacker who can choose it receives the code.
- state is a random value you store and check, so a login you started is the login that returns.
- The client secret stays on the server.
- The scopes are the minimum. A login does not need the user's entire mailbox.
- OAuth is a referral letter. The address on the envelope must be yours, and the letter must be the one you asked for.
- careful: A wildcard redirect, or a secret in the mobile bundle.
- What is the state parameter for?
- It ties the callback to the browser that started the login. Without it, another site can start a login and attach the result to a victim. I generate it, store it, and reject a callback that does not match.

```
redirect_uri must equal https://vms.arrobin.com/callback
state checked against the cookie you set
```

- homework
```
redirect_uri must equal https://vms.arrobin.com/callback
state checked against the cookie you set
```

## Secrets management

- Secrets are the keys to other systems. They live in the environment or a secret store, not in the repository.
- JWT signing key, database URL, Stripe secret, TOTP encryption key, SMTP password.
- Different values in development and production.
- A log, a Sentry breadcrumb, and an error page must not print them.
- Rotation is a planned change, and it is also the response to a leak.
- A secret is a key in a locked drawer at the office. The source code is a book that gets copied.
- careful: A default password that 'only works in dev' and is still in the file that deploys.
- How do you know a secret is required?
- The process exits on startup if it is absent. A fallback password in the code is a secret you have already published.

```
read from the environment at boot
refuse to boot if a required secret is missing
```

- homework
```
read from the environment at boot
refuse to boot if a required secret is missing
```

## IAM and least privilege

- Least privilege means each person and each programme can do only what its job needs.
- The API's database user cannot drop the database.
- A developer laptop does not use the production password.
- The worker that encodes video cannot read the payments table.
- Admin routes are a role, checked on the server.
- Least privilege is a key that opens one room. The master key stays in a drawer almost nobody opens.
- careful: Everyone in the team sharing the root password in a chat.
- Why not one database superuser?
- Because a bug or a leaked URL then includes the right to drop tables. A narrow user makes the worst day smaller.

```
api_user: select, insert, update on the app tables
migrator: used only by the deploy, not by the running API
```

- homework
```
api_user: select, insert, update on the app tables
migrator: used only by the deploy, not by the running API
```

## Security headers and CSP

- Headers are instructions to the browser about what the page may do.
- Content-Security-Policy names where scripts and images may come from.
- X-Content-Type-Options: nosniff stops the browser guessing that a file is a script.
- Referrer-Policy limits what URL you leak to the next site.
- Strict-Transport-Security tells the browser to keep using HTTPS.
- A policy you copy from a blog and never test will break the app, or be so loose it does nothing. Start strict in a report mode if you need to.
- Headers are the house rules posted at the door. The locks are still the locks. The rules help the guests behave.
- careful: A policy of star-star because one image broke, left there for a year.
- What does CSP buy you after React already escapes?
- A second chance. If a bug renders raw HTML, the browser still refuses a script from a host you did not name. It is not a reason to skip escaping.

```http
Content-Security-Policy: default-src 'self'
X-Content-Type-Options: nosniff
Referrer-Policy: no-referrer
```

- homework
```http
Content-Security-Policy: default-src 'self'
X-Content-Type-Options: nosniff
Referrer-Policy: no-referrer
```

## Rate limiting and DDoS

- A rate limit slows abuse you can name. A volumetric flood is a network problem in front of your process.
- Login and password reset are limited per IP and per account.
- 429 is the answer, with Retry-After.
- A flood of traffic that fills the pipe is absorbed by the host or a scrubbing service, not by a line of Node code.
- A limit that is only in the UI does not exist.
- The rate limit is a turnstile. A flood that buries the building is a different department.
- careful: A limit so low that a school sharing one IP cannot log in, or so high that guessing is free.
- Can the API rate-limit a DDoS?
- It can limit a login guesser who is speaking HTTP. It cannot help when the pipe is full of junk before nginx. I say which problem I am solving.

```
login: 10 per minute per IP in Redis
a network flood: the provider, not the Nest guard
```

- homework
```
login: 10 per minute per IP in Redis
a network flood: the provider, not the Nest guard
```

## Input validation

- Validation rejects the shape you do not accept, before the business rule runs.
- Types, lengths, enums, and formats at the edge.
- Allowlists beat blocklists. A role is one of three strings, not 'anything except these bad words'.
- Reject unexpected fields on an update, so a user cannot post role and have it stick.
- The database constraint remains, for the path you forgot.
- Validation is the door size. What does not fit does not come in. You do not sand it down into a different object.
- careful: Stripping characters until the string is 'safe', and changing the meaning.
- Validation or sanitisation?
- Validation refuses the bad shape. Sanitisation rewrites it. I refuse a role I do not know. I do not silently map it to admin. For text I store, I escape on the way out.

```typescript
z.object({ role: z.enum(["viewer", "operator", "admin"]) }).strict()
```

- homework
```typescript
z.object({ role: z.enum(["viewer", "operator", "admin"]) }).strict()
```

## Dependency scanning

- Your application includes other people's packages. A known bug in one of them is your bug until you update.
- npm audit and GitHub's dependency alerts read the lockfile.
- A high advisory on a package you call from a request is urgent. A low advisory in a build tool is scheduled.
- Renovate or Dependabot opens the pull request. CI must pass before you merge.
- Pin the lockfile. A floating version is a surprise deploy.
- Scanning is reading the recall list for parts already in the car.
- careful: npm audit fix --force on Friday because the count was embarrassing.
- Do you merge every audit?
- I read it. A denial of service in a parser we feed user input is this week. A note about a dev tool we do not ship can wait for the next maintenance window. I do not ignore the list.

```bash
npm ci
npm audit --omit=dev
```

- homework
```bash
npm ci
npm audit --omit=dev
```

## Penetration testing

- A penetration test is a permitted, scoped attempt by someone else to find the holes, followed by you fixing them.
- You agree the targets, the time, and the rules. Your own production is not a place for an uninvited experiment, and neither is anyone else's.
- The report is a list of findings with impact. You fix, then you retest.
- Before you pay for one, run the checklist you can already name: roles, validation, headers, dependencies, backups.
- A test is a sample. A clear report with no findings is not a proof the system is finished.
- A test is a fire drill you scheduled. It is not setting the building alight to see what happens, and it is not a certificate you frame.
- careful: Calling a scan of your own curiosity against a system you do not operate a 'test'.
- What would you hand a tester first?
- Two accounts of different roles, the list of routes, and a request that the test stay inside those hosts. I want a broken access-control finding more than a clever story.

```
scope: vms.arrobin.com, test accounts, no denial of service
output: findings, impact, fix, retest
```

- homework
```
scope: vms.arrobin.com, test accounts, no denial of service
output: findings, impact, fix, retest
```

## Prompt injection

- Prompt injection is untrusted text that tries to override the instruction you gave a model.
- The impact is the model ignoring your format, leaking the prompt, or calling a tool it should not call.
- You separate instructions from data. You label the user text as data.
- The real control is the tool layer: the model cannot run a tool the user could not run, and numbers are checked against code.
- Do not put a secret in the prompt and hope the model keeps it.
- This book will not list trick phrases. The defence is the boundary, not a filter of naughty sentences.
- Prompt injection is a note hidden in a stack of papers that says 'ignore the boss'. The clerk might obey. The safe still has its own lock, and that lock is your code.
- careful: A secret in the system prompt, and a tool that will do anything the model asks.
- Can you filter the bad prompts?
- A filter catches yesterday's wording. I assume some wording will get through. The tool still checks the role, and the answer's number still has to match the function. That survives a new wording.

```
tools check the caller's role
money comes from laytime(), not from the paragraph
untrusted text is wrapped as data
```

- homework
```
tools check the caller's role
money comes from laytime(), not from the paragraph
untrusted text is wrapped as data
```
