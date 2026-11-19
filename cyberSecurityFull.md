# Cyber Security

## chapter 1 OWASP Top 10

- the OWASP Top 10 is a short list of the ways web apps usually fail
- it is a checklist for one route, not a certificate
- broken access control: the UI hides a button and the API does not check the role
- injection: user text is stitched into a query, a command, or a page
- cryptographic failures: passwords stored raw, or TLS skipped
- identification failures: weak login, no rate limit, tokens that never expire
- for each route we name: who may call it, how the query is built, what is logged, what is limited
- the items we can point at in our code: access control on the API, bcrypt, short JWTs, refresh rotation, rate limits, validation at the edge

```text
for each route: auth, role, validation, query style, log redaction, rate limit
```

- reciting ten names is not the same as walking one route
- the rest of this file is that walk, one failure at a time, and the fix

- homework of chapter 1
```text
# 1a  the check that must exist even if the button is hidden
# 1b  three controls we can point at in the products
# 1c  why the list is a review, not a badge
```

## chapter 2 SQL injection

- SQL injection happens when a program builds a query by gluing user text into the SQL string
- the text can change the meaning of the query
- the impact is reading or changing rows the person should not touch
- the fix is to send the SQL and the values separately. the database binds the value as data
- Prisma's normal methods do this
- a raw query we build with string concatenation does not
- a database user with only the rights it needs limits the damage of any remaining bug

```ts
await db.$queryRaw`SELECT * FROM users WHERE email = ${email}`;
```

- the tagged form binds the value. it is not pasted into the sentence
- we do not concatenate email into a string of SQL
- a front-end check is not this fix. the request can skip the browser

- homework of chapter 2
```ts
// 2a  which form binds the value
// 2b  why a check in React is not enough
// 2c  what a limited database user changes about the damage
```

## chapter 3 XSS

- cross-site scripting is when someone else's text runs as script in a user's browser
- the impact is that script acting as the user: reading the page, calling our API as them
- React escapes text in JSX. the dangerous path is rendering HTML on purpose
- we do not use dangerouslySetInnerHTML for a comment, a vessel name, or a chat line
- a content security policy is a second net. the browser refuses script that did not come from a place we named
- if a script runs on our origin, it can call our API with the user's session
- a token in localStorage is also readable by that script
- escaping untrusted text is the first control. a strict content security policy is the next

```tsx
<p>{comment}</p>
```

- the braces are text. they are not HTML
- a rich-text box needs a sanitiser we chose, and a test, or it does not ship

- homework of chapter 3
```tsx
// 3a  the safe way to show a vessel name in React
// 3b  where an XSS meets a token that lives in localStorage
// 3c  what the content security policy refuses
```

## chapter 4 CSRF and CORS

- CSRF = another site causes the browser to send a request that already has our cookie
- cookies are attached by the browser. a hostile page can submit a form to our origin if the cookie is sent
- SameSite=Lax or Strict stops many of those sends
- a CSRF token is a second value the hostile page cannot read. we check it on the server
- a JWT we set in an Authorization header is not attached automatically. a plain form post does not carry it
- this bug shows up when we move the session into a cookie. we add SameSite and the CSRF token in the same change
- CORS = the browser's rule about which other origins may read a response
- the browser sends Origin. our API answers with the origins it allows
- CORS is not access control. a non-browser client ignores it
- reflecting whatever Origin arrived, together with credentials, lets any website call the API as the user
- we allow the web origin we actually have. we do not combine a star with credentials

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
Access-Control-Allow-Origin: https://vms.arrobin.com
Access-Control-Allow-Credentials: true
```

- the cookie line is the CSRF chapter. the CORS lines are the guest list for browsers
- a tool that is not a browser does not look at the guest list. the guard still checks the token

- homework of chapter 4
```http
# 4a  why a bearer header is not sent by a foreign form
# 4b  the two things we add on the day we switch to a cookie session
# 4c  why CORS star plus credentials is wrong
# 4d  why a passing CORS check is not a role check
```

## chapter 5 SSRF

- server-side request forgery is when our server fetches a URL the user supplied
- the user can point that fetch at a place the server can see and the user cannot
- the impact is the server being used as a client toward internal addresses
- the fix is an allowlist of hosts and schemes, and a refusal of private and link-local addresses
- a webhook test button, an image import, or "fetch this video URL" is the usual shape
- we resolve the name and check the address before the request
- we do not follow a redirect onto a private address
- the safe version uploads the bytes, or fetches only from a host we chose

```text
allow only https
allow only hosts we named
refuse addresses that are internal to the network
```

- Anemi takes an upload. it does not need to fetch an arbitrary URL
- a logo import that accepts any URL is the feature we do not add

- homework of chapter 5
```text
# 5a  who connects to the internal address, the user or our server
# 5b  the three rules on the allowlist
# 5c  the design that does not need a URL from the user
```

## chapter 6 HTTPS, hashing, and encryption

- HTTPS is HTTP inside TLS
- TLS protects the bytes on the path and checks the server name
- a certificate must match the domain, be inside its dates, and chain to a root the client trusts
- we redirect HTTP to HTTPS
- TLS does not make a weak password strong, and it does not fix a missing role check
- on localhost, nginx to Node can be plain HTTP. the public hop is TLS
- a hash is one way. we cannot read the password back out
- encryption is reversible if we have the key
- we hash a password. we encrypt a TOTP secret, because we must read it to check the code
- the encryption key is not in the database beside the secret

```text
password -> bcrypt hash -> stored
TOTP secret -> encrypt with a key outside the database -> stored
public hop -> TLS
```

- hashing and encryption are not interchangeable. a password we can decrypt is a password we stored wrong
- a certificate we never renew breaks the site on a Saturday

- homework of chapter 6
```text
# 6a  hash or encrypt the password
# 6b  hash or encrypt the TOTP secret, and why
# 6c  three checks on a certificate
# 6d  which hop must be TLS
```

## chapter 7 Password hashing and secure sessions

- bcrypt has a salt and a cost. the salt is different per password. the cost is the slowness
- cost 12 is the figure we use
- login uses compare. it does not decrypt
- a session id is random and long. we store the session server-side, or we use the JWT design we already ship
- the cookie flags are HttpOnly, Secure, and SameSite
- the access token is short, about 15 minutes
- the refresh token is stored as a hash and rotated
- if a refresh token is reused after rotation, we revoke the family
- a session that never expires is a stolen cookie that works forever
- we do not put the session id in a URL. URLs end up in logs

```ts
import { hash, compare } from "bcrypt";

const passwordHash = await hash(plain, 12);
const ok = await compare(plain, passwordHash);
```

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
```

- the picture had these two lines partly hidden. this is the full note
- logout deletes the server session or revokes the refresh token. clearing the screen is not logout

- homework of chapter 7
```ts
// 7a  what we store instead of the password
// 7b  the three cookie flags
// 7c  what we do when a rotated refresh token shows up again
// 7d  why the session id stays out of the URL
```

## chapter 8 JWT security and OAuth security

- a JWT is readable. the signature stops edits. it does not stop someone who stole it from reading the payload
- we put the user id and the roles in it. we do not put a password, a secret, or a long-lived power we cannot revoke
- we check the signature, the expiry, and the expected algorithm
- we do not accept a token that says its algorithm is none
- the access token is short so a leak expires
- refresh rotation is how we notice reuse
- OAuth's client secret stays on the server
- the code is traded for tokens on the server. the browser does not do that trade with the secret
- the redirect URI is an exact allowlist. an open redirect turns the code over to someone else
- state is a random value we check when the user comes back, so the response matches the request we started

```text
check signature
check exp
check algorithm is the one we sign with
access token minutes, not months
```

- a JWT in localStorage is stealable by script. a cookie session has CSRF to solve. we pick one and finish its controls
- our products use our own login. "login with Google" would add the secret, the redirect allowlist, and the state check

- homework of chapter 8
```text
# 8a  what the signature does not hide
# 8b  three checks on an incoming JWT
# 8c  where the OAuth client secret lives
# 8d  what an open redirect URI gives away
```

## chapter 9 Secrets, IAM, headers, and CSP

- a secret in git is still in the history after we delete the file
- secrets live in the environment or a secret store. `.env` is gitignored
- we rotate by adding the new value, deploying, then removing the old
- IAM = who may do what, on the cloud and in the app
- least privilege = the database user cannot drop the cluster. the deploy key cannot read every secret. the app role cannot do more than its routes
- a human admin account is not the application's database login
- security headers tell the browser extra rules
- Content-Security-Policy names where script may load from
- X-Content-Type-Options: nosniff stops a file being treated as a different type
- a strict transport header tells the browser to stay on HTTPS
- frame rules stop another site embedding us when we do not want that

```text
Content-Security-Policy: default-src 'self'
X-Content-Type-Options: nosniff
```

- the policy has to match how the app actually loads script. a policy we copy and never test breaks the page or protects nothing
- least privilege on a route is the role guard. least privilege on the server is the database user and the cloud keys

- homework of chapter 9
```text
# 9a  what we do after a secret was committed
# 9b  why the app's database user is not a superuser
# 9c  what the content security policy is for
# 9d  a header that keeps the browser on HTTPS
```

## chapter 10 Rate limiting, DDoS, and input validation

- a rate limit slows abuse and mistakes. it is not a full answer to a flood
- login is a small limit. a list route can be higher
- the counter is in Redis so every process agrees
- 429 is the status
- a distributed flood fills the pipe before our app runs. the host or the front door has to absorb that. our limiter protects the login and the expensive routes
- validation rejects the shape we do not handle
- we check type, length, and range at the edge
- we do not build a query, a path, or a shell command from the raw string
- a file upload has a size limit and an allowed type
- the database constraints stay, for the client that skipped our edge

```ts
const CreatePortCall = z.object({
  vesselName: z.string().min(1).max(120),
  allowedHours: z.number().positive().max(24 * 30),
});
```

- max length is part of validation. an unbounded string is a memory problem as well as a bad row
- the limiter and the validator are both on the route. one does not replace the other

- homework of chapter 10
```ts
// 10a  the status when the login limit trips
// 10b  why the limit is not the whole answer to a flood
// 10c  add a max length to a team name
// 10d  a fact the database still checks if Zod is bypassed
```

## chapter 11 Dependency scanning

- a dependency is code we did not write and we do run
- a lockfile pins the versions. `npm ci` installs that pin
- a scanner reads the lockfile against a list of known problems
- Dependabot or Renovate opens the pull request. CI must pass before we merge
- we read the note. a bug in a parser we feed user input is this week
- a note about a dev tool we do not ship can wait for the next maintenance window
- `npm audit fix --force` on a Friday is how a lockfile becomes a surprise upgrade
- we do not ignore the list. we order it

```bash
npm ci
npm audit --omit=dev
```

- the command is a reading list. the merge is a decision
- a floating version with no lockfile is a different tree on every install

- homework of chapter 11
```bash
# 11a  the install command that respects the lockfile
# 11b  a finding we would patch this week
# 11c  why force-fix is not the Friday plan
```

## chapter 12 Penetration testing and prompt injection

- a penetration test is a permitted, scoped check by someone we asked, followed by fixes
- we agree the targets, the time, and the rules
- our own production is not a place for an unplanned experiment. neither is anyone else's system
- the report is findings with impact. we fix, then we retest
- before we pay for one, we walk the checklist we can already name: roles, validation, headers, dependencies, backups
- a clear report is a sample. it is not proof the system is finished
- prompt injection is untrusted text that tries to override the instruction we gave a model
- the impact is a wrong format, a leaked prompt, or a tool call the user should not have
- we separate instructions from data. we label the user text as data
- the real control is the tool layer. the model cannot run a tool the user could not run
- numbers are checked against code
- we do not put a secret in the prompt
- this note does not list trick phrases. a filter catches yesterday's wording. the tool check and the number check survive a new wording

```text
scope: the hosts we named, test accounts, no denial of service
tools check the caller's role
money comes from laytime(), not from the paragraph
untrusted text is wrapped as data
```

- a test we scheduled is a fire drill. it is not something we point at a system we do not operate
- a secret in the system prompt, and a tool that will do anything the model asks, is the failure

- homework of chapter 12
```text
# 12a  what we hand a tester: which accounts, which hosts
# 12b  what we do not point at a system we do not operate
# 12c  the two controls that still hold when the wording is new
# 12d  where 7500 has to come from
```
