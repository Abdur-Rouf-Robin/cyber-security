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

- example 1. review the route for port-calls pc_12
- who may call it
- the query is parameterised
- the log has no password
- the write is rate limited
- the role is checked on the API, not only by hiding a button

```text
route /port-calls/pc_12
auth yes
role operator for POST
validation on vesselName
query parameterised
log redacts secrets
rate limit on login and on this write
```

- homework
```text
# 1a  the hidden button is not the check for pc_12
# 1b  name bcrypt, short JWT, and validation as controls we can point at
# 1c  walk this one route, do not only recite ten names
```

- example 2. review the route for matches m_1
- who may call it
- the query is parameterised
- the log has no password
- the write is rate limited
- the role is checked on the API, not only by hiding a button

```text
route /matches/m_1
auth yes
role operator for POST
validation on home
query parameterised
log redacts secrets
rate limit on login and on this write
```

- homework
```text
# 2a  the hidden button is not the check for m_1
# 2b  name bcrypt, short JWT, and validation as controls we can point at
# 2c  walk this one route, do not only recite ten names
```

- example 3. review the route for tournaments t_9
- who may call it
- the query is parameterised
- the log has no password
- the write is rate limited
- the role is checked on the API, not only by hiding a button

```text
route /tournaments/t_9
auth yes
role operator for POST
validation on name
query parameterised
log redacts secrets
rate limit on login and on this write
```

- homework
```text
# 3a  the hidden button is not the check for t_9
# 3b  name bcrypt, short JWT, and validation as controls we can point at
# 3c  walk this one route, do not only recite ten names
```

- example 4. review the route for videos v_4
- who may call it
- the query is parameterised
- the log has no password
- the write is rate limited
- the role is checked on the API, not only by hiding a button

```text
route /videos/v_4
auth yes
role operator for POST
validation on title
query parameterised
log redacts secrets
rate limit on login and on this write
```

- homework
```text
# 4a  the hidden button is not the check for v_4
# 4b  name bcrypt, short JWT, and validation as controls we can point at
# 4c  walk this one route, do not only recite ten names
```

- example 5. review the route for facts f_2
- who may call it
- the query is parameterised
- the log has no password
- the write is rate limited
- the role is checked on the API, not only by hiding a button

```text
route /facts/f_2
auth yes
role operator for POST
validation on kind
query parameterised
log redacts secrets
rate limit on login and on this write
```

- homework
```text
# 5a  the hidden button is not the check for f_2
# 5b  name bcrypt, short JWT, and validation as controls we can point at
# 5c  walk this one route, do not only recite ten names
```

- example 6. review the route for users u_3
- who may call it
- the query is parameterised
- the log has no password
- the write is rate limited
- the role is checked on the API, not only by hiding a button

```text
route /users/u_3
auth yes
role operator for POST
validation on email
query parameterised
log redacts secrets
rate limit on login and on this write
```

- homework
```text
# 6a  the hidden button is not the check for u_3
# 6b  name bcrypt, short JWT, and validation as controls we can point at
# 6c  walk this one route, do not only recite ten names
```

- example 7. review the route for payments pay_8
- who may call it
- the query is parameterised
- the log has no password
- the write is rate limited
- the role is checked on the API, not only by hiding a button

```text
route /payments/pay_8
auth yes
role operator for POST
validation on eventId
query parameterised
log redacts secrets
rate limit on login and on this write
```

- homework
```text
# 7a  the hidden button is not the check for pay_8
# 7b  name bcrypt, short JWT, and validation as controls we can point at
# 7c  walk this one route, do not only recite ten names
```

- example 8. review the route for rooms room_2
- who may call it
- the query is parameterised
- the log has no password
- the write is rate limited
- the role is checked on the API, not only by hiding a button

```text
route /rooms/room_2
auth yes
role operator for POST
validation on sessionId
query parameterised
log redacts secrets
rate limit on login and on this write
```

- homework
```text
# 8a  the hidden button is not the check for room_2
# 8b  name bcrypt, short JWT, and validation as controls we can point at
# 8c  walk this one route, do not only recite ten names
```

- example 9. review the route for vessels vs_7
- who may call it
- the query is parameterised
- the log has no password
- the write is rate limited
- the role is checked on the API, not only by hiding a button

```text
route /vessels/vs_7
auth yes
role operator for POST
validation on name
query parameterised
log redacts secrets
rate limit on login and on this write
```

- homework
```text
# 9a  the hidden button is not the check for vs_7
# 9b  name bcrypt, short JWT, and validation as controls we can point at
# 9c  walk this one route, do not only recite ten names
```

- example 10. review the route for scores sc_3
- who may call it
- the query is parameterised
- the log has no password
- the write is rate limited
- the role is checked on the API, not only by hiding a button

```text
route /scores/sc_3
auth yes
role operator for POST
validation on points
query parameterised
log redacts secrets
rate limit on login and on this write
```

- homework
```text
# 10a  the hidden button is not the check for sc_3
# 10b  name bcrypt, short JWT, and validation as controls we can point at
# 10c  walk this one route, do not only recite ten names
```

- example 11. review the route for teams tm_2
- who may call it
- the query is parameterised
- the log has no password
- the write is rate limited
- the role is checked on the API, not only by hiding a button

```text
route /teams/tm_2
auth yes
role operator for POST
validation on name
query parameterised
log redacts secrets
rate limit on login and on this write
```

- homework
```text
# 11a  the hidden button is not the check for tm_2
# 11b  name bcrypt, short JWT, and validation as controls we can point at
# 11c  walk this one route, do not only recite ten names
```

- example 12. review the route for uploads up_6
- who may call it
- the query is parameterised
- the log has no password
- the write is rate limited
- the role is checked on the API, not only by hiding a button

```text
route /uploads/up_6
auth yes
role operator for POST
validation on key
query parameterised
log redacts secrets
rate limit on login and on this write
```

- homework
```text
# 12a  the hidden button is not the check for up_6
# 12b  name bcrypt, short JWT, and validation as controls we can point at
# 12c  walk this one route, do not only recite ten names
```

- example 13. review the route for standings st_1
- who may call it
- the query is parameterised
- the log has no password
- the write is rate limited
- the role is checked on the API, not only by hiding a button

```text
route /standings/st_1
auth yes
role operator for POST
validation on player
query parameterised
log redacts secrets
rate limit on login and on this write
```

- homework
```text
# 13a  the hidden button is not the check for st_1
# 13b  name bcrypt, short JWT, and validation as controls we can point at
# 13c  walk this one route, do not only recite ten names
```

- example 14. review the route for notices n_2
- who may call it
- the query is parameterised
- the log has no password
- the write is rate limited
- the role is checked on the API, not only by hiding a button

```text
route /notices/n_2
auth yes
role operator for POST
validation on port
query parameterised
log redacts secrets
rate limit on login and on this write
```

- homework
```text
# 14a  the hidden button is not the check for n_2
# 14b  name bcrypt, short JWT, and validation as controls we can point at
# 14c  walk this one route, do not only recite ten names
```

- example 15. review the route for brackets b_3
- who may call it
- the query is parameterised
- the log has no password
- the write is rate limited
- the role is checked on the API, not only by hiding a button

```text
route /brackets/b_3
auth yes
role operator for POST
validation on round
query parameterised
log redacts secrets
rate limit on login and on this write
```

- homework
```text
# 15a  the hidden button is not the check for b_3
# 15b  name bcrypt, short JWT, and validation as controls we can point at
# 15c  walk this one route, do not only recite ten names
```

- example 16. review the route for sessions se_1
- who may call it
- the query is parameterised
- the log has no password
- the write is rate limited
- the role is checked on the API, not only by hiding a button

```text
route /sessions/se_1
auth yes
role operator for POST
validation on userId
query parameterised
log redacts secrets
rate limit on login and on this write
```

- homework
```text
# 16a  the hidden button is not the check for se_1
# 16b  name bcrypt, short JWT, and validation as controls we can point at
# 16c  walk this one route, do not only recite ten names
```

- example 17. review the route for queues q_1
- who may call it
- the query is parameterised
- the log has no password
- the write is rate limited
- the role is checked on the API, not only by hiding a button

```text
route /queues/q_1
auth yes
role operator for POST
validation on name
query parameterised
log redacts secrets
rate limit on login and on this write
```

- homework
```text
# 17a  the hidden button is not the check for q_1
# 17b  name bcrypt, short JWT, and validation as controls we can point at
# 17c  walk this one route, do not only recite ten names
```

- example 18. review the route for roles r_1
- who may call it
- the query is parameterised
- the log has no password
- the write is rate limited
- the role is checked on the API, not only by hiding a button

```text
route /roles/r_1
auth yes
role operator for POST
validation on name
query parameterised
log redacts secrets
rate limit on login and on this write
```

- homework
```text
# 18a  the hidden button is not the check for r_1
# 18b  name bcrypt, short JWT, and validation as controls we can point at
# 18c  walk this one route, do not only recite ten names
```

- example 19. review the route for port-calls pc_12
- who may call it
- the query is parameterised
- the log has no password
- the write is rate limited
- the role is checked on the API, not only by hiding a button

```text
route /port-calls/pc_12
auth yes
role operator for POST
validation on vesselName
query parameterised
log redacts secrets
rate limit on login and on this write
```

- homework
```text
# 19a  the hidden button is not the check for pc_12
# 19b  name bcrypt, short JWT, and validation as controls we can point at
# 19c  walk this one route, do not only recite ten names
```

- example 20. review the route for matches m_1
- who may call it
- the query is parameterised
- the log has no password
- the write is rate limited
- the role is checked on the API, not only by hiding a button

```text
route /matches/m_1
auth yes
role operator for POST
validation on home
query parameterised
log redacts secrets
rate limit on login and on this write
```

- homework
```text
# 20a  the hidden button is not the check for m_1
# 20b  name bcrypt, short JWT, and validation as controls we can point at
# 20c  walk this one route, do not only recite ten names
```

- example 21. review the route for tournaments t_9
- who may call it
- the query is parameterised
- the log has no password
- the write is rate limited
- the role is checked on the API, not only by hiding a button

```text
route /tournaments/t_9
auth yes
role operator for POST
validation on name
query parameterised
log redacts secrets
rate limit on login and on this write
```

- homework
```text
# 21a  the hidden button is not the check for t_9
# 21b  name bcrypt, short JWT, and validation as controls we can point at
# 21c  walk this one route, do not only recite ten names
```

- example 22. review the route for videos v_4
- who may call it
- the query is parameterised
- the log has no password
- the write is rate limited
- the role is checked on the API, not only by hiding a button

```text
route /videos/v_4
auth yes
role operator for POST
validation on title
query parameterised
log redacts secrets
rate limit on login and on this write
```

- homework
```text
# 22a  the hidden button is not the check for v_4
# 22b  name bcrypt, short JWT, and validation as controls we can point at
# 22c  walk this one route, do not only recite ten names
```

- example 23. review the route for facts f_2
- who may call it
- the query is parameterised
- the log has no password
- the write is rate limited
- the role is checked on the API, not only by hiding a button

```text
route /facts/f_2
auth yes
role operator for POST
validation on kind
query parameterised
log redacts secrets
rate limit on login and on this write
```

- homework
```text
# 23a  the hidden button is not the check for f_2
# 23b  name bcrypt, short JWT, and validation as controls we can point at
# 23c  walk this one route, do not only recite ten names
```

- example 24. review the route for users u_3
- who may call it
- the query is parameterised
- the log has no password
- the write is rate limited
- the role is checked on the API, not only by hiding a button

```text
route /users/u_3
auth yes
role operator for POST
validation on email
query parameterised
log redacts secrets
rate limit on login and on this write
```

- homework
```text
# 24a  the hidden button is not the check for u_3
# 24b  name bcrypt, short JWT, and validation as controls we can point at
# 24c  walk this one route, do not only recite ten names
```

- example 25. review the route for payments pay_8
- who may call it
- the query is parameterised
- the log has no password
- the write is rate limited
- the role is checked on the API, not only by hiding a button

```text
route /payments/pay_8
auth yes
role operator for POST
validation on eventId
query parameterised
log redacts secrets
rate limit on login and on this write
```

- homework
```text
# 25a  the hidden button is not the check for pay_8
# 25b  name bcrypt, short JWT, and validation as controls we can point at
# 25c  walk this one route, do not only recite ten names
```

- example 26. review the route for rooms room_2
- who may call it
- the query is parameterised
- the log has no password
- the write is rate limited
- the role is checked on the API, not only by hiding a button

```text
route /rooms/room_2
auth yes
role operator for POST
validation on sessionId
query parameterised
log redacts secrets
rate limit on login and on this write
```

- homework
```text
# 26a  the hidden button is not the check for room_2
# 26b  name bcrypt, short JWT, and validation as controls we can point at
# 26c  walk this one route, do not only recite ten names
```

- example 27. review the route for vessels vs_7
- who may call it
- the query is parameterised
- the log has no password
- the write is rate limited
- the role is checked on the API, not only by hiding a button

```text
route /vessels/vs_7
auth yes
role operator for POST
validation on name
query parameterised
log redacts secrets
rate limit on login and on this write
```

- homework
```text
# 27a  the hidden button is not the check for vs_7
# 27b  name bcrypt, short JWT, and validation as controls we can point at
# 27c  walk this one route, do not only recite ten names
```

- example 28. review the route for scores sc_3
- who may call it
- the query is parameterised
- the log has no password
- the write is rate limited
- the role is checked on the API, not only by hiding a button

```text
route /scores/sc_3
auth yes
role operator for POST
validation on points
query parameterised
log redacts secrets
rate limit on login and on this write
```

- homework
```text
# 28a  the hidden button is not the check for sc_3
# 28b  name bcrypt, short JWT, and validation as controls we can point at
# 28c  walk this one route, do not only recite ten names
```

- example 29. review the route for teams tm_2
- who may call it
- the query is parameterised
- the log has no password
- the write is rate limited
- the role is checked on the API, not only by hiding a button

```text
route /teams/tm_2
auth yes
role operator for POST
validation on name
query parameterised
log redacts secrets
rate limit on login and on this write
```

- homework
```text
# 29a  the hidden button is not the check for tm_2
# 29b  name bcrypt, short JWT, and validation as controls we can point at
# 29c  walk this one route, do not only recite ten names
```

- example 30. review the route for uploads up_6
- who may call it
- the query is parameterised
- the log has no password
- the write is rate limited
- the role is checked on the API, not only by hiding a button

```text
route /uploads/up_6
auth yes
role operator for POST
validation on key
query parameterised
log redacts secrets
rate limit on login and on this write
```

- homework
```text
# 30a  the hidden button is not the check for up_6
# 30b  name bcrypt, short JWT, and validation as controls we can point at
# 30c  walk this one route, do not only recite ten names
```

- example 31. review the route for standings st_1
- who may call it
- the query is parameterised
- the log has no password
- the write is rate limited
- the role is checked on the API, not only by hiding a button

```text
route /standings/st_1
auth yes
role operator for POST
validation on player
query parameterised
log redacts secrets
rate limit on login and on this write
```

- homework
```text
# 31a  the hidden button is not the check for st_1
# 31b  name bcrypt, short JWT, and validation as controls we can point at
# 31c  walk this one route, do not only recite ten names
```

- example 32. review the route for notices n_2
- who may call it
- the query is parameterised
- the log has no password
- the write is rate limited
- the role is checked on the API, not only by hiding a button

```text
route /notices/n_2
auth yes
role operator for POST
validation on port
query parameterised
log redacts secrets
rate limit on login and on this write
```

- homework
```text
# 32a  the hidden button is not the check for n_2
# 32b  name bcrypt, short JWT, and validation as controls we can point at
# 32c  walk this one route, do not only recite ten names
```

- example 33. review the route for brackets b_3
- who may call it
- the query is parameterised
- the log has no password
- the write is rate limited
- the role is checked on the API, not only by hiding a button

```text
route /brackets/b_3
auth yes
role operator for POST
validation on round
query parameterised
log redacts secrets
rate limit on login and on this write
```

- homework
```text
# 33a  the hidden button is not the check for b_3
# 33b  name bcrypt, short JWT, and validation as controls we can point at
# 33c  walk this one route, do not only recite ten names
```

- example 34. review the route for sessions se_1
- who may call it
- the query is parameterised
- the log has no password
- the write is rate limited
- the role is checked on the API, not only by hiding a button

```text
route /sessions/se_1
auth yes
role operator for POST
validation on userId
query parameterised
log redacts secrets
rate limit on login and on this write
```

- homework
```text
# 34a  the hidden button is not the check for se_1
# 34b  name bcrypt, short JWT, and validation as controls we can point at
# 34c  walk this one route, do not only recite ten names
```

- example 35. review the route for queues q_1
- who may call it
- the query is parameterised
- the log has no password
- the write is rate limited
- the role is checked on the API, not only by hiding a button

```text
route /queues/q_1
auth yes
role operator for POST
validation on name
query parameterised
log redacts secrets
rate limit on login and on this write
```

- homework
```text
# 35a  the hidden button is not the check for q_1
# 35b  name bcrypt, short JWT, and validation as controls we can point at
# 35c  walk this one route, do not only recite ten names
```

- example 36. review the route for roles r_1
- who may call it
- the query is parameterised
- the log has no password
- the write is rate limited
- the role is checked on the API, not only by hiding a button

```text
route /roles/r_1
auth yes
role operator for POST
validation on name
query parameterised
log redacts secrets
rate limit on login and on this write
```

- homework
```text
# 36a  the hidden button is not the check for r_1
# 36b  name bcrypt, short JWT, and validation as controls we can point at
# 36c  walk this one route, do not only recite ten names
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

- example 1. bind the value for pc_12
- the SQL text and the value travel separately
- Prisma's normal calls do this
- a string we concatenate does not
- the database user cannot do more than this app needs

```ts
await db.$queryRaw`SELECT id, vesselName FROM items WHERE id = ${id}`;
// id is pc_12 when the caller asks for that row
// the value is bound. it is not glued into the sentence
```

- homework
```ts
// 1a  the tagged query binds id
// 1b  a React check is not this fix
// 1c  a limited database user caps the damage
```

- example 2. bind the value for m_1
- the SQL text and the value travel separately
- Prisma's normal calls do this
- a string we concatenate does not
- the database user cannot do more than this app needs

```ts
await db.$queryRaw`SELECT id, home FROM items WHERE id = ${id}`;
// id is m_1 when the caller asks for that row
// the value is bound. it is not glued into the sentence
```

- homework
```ts
// 2a  the tagged query binds id
// 2b  a React check is not this fix
// 2c  a limited database user caps the damage
```

- example 3. bind the value for t_9
- the SQL text and the value travel separately
- Prisma's normal calls do this
- a string we concatenate does not
- the database user cannot do more than this app needs

```ts
await db.$queryRaw`SELECT id, name FROM items WHERE id = ${id}`;
// id is t_9 when the caller asks for that row
// the value is bound. it is not glued into the sentence
```

- homework
```ts
// 3a  the tagged query binds id
// 3b  a React check is not this fix
// 3c  a limited database user caps the damage
```

- example 4. bind the value for v_4
- the SQL text and the value travel separately
- Prisma's normal calls do this
- a string we concatenate does not
- the database user cannot do more than this app needs

```ts
await db.$queryRaw`SELECT id, title FROM items WHERE id = ${id}`;
// id is v_4 when the caller asks for that row
// the value is bound. it is not glued into the sentence
```

- homework
```ts
// 4a  the tagged query binds id
// 4b  a React check is not this fix
// 4c  a limited database user caps the damage
```

- example 5. bind the value for f_2
- the SQL text and the value travel separately
- Prisma's normal calls do this
- a string we concatenate does not
- the database user cannot do more than this app needs

```ts
await db.$queryRaw`SELECT id, kind FROM items WHERE id = ${id}`;
// id is f_2 when the caller asks for that row
// the value is bound. it is not glued into the sentence
```

- homework
```ts
// 5a  the tagged query binds id
// 5b  a React check is not this fix
// 5c  a limited database user caps the damage
```

- example 6. bind the value for u_3
- the SQL text and the value travel separately
- Prisma's normal calls do this
- a string we concatenate does not
- the database user cannot do more than this app needs

```ts
await db.$queryRaw`SELECT id, email FROM items WHERE id = ${id}`;
// id is u_3 when the caller asks for that row
// the value is bound. it is not glued into the sentence
```

- homework
```ts
// 6a  the tagged query binds id
// 6b  a React check is not this fix
// 6c  a limited database user caps the damage
```

- example 7. bind the value for pay_8
- the SQL text and the value travel separately
- Prisma's normal calls do this
- a string we concatenate does not
- the database user cannot do more than this app needs

```ts
await db.$queryRaw`SELECT id, eventId FROM items WHERE id = ${id}`;
// id is pay_8 when the caller asks for that row
// the value is bound. it is not glued into the sentence
```

- homework
```ts
// 7a  the tagged query binds id
// 7b  a React check is not this fix
// 7c  a limited database user caps the damage
```

- example 8. bind the value for room_2
- the SQL text and the value travel separately
- Prisma's normal calls do this
- a string we concatenate does not
- the database user cannot do more than this app needs

```ts
await db.$queryRaw`SELECT id, sessionId FROM items WHERE id = ${id}`;
// id is room_2 when the caller asks for that row
// the value is bound. it is not glued into the sentence
```

- homework
```ts
// 8a  the tagged query binds id
// 8b  a React check is not this fix
// 8c  a limited database user caps the damage
```

- example 9. bind the value for vs_7
- the SQL text and the value travel separately
- Prisma's normal calls do this
- a string we concatenate does not
- the database user cannot do more than this app needs

```ts
await db.$queryRaw`SELECT id, name FROM items WHERE id = ${id}`;
// id is vs_7 when the caller asks for that row
// the value is bound. it is not glued into the sentence
```

- homework
```ts
// 9a  the tagged query binds id
// 9b  a React check is not this fix
// 9c  a limited database user caps the damage
```

- example 10. bind the value for sc_3
- the SQL text and the value travel separately
- Prisma's normal calls do this
- a string we concatenate does not
- the database user cannot do more than this app needs

```ts
await db.$queryRaw`SELECT id, points FROM items WHERE id = ${id}`;
// id is sc_3 when the caller asks for that row
// the value is bound. it is not glued into the sentence
```

- homework
```ts
// 10a  the tagged query binds id
// 10b  a React check is not this fix
// 10c  a limited database user caps the damage
```

- example 11. bind the value for tm_2
- the SQL text and the value travel separately
- Prisma's normal calls do this
- a string we concatenate does not
- the database user cannot do more than this app needs

```ts
await db.$queryRaw`SELECT id, name FROM items WHERE id = ${id}`;
// id is tm_2 when the caller asks for that row
// the value is bound. it is not glued into the sentence
```

- homework
```ts
// 11a  the tagged query binds id
// 11b  a React check is not this fix
// 11c  a limited database user caps the damage
```

- example 12. bind the value for up_6
- the SQL text and the value travel separately
- Prisma's normal calls do this
- a string we concatenate does not
- the database user cannot do more than this app needs

```ts
await db.$queryRaw`SELECT id, key FROM items WHERE id = ${id}`;
// id is up_6 when the caller asks for that row
// the value is bound. it is not glued into the sentence
```

- homework
```ts
// 12a  the tagged query binds id
// 12b  a React check is not this fix
// 12c  a limited database user caps the damage
```

- example 13. bind the value for st_1
- the SQL text and the value travel separately
- Prisma's normal calls do this
- a string we concatenate does not
- the database user cannot do more than this app needs

```ts
await db.$queryRaw`SELECT id, player FROM items WHERE id = ${id}`;
// id is st_1 when the caller asks for that row
// the value is bound. it is not glued into the sentence
```

- homework
```ts
// 13a  the tagged query binds id
// 13b  a React check is not this fix
// 13c  a limited database user caps the damage
```

- example 14. bind the value for n_2
- the SQL text and the value travel separately
- Prisma's normal calls do this
- a string we concatenate does not
- the database user cannot do more than this app needs

```ts
await db.$queryRaw`SELECT id, port FROM items WHERE id = ${id}`;
// id is n_2 when the caller asks for that row
// the value is bound. it is not glued into the sentence
```

- homework
```ts
// 14a  the tagged query binds id
// 14b  a React check is not this fix
// 14c  a limited database user caps the damage
```

- example 15. bind the value for b_3
- the SQL text and the value travel separately
- Prisma's normal calls do this
- a string we concatenate does not
- the database user cannot do more than this app needs

```ts
await db.$queryRaw`SELECT id, round FROM items WHERE id = ${id}`;
// id is b_3 when the caller asks for that row
// the value is bound. it is not glued into the sentence
```

- homework
```ts
// 15a  the tagged query binds id
// 15b  a React check is not this fix
// 15c  a limited database user caps the damage
```

- example 16. bind the value for se_1
- the SQL text and the value travel separately
- Prisma's normal calls do this
- a string we concatenate does not
- the database user cannot do more than this app needs

```ts
await db.$queryRaw`SELECT id, userId FROM items WHERE id = ${id}`;
// id is se_1 when the caller asks for that row
// the value is bound. it is not glued into the sentence
```

- homework
```ts
// 16a  the tagged query binds id
// 16b  a React check is not this fix
// 16c  a limited database user caps the damage
```

- example 17. bind the value for q_1
- the SQL text and the value travel separately
- Prisma's normal calls do this
- a string we concatenate does not
- the database user cannot do more than this app needs

```ts
await db.$queryRaw`SELECT id, name FROM items WHERE id = ${id}`;
// id is q_1 when the caller asks for that row
// the value is bound. it is not glued into the sentence
```

- homework
```ts
// 17a  the tagged query binds id
// 17b  a React check is not this fix
// 17c  a limited database user caps the damage
```

- example 18. bind the value for r_1
- the SQL text and the value travel separately
- Prisma's normal calls do this
- a string we concatenate does not
- the database user cannot do more than this app needs

```ts
await db.$queryRaw`SELECT id, name FROM items WHERE id = ${id}`;
// id is r_1 when the caller asks for that row
// the value is bound. it is not glued into the sentence
```

- homework
```ts
// 18a  the tagged query binds id
// 18b  a React check is not this fix
// 18c  a limited database user caps the damage
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

- example 1. show vesselName as text
- JSX escapes the string Ocean Star
- we do not render raw HTML for a name or a comment
- a content security policy refuses script we did not allow
- a token in localStorage is readable if script runs on our origin

```tsx
<p>{row.vesselName}</p>
// row id pc_12
// the braces are text
```

- homework
```tsx
// 1a  vessel or title Ocean Star goes in braces
// 1b  localStorage plus script on our origin exposes the token
// 1c  the policy is the second net
```

- example 2. show home as text
- JSX escapes the string Ada
- we do not render raw HTML for a name or a comment
- a content security policy refuses script we did not allow
- a token in localStorage is readable if script runs on our origin

```tsx
<p>{row.home}</p>
// row id m_1
// the braces are text
```

- homework
```tsx
// 2a  vessel or title Ada goes in braces
// 2b  localStorage plus script on our origin exposes the token
// 2c  the policy is the second net
```

- example 3. show name as text
- JSX escapes the string Rajshahi Open
- we do not render raw HTML for a name or a comment
- a content security policy refuses script we did not allow
- a token in localStorage is readable if script runs on our origin

```tsx
<p>{row.name}</p>
// row id t_9
// the braces are text
```

- homework
```tsx
// 3a  vessel or title Rajshahi Open goes in braces
// 3b  localStorage plus script on our origin exposes the token
// 3c  the policy is the second net
```

- example 4. show title as text
- JSX escapes the string Episode 1
- we do not render raw HTML for a name or a comment
- a content security policy refuses script we did not allow
- a token in localStorage is readable if script runs on our origin

```tsx
<p>{row.title}</p>
// row id v_4
// the braces are text
```

- homework
```tsx
// 4a  vessel or title Episode 1 goes in braces
// 4b  localStorage plus script on our origin exposes the token
// 4c  the policy is the second net
```

- example 5. show kind as text
- JSX escapes the string NOR
- we do not render raw HTML for a name or a comment
- a content security policy refuses script we did not allow
- a token in localStorage is readable if script runs on our origin

```tsx
<p>{row.kind}</p>
// row id f_2
// the braces are text
```

- homework
```tsx
// 5a  vessel or title NOR goes in braces
// 5b  localStorage plus script on our origin exposes the token
// 5c  the policy is the second net
```

- example 6. show email as text
- JSX escapes the string a@example.com
- we do not render raw HTML for a name or a comment
- a content security policy refuses script we did not allow
- a token in localStorage is readable if script runs on our origin

```tsx
<p>{row.email}</p>
// row id u_3
// the braces are text
```

- homework
```tsx
// 6a  vessel or title a@example.com goes in braces
// 6b  localStorage plus script on our origin exposes the token
// 6c  the policy is the second net
```

- example 7. show eventId as text
- JSX escapes the string evt_1
- we do not render raw HTML for a name or a comment
- a content security policy refuses script we did not allow
- a token in localStorage is readable if script runs on our origin

```tsx
<p>{row.eventId}</p>
// row id pay_8
// the braces are text
```

- homework
```tsx
// 7a  vessel or title evt_1 goes in braces
// 7b  localStorage plus script on our origin exposes the token
// 7c  the policy is the second net
```

- example 8. show sessionId as text
- JSX escapes the string s_9
- we do not render raw HTML for a name or a comment
- a content security policy refuses script we did not allow
- a token in localStorage is readable if script runs on our origin

```tsx
<p>{row.sessionId}</p>
// row id room_2
// the braces are text
```

- homework
```tsx
// 8a  vessel or title s_9 goes in braces
// 8b  localStorage plus script on our origin exposes the token
// 8c  the policy is the second net
```

- example 9. show name as text
- JSX escapes the string North Wind
- we do not render raw HTML for a name or a comment
- a content security policy refuses script we did not allow
- a token in localStorage is readable if script runs on our origin

```tsx
<p>{row.name}</p>
// row id vs_7
// the braces are text
```

- homework
```tsx
// 9a  vessel or title North Wind goes in braces
// 9b  localStorage plus script on our origin exposes the token
// 9c  the policy is the second net
```

- example 10. show points as text
- JSX escapes the string 11
- we do not render raw HTML for a name or a comment
- a content security policy refuses script we did not allow
- a token in localStorage is readable if script runs on our origin

```tsx
<p>{row.points}</p>
// row id sc_3
// the braces are text
```

- homework
```tsx
// 10a  vessel or title 11 goes in braces
// 10b  localStorage plus script on our origin exposes the token
// 10c  the policy is the second net
```

- example 11. show name as text
- JSX escapes the string Blue
- we do not render raw HTML for a name or a comment
- a content security policy refuses script we did not allow
- a token in localStorage is readable if script runs on our origin

```tsx
<p>{row.name}</p>
// row id tm_2
// the braces are text
```

- homework
```tsx
// 11a  vessel or title Blue goes in braces
// 11b  localStorage plus script on our origin exposes the token
// 11c  the policy is the second net
```

- example 12. show key as text
- JSX escapes the string videos/u_1/a.mp4
- we do not render raw HTML for a name or a comment
- a content security policy refuses script we did not allow
- a token in localStorage is readable if script runs on our origin

```tsx
<p>{row.key}</p>
// row id up_6
// the braces are text
```

- homework
```tsx
// 12a  vessel or title videos/u_1/a.mp4 goes in braces
// 12b  localStorage plus script on our origin exposes the token
// 12c  the policy is the second net
```

- example 13. show player as text
- JSX escapes the string player_a
- we do not render raw HTML for a name or a comment
- a content security policy refuses script we did not allow
- a token in localStorage is readable if script runs on our origin

```tsx
<p>{row.player}</p>
// row id st_1
// the braces are text
```

- homework
```tsx
// 13a  vessel or title player_a goes in braces
// 13b  localStorage plus script on our origin exposes the token
// 13c  the policy is the second net
```

- example 14. show port as text
- JSX escapes the string Chattogram
- we do not render raw HTML for a name or a comment
- a content security policy refuses script we did not allow
- a token in localStorage is readable if script runs on our origin

```tsx
<p>{row.port}</p>
// row id n_2
// the braces are text
```

- homework
```tsx
// 14a  vessel or title Chattogram goes in braces
// 14b  localStorage plus script on our origin exposes the token
// 14c  the policy is the second net
```

- example 15. show round as text
- JSX escapes the string semi
- we do not render raw HTML for a name or a comment
- a content security policy refuses script we did not allow
- a token in localStorage is readable if script runs on our origin

```tsx
<p>{row.round}</p>
// row id b_3
// the braces are text
```

- homework
```tsx
// 15a  vessel or title semi goes in braces
// 15b  localStorage plus script on our origin exposes the token
// 15c  the policy is the second net
```

- example 16. show userId as text
- JSX escapes the string u_3
- we do not render raw HTML for a name or a comment
- a content security policy refuses script we did not allow
- a token in localStorage is readable if script runs on our origin

```tsx
<p>{row.userId}</p>
// row id se_1
// the braces are text
```

- homework
```tsx
// 16a  vessel or title u_3 goes in braces
// 16b  localStorage plus script on our origin exposes the token
// 16c  the policy is the second net
```

- example 17. show name as text
- JSX escapes the string laytime
- we do not render raw HTML for a name or a comment
- a content security policy refuses script we did not allow
- a token in localStorage is readable if script runs on our origin

```tsx
<p>{row.name}</p>
// row id q_1
// the braces are text
```

- homework
```tsx
// 17a  vessel or title laytime goes in braces
// 17b  localStorage plus script on our origin exposes the token
// 17c  the policy is the second net
```

- example 18. show name as text
- JSX escapes the string operator
- we do not render raw HTML for a name or a comment
- a content security policy refuses script we did not allow
- a token in localStorage is readable if script runs on our origin

```tsx
<p>{row.name}</p>
// row id r_1
// the braces are text
```

- homework
```tsx
// 18a  vessel or title operator goes in braces
// 18b  localStorage plus script on our origin exposes the token
// 18c  the policy is the second net
```

- example 19. show vesselName as text
- JSX escapes the string Ocean Star
- we do not render raw HTML for a name or a comment
- a content security policy refuses script we did not allow
- a token in localStorage is readable if script runs on our origin

```tsx
<p>{row.vesselName}</p>
// row id pc_12
// the braces are text
```

- homework
```tsx
// 19a  vessel or title Ocean Star goes in braces
// 19b  localStorage plus script on our origin exposes the token
// 19c  the policy is the second net
```

- example 20. show home as text
- JSX escapes the string Ada
- we do not render raw HTML for a name or a comment
- a content security policy refuses script we did not allow
- a token in localStorage is readable if script runs on our origin

```tsx
<p>{row.home}</p>
// row id m_1
// the braces are text
```

- homework
```tsx
// 20a  vessel or title Ada goes in braces
// 20b  localStorage plus script on our origin exposes the token
// 20c  the policy is the second net
```

- example 21. show name as text
- JSX escapes the string Rajshahi Open
- we do not render raw HTML for a name or a comment
- a content security policy refuses script we did not allow
- a token in localStorage is readable if script runs on our origin

```tsx
<p>{row.name}</p>
// row id t_9
// the braces are text
```

- homework
```tsx
// 21a  vessel or title Rajshahi Open goes in braces
// 21b  localStorage plus script on our origin exposes the token
// 21c  the policy is the second net
```

- example 22. show title as text
- JSX escapes the string Episode 1
- we do not render raw HTML for a name or a comment
- a content security policy refuses script we did not allow
- a token in localStorage is readable if script runs on our origin

```tsx
<p>{row.title}</p>
// row id v_4
// the braces are text
```

- homework
```tsx
// 22a  vessel or title Episode 1 goes in braces
// 22b  localStorage plus script on our origin exposes the token
// 22c  the policy is the second net
```

- example 23. show kind as text
- JSX escapes the string NOR
- we do not render raw HTML for a name or a comment
- a content security policy refuses script we did not allow
- a token in localStorage is readable if script runs on our origin

```tsx
<p>{row.kind}</p>
// row id f_2
// the braces are text
```

- homework
```tsx
// 23a  vessel or title NOR goes in braces
// 23b  localStorage plus script on our origin exposes the token
// 23c  the policy is the second net
```

- example 24. show email as text
- JSX escapes the string a@example.com
- we do not render raw HTML for a name or a comment
- a content security policy refuses script we did not allow
- a token in localStorage is readable if script runs on our origin

```tsx
<p>{row.email}</p>
// row id u_3
// the braces are text
```

- homework
```tsx
// 24a  vessel or title a@example.com goes in braces
// 24b  localStorage plus script on our origin exposes the token
// 24c  the policy is the second net
```

- example 25. show eventId as text
- JSX escapes the string evt_1
- we do not render raw HTML for a name or a comment
- a content security policy refuses script we did not allow
- a token in localStorage is readable if script runs on our origin

```tsx
<p>{row.eventId}</p>
// row id pay_8
// the braces are text
```

- homework
```tsx
// 25a  vessel or title evt_1 goes in braces
// 25b  localStorage plus script on our origin exposes the token
// 25c  the policy is the second net
```

- example 26. show sessionId as text
- JSX escapes the string s_9
- we do not render raw HTML for a name or a comment
- a content security policy refuses script we did not allow
- a token in localStorage is readable if script runs on our origin

```tsx
<p>{row.sessionId}</p>
// row id room_2
// the braces are text
```

- homework
```tsx
// 26a  vessel or title s_9 goes in braces
// 26b  localStorage plus script on our origin exposes the token
// 26c  the policy is the second net
```

- example 27. show name as text
- JSX escapes the string North Wind
- we do not render raw HTML for a name or a comment
- a content security policy refuses script we did not allow
- a token in localStorage is readable if script runs on our origin

```tsx
<p>{row.name}</p>
// row id vs_7
// the braces are text
```

- homework
```tsx
// 27a  vessel or title North Wind goes in braces
// 27b  localStorage plus script on our origin exposes the token
// 27c  the policy is the second net
```

- example 28. show points as text
- JSX escapes the string 11
- we do not render raw HTML for a name or a comment
- a content security policy refuses script we did not allow
- a token in localStorage is readable if script runs on our origin

```tsx
<p>{row.points}</p>
// row id sc_3
// the braces are text
```

- homework
```tsx
// 28a  vessel or title 11 goes in braces
// 28b  localStorage plus script on our origin exposes the token
// 28c  the policy is the second net
```

- example 29. show name as text
- JSX escapes the string Blue
- we do not render raw HTML for a name or a comment
- a content security policy refuses script we did not allow
- a token in localStorage is readable if script runs on our origin

```tsx
<p>{row.name}</p>
// row id tm_2
// the braces are text
```

- homework
```tsx
// 29a  vessel or title Blue goes in braces
// 29b  localStorage plus script on our origin exposes the token
// 29c  the policy is the second net
```

- example 30. show key as text
- JSX escapes the string videos/u_1/a.mp4
- we do not render raw HTML for a name or a comment
- a content security policy refuses script we did not allow
- a token in localStorage is readable if script runs on our origin

```tsx
<p>{row.key}</p>
// row id up_6
// the braces are text
```

- homework
```tsx
// 30a  vessel or title videos/u_1/a.mp4 goes in braces
// 30b  localStorage plus script on our origin exposes the token
// 30c  the policy is the second net
```

- example 31. show player as text
- JSX escapes the string player_a
- we do not render raw HTML for a name or a comment
- a content security policy refuses script we did not allow
- a token in localStorage is readable if script runs on our origin

```tsx
<p>{row.player}</p>
// row id st_1
// the braces are text
```

- homework
```tsx
// 31a  vessel or title player_a goes in braces
// 31b  localStorage plus script on our origin exposes the token
// 31c  the policy is the second net
```

- example 32. show port as text
- JSX escapes the string Chattogram
- we do not render raw HTML for a name or a comment
- a content security policy refuses script we did not allow
- a token in localStorage is readable if script runs on our origin

```tsx
<p>{row.port}</p>
// row id n_2
// the braces are text
```

- homework
```tsx
// 32a  vessel or title Chattogram goes in braces
// 32b  localStorage plus script on our origin exposes the token
// 32c  the policy is the second net
```

- example 33. show round as text
- JSX escapes the string semi
- we do not render raw HTML for a name or a comment
- a content security policy refuses script we did not allow
- a token in localStorage is readable if script runs on our origin

```tsx
<p>{row.round}</p>
// row id b_3
// the braces are text
```

- homework
```tsx
// 33a  vessel or title semi goes in braces
// 33b  localStorage plus script on our origin exposes the token
// 33c  the policy is the second net
```

- example 34. show userId as text
- JSX escapes the string u_3
- we do not render raw HTML for a name or a comment
- a content security policy refuses script we did not allow
- a token in localStorage is readable if script runs on our origin

```tsx
<p>{row.userId}</p>
// row id se_1
// the braces are text
```

- homework
```tsx
// 34a  vessel or title u_3 goes in braces
// 34b  localStorage plus script on our origin exposes the token
// 34c  the policy is the second net
```

- example 35. show name as text
- JSX escapes the string laytime
- we do not render raw HTML for a name or a comment
- a content security policy refuses script we did not allow
- a token in localStorage is readable if script runs on our origin

```tsx
<p>{row.name}</p>
// row id q_1
// the braces are text
```

- homework
```tsx
// 35a  vessel or title laytime goes in braces
// 35b  localStorage plus script on our origin exposes the token
// 35c  the policy is the second net
```

- example 36. show name as text
- JSX escapes the string operator
- we do not render raw HTML for a name or a comment
- a content security policy refuses script we did not allow
- a token in localStorage is readable if script runs on our origin

```tsx
<p>{row.name}</p>
// row id r_1
// the braces are text
```

- homework
```tsx
// 36a  vessel or title operator goes in braces
// 36b  localStorage plus script on our origin exposes the token
// 36c  the policy is the second net
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

- example 1. cookie flags and a CORS origin for port-calls
- SameSite and a CSRF token if the session is a cookie
- a bearer header is not attached by a foreign form
- allow the real web origin. do not combine a star with credentials
- CORS is not the role check on pc_12

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
Access-Control-Allow-Origin: https://vms.arrobin.com
Access-Control-Allow-Credentials: true
```

- homework
```http
# 1a  three cookie flags
# 1b  add CSRF in the same change as the cookie
# 1c  a non-browser ignores CORS. the guard still checks pc_12
```

- example 2. cookie flags and a CORS origin for matches
- SameSite and a CSRF token if the session is a cookie
- a bearer header is not attached by a foreign form
- allow the real web origin. do not combine a star with credentials
- CORS is not the role check on m_1

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
Access-Control-Allow-Origin: https://vms.arrobin.com
Access-Control-Allow-Credentials: true
```

- homework
```http
# 2a  three cookie flags
# 2b  add CSRF in the same change as the cookie
# 2c  a non-browser ignores CORS. the guard still checks m_1
```

- example 3. cookie flags and a CORS origin for tournaments
- SameSite and a CSRF token if the session is a cookie
- a bearer header is not attached by a foreign form
- allow the real web origin. do not combine a star with credentials
- CORS is not the role check on t_9

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
Access-Control-Allow-Origin: https://vms.arrobin.com
Access-Control-Allow-Credentials: true
```

- homework
```http
# 3a  three cookie flags
# 3b  add CSRF in the same change as the cookie
# 3c  a non-browser ignores CORS. the guard still checks t_9
```

- example 4. cookie flags and a CORS origin for videos
- SameSite and a CSRF token if the session is a cookie
- a bearer header is not attached by a foreign form
- allow the real web origin. do not combine a star with credentials
- CORS is not the role check on v_4

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
Access-Control-Allow-Origin: https://vms.arrobin.com
Access-Control-Allow-Credentials: true
```

- homework
```http
# 4a  three cookie flags
# 4b  add CSRF in the same change as the cookie
# 4c  a non-browser ignores CORS. the guard still checks v_4
```

- example 5. cookie flags and a CORS origin for facts
- SameSite and a CSRF token if the session is a cookie
- a bearer header is not attached by a foreign form
- allow the real web origin. do not combine a star with credentials
- CORS is not the role check on f_2

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
Access-Control-Allow-Origin: https://vms.arrobin.com
Access-Control-Allow-Credentials: true
```

- homework
```http
# 5a  three cookie flags
# 5b  add CSRF in the same change as the cookie
# 5c  a non-browser ignores CORS. the guard still checks f_2
```

- example 6. cookie flags and a CORS origin for users
- SameSite and a CSRF token if the session is a cookie
- a bearer header is not attached by a foreign form
- allow the real web origin. do not combine a star with credentials
- CORS is not the role check on u_3

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
Access-Control-Allow-Origin: https://vms.arrobin.com
Access-Control-Allow-Credentials: true
```

- homework
```http
# 6a  three cookie flags
# 6b  add CSRF in the same change as the cookie
# 6c  a non-browser ignores CORS. the guard still checks u_3
```

- example 7. cookie flags and a CORS origin for payments
- SameSite and a CSRF token if the session is a cookie
- a bearer header is not attached by a foreign form
- allow the real web origin. do not combine a star with credentials
- CORS is not the role check on pay_8

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
Access-Control-Allow-Origin: https://vms.arrobin.com
Access-Control-Allow-Credentials: true
```

- homework
```http
# 7a  three cookie flags
# 7b  add CSRF in the same change as the cookie
# 7c  a non-browser ignores CORS. the guard still checks pay_8
```

- example 8. cookie flags and a CORS origin for rooms
- SameSite and a CSRF token if the session is a cookie
- a bearer header is not attached by a foreign form
- allow the real web origin. do not combine a star with credentials
- CORS is not the role check on room_2

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
Access-Control-Allow-Origin: https://vms.arrobin.com
Access-Control-Allow-Credentials: true
```

- homework
```http
# 8a  three cookie flags
# 8b  add CSRF in the same change as the cookie
# 8c  a non-browser ignores CORS. the guard still checks room_2
```

- example 9. cookie flags and a CORS origin for vessels
- SameSite and a CSRF token if the session is a cookie
- a bearer header is not attached by a foreign form
- allow the real web origin. do not combine a star with credentials
- CORS is not the role check on vs_7

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
Access-Control-Allow-Origin: https://vms.arrobin.com
Access-Control-Allow-Credentials: true
```

- homework
```http
# 9a  three cookie flags
# 9b  add CSRF in the same change as the cookie
# 9c  a non-browser ignores CORS. the guard still checks vs_7
```

- example 10. cookie flags and a CORS origin for scores
- SameSite and a CSRF token if the session is a cookie
- a bearer header is not attached by a foreign form
- allow the real web origin. do not combine a star with credentials
- CORS is not the role check on sc_3

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
Access-Control-Allow-Origin: https://vms.arrobin.com
Access-Control-Allow-Credentials: true
```

- homework
```http
# 10a  three cookie flags
# 10b  add CSRF in the same change as the cookie
# 10c  a non-browser ignores CORS. the guard still checks sc_3
```

- example 11. cookie flags and a CORS origin for teams
- SameSite and a CSRF token if the session is a cookie
- a bearer header is not attached by a foreign form
- allow the real web origin. do not combine a star with credentials
- CORS is not the role check on tm_2

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
Access-Control-Allow-Origin: https://vms.arrobin.com
Access-Control-Allow-Credentials: true
```

- homework
```http
# 11a  three cookie flags
# 11b  add CSRF in the same change as the cookie
# 11c  a non-browser ignores CORS. the guard still checks tm_2
```

- example 12. cookie flags and a CORS origin for uploads
- SameSite and a CSRF token if the session is a cookie
- a bearer header is not attached by a foreign form
- allow the real web origin. do not combine a star with credentials
- CORS is not the role check on up_6

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
Access-Control-Allow-Origin: https://vms.arrobin.com
Access-Control-Allow-Credentials: true
```

- homework
```http
# 12a  three cookie flags
# 12b  add CSRF in the same change as the cookie
# 12c  a non-browser ignores CORS. the guard still checks up_6
```

- example 13. cookie flags and a CORS origin for standings
- SameSite and a CSRF token if the session is a cookie
- a bearer header is not attached by a foreign form
- allow the real web origin. do not combine a star with credentials
- CORS is not the role check on st_1

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
Access-Control-Allow-Origin: https://vms.arrobin.com
Access-Control-Allow-Credentials: true
```

- homework
```http
# 13a  three cookie flags
# 13b  add CSRF in the same change as the cookie
# 13c  a non-browser ignores CORS. the guard still checks st_1
```

- example 14. cookie flags and a CORS origin for notices
- SameSite and a CSRF token if the session is a cookie
- a bearer header is not attached by a foreign form
- allow the real web origin. do not combine a star with credentials
- CORS is not the role check on n_2

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
Access-Control-Allow-Origin: https://vms.arrobin.com
Access-Control-Allow-Credentials: true
```

- homework
```http
# 14a  three cookie flags
# 14b  add CSRF in the same change as the cookie
# 14c  a non-browser ignores CORS. the guard still checks n_2
```

- example 15. cookie flags and a CORS origin for brackets
- SameSite and a CSRF token if the session is a cookie
- a bearer header is not attached by a foreign form
- allow the real web origin. do not combine a star with credentials
- CORS is not the role check on b_3

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
Access-Control-Allow-Origin: https://vms.arrobin.com
Access-Control-Allow-Credentials: true
```

- homework
```http
# 15a  three cookie flags
# 15b  add CSRF in the same change as the cookie
# 15c  a non-browser ignores CORS. the guard still checks b_3
```

- example 16. cookie flags and a CORS origin for sessions
- SameSite and a CSRF token if the session is a cookie
- a bearer header is not attached by a foreign form
- allow the real web origin. do not combine a star with credentials
- CORS is not the role check on se_1

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
Access-Control-Allow-Origin: https://vms.arrobin.com
Access-Control-Allow-Credentials: true
```

- homework
```http
# 16a  three cookie flags
# 16b  add CSRF in the same change as the cookie
# 16c  a non-browser ignores CORS. the guard still checks se_1
```

- example 17. cookie flags and a CORS origin for queues
- SameSite and a CSRF token if the session is a cookie
- a bearer header is not attached by a foreign form
- allow the real web origin. do not combine a star with credentials
- CORS is not the role check on q_1

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
Access-Control-Allow-Origin: https://vms.arrobin.com
Access-Control-Allow-Credentials: true
```

- homework
```http
# 17a  three cookie flags
# 17b  add CSRF in the same change as the cookie
# 17c  a non-browser ignores CORS. the guard still checks q_1
```

- example 18. cookie flags and a CORS origin for roles
- SameSite and a CSRF token if the session is a cookie
- a bearer header is not attached by a foreign form
- allow the real web origin. do not combine a star with credentials
- CORS is not the role check on r_1

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
Access-Control-Allow-Origin: https://vms.arrobin.com
Access-Control-Allow-Credentials: true
```

- homework
```http
# 18a  three cookie flags
# 18b  add CSRF in the same change as the cookie
# 18c  a non-browser ignores CORS. the guard still checks r_1
```

- example 19. cookie flags and a CORS origin for port-calls
- SameSite and a CSRF token if the session is a cookie
- a bearer header is not attached by a foreign form
- allow the real web origin. do not combine a star with credentials
- CORS is not the role check on pc_12

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
Access-Control-Allow-Origin: https://vms.arrobin.com
Access-Control-Allow-Credentials: true
```

- homework
```http
# 19a  three cookie flags
# 19b  add CSRF in the same change as the cookie
# 19c  a non-browser ignores CORS. the guard still checks pc_12
```

- example 20. cookie flags and a CORS origin for matches
- SameSite and a CSRF token if the session is a cookie
- a bearer header is not attached by a foreign form
- allow the real web origin. do not combine a star with credentials
- CORS is not the role check on m_1

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
Access-Control-Allow-Origin: https://vms.arrobin.com
Access-Control-Allow-Credentials: true
```

- homework
```http
# 20a  three cookie flags
# 20b  add CSRF in the same change as the cookie
# 20c  a non-browser ignores CORS. the guard still checks m_1
```

- example 21. cookie flags and a CORS origin for tournaments
- SameSite and a CSRF token if the session is a cookie
- a bearer header is not attached by a foreign form
- allow the real web origin. do not combine a star with credentials
- CORS is not the role check on t_9

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
Access-Control-Allow-Origin: https://vms.arrobin.com
Access-Control-Allow-Credentials: true
```

- homework
```http
# 21a  three cookie flags
# 21b  add CSRF in the same change as the cookie
# 21c  a non-browser ignores CORS. the guard still checks t_9
```

- example 22. cookie flags and a CORS origin for videos
- SameSite and a CSRF token if the session is a cookie
- a bearer header is not attached by a foreign form
- allow the real web origin. do not combine a star with credentials
- CORS is not the role check on v_4

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
Access-Control-Allow-Origin: https://vms.arrobin.com
Access-Control-Allow-Credentials: true
```

- homework
```http
# 22a  three cookie flags
# 22b  add CSRF in the same change as the cookie
# 22c  a non-browser ignores CORS. the guard still checks v_4
```

- example 23. cookie flags and a CORS origin for facts
- SameSite and a CSRF token if the session is a cookie
- a bearer header is not attached by a foreign form
- allow the real web origin. do not combine a star with credentials
- CORS is not the role check on f_2

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
Access-Control-Allow-Origin: https://vms.arrobin.com
Access-Control-Allow-Credentials: true
```

- homework
```http
# 23a  three cookie flags
# 23b  add CSRF in the same change as the cookie
# 23c  a non-browser ignores CORS. the guard still checks f_2
```

- example 24. cookie flags and a CORS origin for users
- SameSite and a CSRF token if the session is a cookie
- a bearer header is not attached by a foreign form
- allow the real web origin. do not combine a star with credentials
- CORS is not the role check on u_3

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
Access-Control-Allow-Origin: https://vms.arrobin.com
Access-Control-Allow-Credentials: true
```

- homework
```http
# 24a  three cookie flags
# 24b  add CSRF in the same change as the cookie
# 24c  a non-browser ignores CORS. the guard still checks u_3
```

- example 25. cookie flags and a CORS origin for payments
- SameSite and a CSRF token if the session is a cookie
- a bearer header is not attached by a foreign form
- allow the real web origin. do not combine a star with credentials
- CORS is not the role check on pay_8

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
Access-Control-Allow-Origin: https://vms.arrobin.com
Access-Control-Allow-Credentials: true
```

- homework
```http
# 25a  three cookie flags
# 25b  add CSRF in the same change as the cookie
# 25c  a non-browser ignores CORS. the guard still checks pay_8
```

- example 26. cookie flags and a CORS origin for rooms
- SameSite and a CSRF token if the session is a cookie
- a bearer header is not attached by a foreign form
- allow the real web origin. do not combine a star with credentials
- CORS is not the role check on room_2

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
Access-Control-Allow-Origin: https://vms.arrobin.com
Access-Control-Allow-Credentials: true
```

- homework
```http
# 26a  three cookie flags
# 26b  add CSRF in the same change as the cookie
# 26c  a non-browser ignores CORS. the guard still checks room_2
```

- example 27. cookie flags and a CORS origin for vessels
- SameSite and a CSRF token if the session is a cookie
- a bearer header is not attached by a foreign form
- allow the real web origin. do not combine a star with credentials
- CORS is not the role check on vs_7

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
Access-Control-Allow-Origin: https://vms.arrobin.com
Access-Control-Allow-Credentials: true
```

- homework
```http
# 27a  three cookie flags
# 27b  add CSRF in the same change as the cookie
# 27c  a non-browser ignores CORS. the guard still checks vs_7
```

- example 28. cookie flags and a CORS origin for scores
- SameSite and a CSRF token if the session is a cookie
- a bearer header is not attached by a foreign form
- allow the real web origin. do not combine a star with credentials
- CORS is not the role check on sc_3

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
Access-Control-Allow-Origin: https://vms.arrobin.com
Access-Control-Allow-Credentials: true
```

- homework
```http
# 28a  three cookie flags
# 28b  add CSRF in the same change as the cookie
# 28c  a non-browser ignores CORS. the guard still checks sc_3
```

- example 29. cookie flags and a CORS origin for teams
- SameSite and a CSRF token if the session is a cookie
- a bearer header is not attached by a foreign form
- allow the real web origin. do not combine a star with credentials
- CORS is not the role check on tm_2

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
Access-Control-Allow-Origin: https://vms.arrobin.com
Access-Control-Allow-Credentials: true
```

- homework
```http
# 29a  three cookie flags
# 29b  add CSRF in the same change as the cookie
# 29c  a non-browser ignores CORS. the guard still checks tm_2
```

- example 30. cookie flags and a CORS origin for uploads
- SameSite and a CSRF token if the session is a cookie
- a bearer header is not attached by a foreign form
- allow the real web origin. do not combine a star with credentials
- CORS is not the role check on up_6

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
Access-Control-Allow-Origin: https://vms.arrobin.com
Access-Control-Allow-Credentials: true
```

- homework
```http
# 30a  three cookie flags
# 30b  add CSRF in the same change as the cookie
# 30c  a non-browser ignores CORS. the guard still checks up_6
```

- example 31. cookie flags and a CORS origin for standings
- SameSite and a CSRF token if the session is a cookie
- a bearer header is not attached by a foreign form
- allow the real web origin. do not combine a star with credentials
- CORS is not the role check on st_1

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
Access-Control-Allow-Origin: https://vms.arrobin.com
Access-Control-Allow-Credentials: true
```

- homework
```http
# 31a  three cookie flags
# 31b  add CSRF in the same change as the cookie
# 31c  a non-browser ignores CORS. the guard still checks st_1
```

- example 32. cookie flags and a CORS origin for notices
- SameSite and a CSRF token if the session is a cookie
- a bearer header is not attached by a foreign form
- allow the real web origin. do not combine a star with credentials
- CORS is not the role check on n_2

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
Access-Control-Allow-Origin: https://vms.arrobin.com
Access-Control-Allow-Credentials: true
```

- homework
```http
# 32a  three cookie flags
# 32b  add CSRF in the same change as the cookie
# 32c  a non-browser ignores CORS. the guard still checks n_2
```

- example 33. cookie flags and a CORS origin for brackets
- SameSite and a CSRF token if the session is a cookie
- a bearer header is not attached by a foreign form
- allow the real web origin. do not combine a star with credentials
- CORS is not the role check on b_3

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
Access-Control-Allow-Origin: https://vms.arrobin.com
Access-Control-Allow-Credentials: true
```

- homework
```http
# 33a  three cookie flags
# 33b  add CSRF in the same change as the cookie
# 33c  a non-browser ignores CORS. the guard still checks b_3
```

- example 34. cookie flags and a CORS origin for sessions
- SameSite and a CSRF token if the session is a cookie
- a bearer header is not attached by a foreign form
- allow the real web origin. do not combine a star with credentials
- CORS is not the role check on se_1

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
Access-Control-Allow-Origin: https://vms.arrobin.com
Access-Control-Allow-Credentials: true
```

- homework
```http
# 34a  three cookie flags
# 34b  add CSRF in the same change as the cookie
# 34c  a non-browser ignores CORS. the guard still checks se_1
```

- example 35. cookie flags and a CORS origin for queues
- SameSite and a CSRF token if the session is a cookie
- a bearer header is not attached by a foreign form
- allow the real web origin. do not combine a star with credentials
- CORS is not the role check on q_1

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
Access-Control-Allow-Origin: https://vms.arrobin.com
Access-Control-Allow-Credentials: true
```

- homework
```http
# 35a  three cookie flags
# 35b  add CSRF in the same change as the cookie
# 35c  a non-browser ignores CORS. the guard still checks q_1
```

- example 36. cookie flags and a CORS origin for roles
- SameSite and a CSRF token if the session is a cookie
- a bearer header is not attached by a foreign form
- allow the real web origin. do not combine a star with credentials
- CORS is not the role check on r_1

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
Access-Control-Allow-Origin: https://vms.arrobin.com
Access-Control-Allow-Credentials: true
```

- homework
```http
# 36a  three cookie flags
# 36b  add CSRF in the same change as the cookie
# 36c  a non-browser ignores CORS. the guard still checks r_1
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

- example 1. do not fetch an arbitrary URL for pc_12
- allow https only
- allow hosts we named
- refuse internal addresses
- do not follow a redirect onto a private address
- the safe design uploads the bytes

```text
upload bytes for pc_12
store the key
do not accept a caller-supplied URL for this feature
vesselName is Ocean Star, a label, not an address to fetch
```

- homework
```text
# 1a  the server would be the one that connects, so we do not give it a blank URL
# 1b  allowlist of scheme and host
# 1c  Anemi takes an upload for the file, not a URL from the form
```

- example 2. do not fetch an arbitrary URL for m_1
- allow https only
- allow hosts we named
- refuse internal addresses
- do not follow a redirect onto a private address
- the safe design uploads the bytes

```text
upload bytes for m_1
store the key
do not accept a caller-supplied URL for this feature
home is Ada, a label, not an address to fetch
```

- homework
```text
# 2a  the server would be the one that connects, so we do not give it a blank URL
# 2b  allowlist of scheme and host
# 2c  Anemi takes an upload for the file, not a URL from the form
```

- example 3. do not fetch an arbitrary URL for t_9
- allow https only
- allow hosts we named
- refuse internal addresses
- do not follow a redirect onto a private address
- the safe design uploads the bytes

```text
upload bytes for t_9
store the key
do not accept a caller-supplied URL for this feature
name is Rajshahi Open, a label, not an address to fetch
```

- homework
```text
# 3a  the server would be the one that connects, so we do not give it a blank URL
# 3b  allowlist of scheme and host
# 3c  Anemi takes an upload for the file, not a URL from the form
```

- example 4. do not fetch an arbitrary URL for v_4
- allow https only
- allow hosts we named
- refuse internal addresses
- do not follow a redirect onto a private address
- the safe design uploads the bytes

```text
upload bytes for v_4
store the key
do not accept a caller-supplied URL for this feature
title is Episode 1, a label, not an address to fetch
```

- homework
```text
# 4a  the server would be the one that connects, so we do not give it a blank URL
# 4b  allowlist of scheme and host
# 4c  Anemi takes an upload for the file, not a URL from the form
```

- example 5. do not fetch an arbitrary URL for f_2
- allow https only
- allow hosts we named
- refuse internal addresses
- do not follow a redirect onto a private address
- the safe design uploads the bytes

```text
upload bytes for f_2
store the key
do not accept a caller-supplied URL for this feature
kind is NOR, a label, not an address to fetch
```

- homework
```text
# 5a  the server would be the one that connects, so we do not give it a blank URL
# 5b  allowlist of scheme and host
# 5c  Anemi takes an upload for the file, not a URL from the form
```

- example 6. do not fetch an arbitrary URL for u_3
- allow https only
- allow hosts we named
- refuse internal addresses
- do not follow a redirect onto a private address
- the safe design uploads the bytes

```text
upload bytes for u_3
store the key
do not accept a caller-supplied URL for this feature
email is a@example.com, a label, not an address to fetch
```

- homework
```text
# 6a  the server would be the one that connects, so we do not give it a blank URL
# 6b  allowlist of scheme and host
# 6c  Anemi takes an upload for the file, not a URL from the form
```

- example 7. do not fetch an arbitrary URL for pay_8
- allow https only
- allow hosts we named
- refuse internal addresses
- do not follow a redirect onto a private address
- the safe design uploads the bytes

```text
upload bytes for pay_8
store the key
do not accept a caller-supplied URL for this feature
eventId is evt_1, a label, not an address to fetch
```

- homework
```text
# 7a  the server would be the one that connects, so we do not give it a blank URL
# 7b  allowlist of scheme and host
# 7c  Anemi takes an upload for the file, not a URL from the form
```

- example 8. do not fetch an arbitrary URL for room_2
- allow https only
- allow hosts we named
- refuse internal addresses
- do not follow a redirect onto a private address
- the safe design uploads the bytes

```text
upload bytes for room_2
store the key
do not accept a caller-supplied URL for this feature
sessionId is s_9, a label, not an address to fetch
```

- homework
```text
# 8a  the server would be the one that connects, so we do not give it a blank URL
# 8b  allowlist of scheme and host
# 8c  Anemi takes an upload for the file, not a URL from the form
```

- example 9. do not fetch an arbitrary URL for vs_7
- allow https only
- allow hosts we named
- refuse internal addresses
- do not follow a redirect onto a private address
- the safe design uploads the bytes

```text
upload bytes for vs_7
store the key
do not accept a caller-supplied URL for this feature
name is North Wind, a label, not an address to fetch
```

- homework
```text
# 9a  the server would be the one that connects, so we do not give it a blank URL
# 9b  allowlist of scheme and host
# 9c  Anemi takes an upload for the file, not a URL from the form
```

- example 10. do not fetch an arbitrary URL for sc_3
- allow https only
- allow hosts we named
- refuse internal addresses
- do not follow a redirect onto a private address
- the safe design uploads the bytes

```text
upload bytes for sc_3
store the key
do not accept a caller-supplied URL for this feature
points is 11, a label, not an address to fetch
```

- homework
```text
# 10a  the server would be the one that connects, so we do not give it a blank URL
# 10b  allowlist of scheme and host
# 10c  Anemi takes an upload for the file, not a URL from the form
```

- example 11. do not fetch an arbitrary URL for tm_2
- allow https only
- allow hosts we named
- refuse internal addresses
- do not follow a redirect onto a private address
- the safe design uploads the bytes

```text
upload bytes for tm_2
store the key
do not accept a caller-supplied URL for this feature
name is Blue, a label, not an address to fetch
```

- homework
```text
# 11a  the server would be the one that connects, so we do not give it a blank URL
# 11b  allowlist of scheme and host
# 11c  Anemi takes an upload for the file, not a URL from the form
```

- example 12. do not fetch an arbitrary URL for up_6
- allow https only
- allow hosts we named
- refuse internal addresses
- do not follow a redirect onto a private address
- the safe design uploads the bytes

```text
upload bytes for up_6
store the key
do not accept a caller-supplied URL for this feature
key is videos/u_1/a.mp4, a label, not an address to fetch
```

- homework
```text
# 12a  the server would be the one that connects, so we do not give it a blank URL
# 12b  allowlist of scheme and host
# 12c  Anemi takes an upload for the file, not a URL from the form
```

- example 13. do not fetch an arbitrary URL for st_1
- allow https only
- allow hosts we named
- refuse internal addresses
- do not follow a redirect onto a private address
- the safe design uploads the bytes

```text
upload bytes for st_1
store the key
do not accept a caller-supplied URL for this feature
player is player_a, a label, not an address to fetch
```

- homework
```text
# 13a  the server would be the one that connects, so we do not give it a blank URL
# 13b  allowlist of scheme and host
# 13c  Anemi takes an upload for the file, not a URL from the form
```

- example 14. do not fetch an arbitrary URL for n_2
- allow https only
- allow hosts we named
- refuse internal addresses
- do not follow a redirect onto a private address
- the safe design uploads the bytes

```text
upload bytes for n_2
store the key
do not accept a caller-supplied URL for this feature
port is Chattogram, a label, not an address to fetch
```

- homework
```text
# 14a  the server would be the one that connects, so we do not give it a blank URL
# 14b  allowlist of scheme and host
# 14c  Anemi takes an upload for the file, not a URL from the form
```

- example 15. do not fetch an arbitrary URL for b_3
- allow https only
- allow hosts we named
- refuse internal addresses
- do not follow a redirect onto a private address
- the safe design uploads the bytes

```text
upload bytes for b_3
store the key
do not accept a caller-supplied URL for this feature
round is semi, a label, not an address to fetch
```

- homework
```text
# 15a  the server would be the one that connects, so we do not give it a blank URL
# 15b  allowlist of scheme and host
# 15c  Anemi takes an upload for the file, not a URL from the form
```

- example 16. do not fetch an arbitrary URL for se_1
- allow https only
- allow hosts we named
- refuse internal addresses
- do not follow a redirect onto a private address
- the safe design uploads the bytes

```text
upload bytes for se_1
store the key
do not accept a caller-supplied URL for this feature
userId is u_3, a label, not an address to fetch
```

- homework
```text
# 16a  the server would be the one that connects, so we do not give it a blank URL
# 16b  allowlist of scheme and host
# 16c  Anemi takes an upload for the file, not a URL from the form
```

- example 17. do not fetch an arbitrary URL for q_1
- allow https only
- allow hosts we named
- refuse internal addresses
- do not follow a redirect onto a private address
- the safe design uploads the bytes

```text
upload bytes for q_1
store the key
do not accept a caller-supplied URL for this feature
name is laytime, a label, not an address to fetch
```

- homework
```text
# 17a  the server would be the one that connects, so we do not give it a blank URL
# 17b  allowlist of scheme and host
# 17c  Anemi takes an upload for the file, not a URL from the form
```

- example 18. do not fetch an arbitrary URL for r_1
- allow https only
- allow hosts we named
- refuse internal addresses
- do not follow a redirect onto a private address
- the safe design uploads the bytes

```text
upload bytes for r_1
store the key
do not accept a caller-supplied URL for this feature
name is operator, a label, not an address to fetch
```

- homework
```text
# 18a  the server would be the one that connects, so we do not give it a blank URL
# 18b  allowlist of scheme and host
# 18c  Anemi takes an upload for the file, not a URL from the form
```

- example 19. do not fetch an arbitrary URL for pc_12
- allow https only
- allow hosts we named
- refuse internal addresses
- do not follow a redirect onto a private address
- the safe design uploads the bytes

```text
upload bytes for pc_12
store the key
do not accept a caller-supplied URL for this feature
vesselName is Ocean Star, a label, not an address to fetch
```

- homework
```text
# 19a  the server would be the one that connects, so we do not give it a blank URL
# 19b  allowlist of scheme and host
# 19c  Anemi takes an upload for the file, not a URL from the form
```

- example 20. do not fetch an arbitrary URL for m_1
- allow https only
- allow hosts we named
- refuse internal addresses
- do not follow a redirect onto a private address
- the safe design uploads the bytes

```text
upload bytes for m_1
store the key
do not accept a caller-supplied URL for this feature
home is Ada, a label, not an address to fetch
```

- homework
```text
# 20a  the server would be the one that connects, so we do not give it a blank URL
# 20b  allowlist of scheme and host
# 20c  Anemi takes an upload for the file, not a URL from the form
```

- example 21. do not fetch an arbitrary URL for t_9
- allow https only
- allow hosts we named
- refuse internal addresses
- do not follow a redirect onto a private address
- the safe design uploads the bytes

```text
upload bytes for t_9
store the key
do not accept a caller-supplied URL for this feature
name is Rajshahi Open, a label, not an address to fetch
```

- homework
```text
# 21a  the server would be the one that connects, so we do not give it a blank URL
# 21b  allowlist of scheme and host
# 21c  Anemi takes an upload for the file, not a URL from the form
```

- example 22. do not fetch an arbitrary URL for v_4
- allow https only
- allow hosts we named
- refuse internal addresses
- do not follow a redirect onto a private address
- the safe design uploads the bytes

```text
upload bytes for v_4
store the key
do not accept a caller-supplied URL for this feature
title is Episode 1, a label, not an address to fetch
```

- homework
```text
# 22a  the server would be the one that connects, so we do not give it a blank URL
# 22b  allowlist of scheme and host
# 22c  Anemi takes an upload for the file, not a URL from the form
```

- example 23. do not fetch an arbitrary URL for f_2
- allow https only
- allow hosts we named
- refuse internal addresses
- do not follow a redirect onto a private address
- the safe design uploads the bytes

```text
upload bytes for f_2
store the key
do not accept a caller-supplied URL for this feature
kind is NOR, a label, not an address to fetch
```

- homework
```text
# 23a  the server would be the one that connects, so we do not give it a blank URL
# 23b  allowlist of scheme and host
# 23c  Anemi takes an upload for the file, not a URL from the form
```

- example 24. do not fetch an arbitrary URL for u_3
- allow https only
- allow hosts we named
- refuse internal addresses
- do not follow a redirect onto a private address
- the safe design uploads the bytes

```text
upload bytes for u_3
store the key
do not accept a caller-supplied URL for this feature
email is a@example.com, a label, not an address to fetch
```

- homework
```text
# 24a  the server would be the one that connects, so we do not give it a blank URL
# 24b  allowlist of scheme and host
# 24c  Anemi takes an upload for the file, not a URL from the form
```

- example 25. do not fetch an arbitrary URL for pay_8
- allow https only
- allow hosts we named
- refuse internal addresses
- do not follow a redirect onto a private address
- the safe design uploads the bytes

```text
upload bytes for pay_8
store the key
do not accept a caller-supplied URL for this feature
eventId is evt_1, a label, not an address to fetch
```

- homework
```text
# 25a  the server would be the one that connects, so we do not give it a blank URL
# 25b  allowlist of scheme and host
# 25c  Anemi takes an upload for the file, not a URL from the form
```

- example 26. do not fetch an arbitrary URL for room_2
- allow https only
- allow hosts we named
- refuse internal addresses
- do not follow a redirect onto a private address
- the safe design uploads the bytes

```text
upload bytes for room_2
store the key
do not accept a caller-supplied URL for this feature
sessionId is s_9, a label, not an address to fetch
```

- homework
```text
# 26a  the server would be the one that connects, so we do not give it a blank URL
# 26b  allowlist of scheme and host
# 26c  Anemi takes an upload for the file, not a URL from the form
```

- example 27. do not fetch an arbitrary URL for vs_7
- allow https only
- allow hosts we named
- refuse internal addresses
- do not follow a redirect onto a private address
- the safe design uploads the bytes

```text
upload bytes for vs_7
store the key
do not accept a caller-supplied URL for this feature
name is North Wind, a label, not an address to fetch
```

- homework
```text
# 27a  the server would be the one that connects, so we do not give it a blank URL
# 27b  allowlist of scheme and host
# 27c  Anemi takes an upload for the file, not a URL from the form
```

- example 28. do not fetch an arbitrary URL for sc_3
- allow https only
- allow hosts we named
- refuse internal addresses
- do not follow a redirect onto a private address
- the safe design uploads the bytes

```text
upload bytes for sc_3
store the key
do not accept a caller-supplied URL for this feature
points is 11, a label, not an address to fetch
```

- homework
```text
# 28a  the server would be the one that connects, so we do not give it a blank URL
# 28b  allowlist of scheme and host
# 28c  Anemi takes an upload for the file, not a URL from the form
```

- example 29. do not fetch an arbitrary URL for tm_2
- allow https only
- allow hosts we named
- refuse internal addresses
- do not follow a redirect onto a private address
- the safe design uploads the bytes

```text
upload bytes for tm_2
store the key
do not accept a caller-supplied URL for this feature
name is Blue, a label, not an address to fetch
```

- homework
```text
# 29a  the server would be the one that connects, so we do not give it a blank URL
# 29b  allowlist of scheme and host
# 29c  Anemi takes an upload for the file, not a URL from the form
```

- example 30. do not fetch an arbitrary URL for up_6
- allow https only
- allow hosts we named
- refuse internal addresses
- do not follow a redirect onto a private address
- the safe design uploads the bytes

```text
upload bytes for up_6
store the key
do not accept a caller-supplied URL for this feature
key is videos/u_1/a.mp4, a label, not an address to fetch
```

- homework
```text
# 30a  the server would be the one that connects, so we do not give it a blank URL
# 30b  allowlist of scheme and host
# 30c  Anemi takes an upload for the file, not a URL from the form
```

- example 31. do not fetch an arbitrary URL for st_1
- allow https only
- allow hosts we named
- refuse internal addresses
- do not follow a redirect onto a private address
- the safe design uploads the bytes

```text
upload bytes for st_1
store the key
do not accept a caller-supplied URL for this feature
player is player_a, a label, not an address to fetch
```

- homework
```text
# 31a  the server would be the one that connects, so we do not give it a blank URL
# 31b  allowlist of scheme and host
# 31c  Anemi takes an upload for the file, not a URL from the form
```

- example 32. do not fetch an arbitrary URL for n_2
- allow https only
- allow hosts we named
- refuse internal addresses
- do not follow a redirect onto a private address
- the safe design uploads the bytes

```text
upload bytes for n_2
store the key
do not accept a caller-supplied URL for this feature
port is Chattogram, a label, not an address to fetch
```

- homework
```text
# 32a  the server would be the one that connects, so we do not give it a blank URL
# 32b  allowlist of scheme and host
# 32c  Anemi takes an upload for the file, not a URL from the form
```

- example 33. do not fetch an arbitrary URL for b_3
- allow https only
- allow hosts we named
- refuse internal addresses
- do not follow a redirect onto a private address
- the safe design uploads the bytes

```text
upload bytes for b_3
store the key
do not accept a caller-supplied URL for this feature
round is semi, a label, not an address to fetch
```

- homework
```text
# 33a  the server would be the one that connects, so we do not give it a blank URL
# 33b  allowlist of scheme and host
# 33c  Anemi takes an upload for the file, not a URL from the form
```

- example 34. do not fetch an arbitrary URL for se_1
- allow https only
- allow hosts we named
- refuse internal addresses
- do not follow a redirect onto a private address
- the safe design uploads the bytes

```text
upload bytes for se_1
store the key
do not accept a caller-supplied URL for this feature
userId is u_3, a label, not an address to fetch
```

- homework
```text
# 34a  the server would be the one that connects, so we do not give it a blank URL
# 34b  allowlist of scheme and host
# 34c  Anemi takes an upload for the file, not a URL from the form
```

- example 35. do not fetch an arbitrary URL for q_1
- allow https only
- allow hosts we named
- refuse internal addresses
- do not follow a redirect onto a private address
- the safe design uploads the bytes

```text
upload bytes for q_1
store the key
do not accept a caller-supplied URL for this feature
name is laytime, a label, not an address to fetch
```

- homework
```text
# 35a  the server would be the one that connects, so we do not give it a blank URL
# 35b  allowlist of scheme and host
# 35c  Anemi takes an upload for the file, not a URL from the form
```

- example 36. do not fetch an arbitrary URL for r_1
- allow https only
- allow hosts we named
- refuse internal addresses
- do not follow a redirect onto a private address
- the safe design uploads the bytes

```text
upload bytes for r_1
store the key
do not accept a caller-supplied URL for this feature
name is operator, a label, not an address to fetch
```

- homework
```text
# 36a  the server would be the one that connects, so we do not give it a blank URL
# 36b  allowlist of scheme and host
# 36c  Anemi takes an upload for the file, not a URL from the form
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

- example 1. hash the password, encrypt the TOTP secret, TLS on the public hop
- bcrypt for the password. we cannot read it back
- the TOTP secret must be readable, so it is encrypted, and the key is outside the database
- certificate matches the name, is in date, chains to a trusted root

```ts
const passwordHash = await hash(plain, 12);
const ok = await compare(plain, passwordHash);
// user pc_12
// TLS ends at nginx for the public name
```

- homework
```ts
// 1a  hash, do not encrypt, the password
// 1b  encrypt the TOTP secret
// 1c  three certificate checks
// 1d  localhost nginx-to-Node is not the public hop
```

- example 2. hash the password, encrypt the TOTP secret, TLS on the public hop
- bcrypt for the password. we cannot read it back
- the TOTP secret must be readable, so it is encrypted, and the key is outside the database
- certificate matches the name, is in date, chains to a trusted root

```ts
const passwordHash = await hash(plain, 12);
const ok = await compare(plain, passwordHash);
// user m_1
// TLS ends at nginx for the public name
```

- homework
```ts
// 2a  hash, do not encrypt, the password
// 2b  encrypt the TOTP secret
// 2c  three certificate checks
// 2d  localhost nginx-to-Node is not the public hop
```

- example 3. hash the password, encrypt the TOTP secret, TLS on the public hop
- bcrypt for the password. we cannot read it back
- the TOTP secret must be readable, so it is encrypted, and the key is outside the database
- certificate matches the name, is in date, chains to a trusted root

```ts
const passwordHash = await hash(plain, 12);
const ok = await compare(plain, passwordHash);
// user t_9
// TLS ends at nginx for the public name
```

- homework
```ts
// 3a  hash, do not encrypt, the password
// 3b  encrypt the TOTP secret
// 3c  three certificate checks
// 3d  localhost nginx-to-Node is not the public hop
```

- example 4. hash the password, encrypt the TOTP secret, TLS on the public hop
- bcrypt for the password. we cannot read it back
- the TOTP secret must be readable, so it is encrypted, and the key is outside the database
- certificate matches the name, is in date, chains to a trusted root

```ts
const passwordHash = await hash(plain, 12);
const ok = await compare(plain, passwordHash);
// user v_4
// TLS ends at nginx for the public name
```

- homework
```ts
// 4a  hash, do not encrypt, the password
// 4b  encrypt the TOTP secret
// 4c  three certificate checks
// 4d  localhost nginx-to-Node is not the public hop
```

- example 5. hash the password, encrypt the TOTP secret, TLS on the public hop
- bcrypt for the password. we cannot read it back
- the TOTP secret must be readable, so it is encrypted, and the key is outside the database
- certificate matches the name, is in date, chains to a trusted root

```ts
const passwordHash = await hash(plain, 12);
const ok = await compare(plain, passwordHash);
// user f_2
// TLS ends at nginx for the public name
```

- homework
```ts
// 5a  hash, do not encrypt, the password
// 5b  encrypt the TOTP secret
// 5c  three certificate checks
// 5d  localhost nginx-to-Node is not the public hop
```

- example 6. hash the password, encrypt the TOTP secret, TLS on the public hop
- bcrypt for the password. we cannot read it back
- the TOTP secret must be readable, so it is encrypted, and the key is outside the database
- certificate matches the name, is in date, chains to a trusted root

```ts
const passwordHash = await hash(plain, 12);
const ok = await compare(plain, passwordHash);
// user u_3
// TLS ends at nginx for the public name
```

- homework
```ts
// 6a  hash, do not encrypt, the password
// 6b  encrypt the TOTP secret
// 6c  three certificate checks
// 6d  localhost nginx-to-Node is not the public hop
```

- example 7. hash the password, encrypt the TOTP secret, TLS on the public hop
- bcrypt for the password. we cannot read it back
- the TOTP secret must be readable, so it is encrypted, and the key is outside the database
- certificate matches the name, is in date, chains to a trusted root

```ts
const passwordHash = await hash(plain, 12);
const ok = await compare(plain, passwordHash);
// user pay_8
// TLS ends at nginx for the public name
```

- homework
```ts
// 7a  hash, do not encrypt, the password
// 7b  encrypt the TOTP secret
// 7c  three certificate checks
// 7d  localhost nginx-to-Node is not the public hop
```

- example 8. hash the password, encrypt the TOTP secret, TLS on the public hop
- bcrypt for the password. we cannot read it back
- the TOTP secret must be readable, so it is encrypted, and the key is outside the database
- certificate matches the name, is in date, chains to a trusted root

```ts
const passwordHash = await hash(plain, 12);
const ok = await compare(plain, passwordHash);
// user room_2
// TLS ends at nginx for the public name
```

- homework
```ts
// 8a  hash, do not encrypt, the password
// 8b  encrypt the TOTP secret
// 8c  three certificate checks
// 8d  localhost nginx-to-Node is not the public hop
```

- example 9. hash the password, encrypt the TOTP secret, TLS on the public hop
- bcrypt for the password. we cannot read it back
- the TOTP secret must be readable, so it is encrypted, and the key is outside the database
- certificate matches the name, is in date, chains to a trusted root

```ts
const passwordHash = await hash(plain, 12);
const ok = await compare(plain, passwordHash);
// user vs_7
// TLS ends at nginx for the public name
```

- homework
```ts
// 9a  hash, do not encrypt, the password
// 9b  encrypt the TOTP secret
// 9c  three certificate checks
// 9d  localhost nginx-to-Node is not the public hop
```

- example 10. hash the password, encrypt the TOTP secret, TLS on the public hop
- bcrypt for the password. we cannot read it back
- the TOTP secret must be readable, so it is encrypted, and the key is outside the database
- certificate matches the name, is in date, chains to a trusted root

```ts
const passwordHash = await hash(plain, 12);
const ok = await compare(plain, passwordHash);
// user sc_3
// TLS ends at nginx for the public name
```

- homework
```ts
// 10a  hash, do not encrypt, the password
// 10b  encrypt the TOTP secret
// 10c  three certificate checks
// 10d  localhost nginx-to-Node is not the public hop
```

- example 11. hash the password, encrypt the TOTP secret, TLS on the public hop
- bcrypt for the password. we cannot read it back
- the TOTP secret must be readable, so it is encrypted, and the key is outside the database
- certificate matches the name, is in date, chains to a trusted root

```ts
const passwordHash = await hash(plain, 12);
const ok = await compare(plain, passwordHash);
// user tm_2
// TLS ends at nginx for the public name
```

- homework
```ts
// 11a  hash, do not encrypt, the password
// 11b  encrypt the TOTP secret
// 11c  three certificate checks
// 11d  localhost nginx-to-Node is not the public hop
```

- example 12. hash the password, encrypt the TOTP secret, TLS on the public hop
- bcrypt for the password. we cannot read it back
- the TOTP secret must be readable, so it is encrypted, and the key is outside the database
- certificate matches the name, is in date, chains to a trusted root

```ts
const passwordHash = await hash(plain, 12);
const ok = await compare(plain, passwordHash);
// user up_6
// TLS ends at nginx for the public name
```

- homework
```ts
// 12a  hash, do not encrypt, the password
// 12b  encrypt the TOTP secret
// 12c  three certificate checks
// 12d  localhost nginx-to-Node is not the public hop
```

- example 13. hash the password, encrypt the TOTP secret, TLS on the public hop
- bcrypt for the password. we cannot read it back
- the TOTP secret must be readable, so it is encrypted, and the key is outside the database
- certificate matches the name, is in date, chains to a trusted root

```ts
const passwordHash = await hash(plain, 12);
const ok = await compare(plain, passwordHash);
// user st_1
// TLS ends at nginx for the public name
```

- homework
```ts
// 13a  hash, do not encrypt, the password
// 13b  encrypt the TOTP secret
// 13c  three certificate checks
// 13d  localhost nginx-to-Node is not the public hop
```

- example 14. hash the password, encrypt the TOTP secret, TLS on the public hop
- bcrypt for the password. we cannot read it back
- the TOTP secret must be readable, so it is encrypted, and the key is outside the database
- certificate matches the name, is in date, chains to a trusted root

```ts
const passwordHash = await hash(plain, 12);
const ok = await compare(plain, passwordHash);
// user n_2
// TLS ends at nginx for the public name
```

- homework
```ts
// 14a  hash, do not encrypt, the password
// 14b  encrypt the TOTP secret
// 14c  three certificate checks
// 14d  localhost nginx-to-Node is not the public hop
```

- example 15. hash the password, encrypt the TOTP secret, TLS on the public hop
- bcrypt for the password. we cannot read it back
- the TOTP secret must be readable, so it is encrypted, and the key is outside the database
- certificate matches the name, is in date, chains to a trusted root

```ts
const passwordHash = await hash(plain, 12);
const ok = await compare(plain, passwordHash);
// user b_3
// TLS ends at nginx for the public name
```

- homework
```ts
// 15a  hash, do not encrypt, the password
// 15b  encrypt the TOTP secret
// 15c  three certificate checks
// 15d  localhost nginx-to-Node is not the public hop
```

- example 16. hash the password, encrypt the TOTP secret, TLS on the public hop
- bcrypt for the password. we cannot read it back
- the TOTP secret must be readable, so it is encrypted, and the key is outside the database
- certificate matches the name, is in date, chains to a trusted root

```ts
const passwordHash = await hash(plain, 12);
const ok = await compare(plain, passwordHash);
// user se_1
// TLS ends at nginx for the public name
```

- homework
```ts
// 16a  hash, do not encrypt, the password
// 16b  encrypt the TOTP secret
// 16c  three certificate checks
// 16d  localhost nginx-to-Node is not the public hop
```

- example 17. hash the password, encrypt the TOTP secret, TLS on the public hop
- bcrypt for the password. we cannot read it back
- the TOTP secret must be readable, so it is encrypted, and the key is outside the database
- certificate matches the name, is in date, chains to a trusted root

```ts
const passwordHash = await hash(plain, 12);
const ok = await compare(plain, passwordHash);
// user q_1
// TLS ends at nginx for the public name
```

- homework
```ts
// 17a  hash, do not encrypt, the password
// 17b  encrypt the TOTP secret
// 17c  three certificate checks
// 17d  localhost nginx-to-Node is not the public hop
```

- example 18. hash the password, encrypt the TOTP secret, TLS on the public hop
- bcrypt for the password. we cannot read it back
- the TOTP secret must be readable, so it is encrypted, and the key is outside the database
- certificate matches the name, is in date, chains to a trusted root

```ts
const passwordHash = await hash(plain, 12);
const ok = await compare(plain, passwordHash);
// user r_1
// TLS ends at nginx for the public name
```

- homework
```ts
// 18a  hash, do not encrypt, the password
// 18b  encrypt the TOTP secret
// 18c  three certificate checks
// 18d  localhost nginx-to-Node is not the public hop
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

- example 1. session for pc_12
- cost 12
- cookie flags when we use a cookie
- access token about 15 minutes
- refresh token stored as a hash and rotated
- reuse revokes the family
- the session id is not placed in the URL

```ts
const passwordHash = await hash(plain, 12);
await compare(plain, passwordHash);
// session subject pc_12
```

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
```

- homework
```ts
// 1a  stored password material for pc_12 is the hash
// 1b  three flags
// 1c  reuse after rotation revokes the family
// 1d  logout revokes the refresh token. clearing the screen does not
```

- example 2. session for m_1
- cost 12
- cookie flags when we use a cookie
- access token about 15 minutes
- refresh token stored as a hash and rotated
- reuse revokes the family
- the session id is not placed in the URL

```ts
const passwordHash = await hash(plain, 12);
await compare(plain, passwordHash);
// session subject m_1
```

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
```

- homework
```ts
// 2a  stored password material for m_1 is the hash
// 2b  three flags
// 2c  reuse after rotation revokes the family
// 2d  logout revokes the refresh token. clearing the screen does not
```

- example 3. session for t_9
- cost 12
- cookie flags when we use a cookie
- access token about 15 minutes
- refresh token stored as a hash and rotated
- reuse revokes the family
- the session id is not placed in the URL

```ts
const passwordHash = await hash(plain, 12);
await compare(plain, passwordHash);
// session subject t_9
```

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
```

- homework
```ts
// 3a  stored password material for t_9 is the hash
// 3b  three flags
// 3c  reuse after rotation revokes the family
// 3d  logout revokes the refresh token. clearing the screen does not
```

- example 4. session for v_4
- cost 12
- cookie flags when we use a cookie
- access token about 15 minutes
- refresh token stored as a hash and rotated
- reuse revokes the family
- the session id is not placed in the URL

```ts
const passwordHash = await hash(plain, 12);
await compare(plain, passwordHash);
// session subject v_4
```

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
```

- homework
```ts
// 4a  stored password material for v_4 is the hash
// 4b  three flags
// 4c  reuse after rotation revokes the family
// 4d  logout revokes the refresh token. clearing the screen does not
```

- example 5. session for f_2
- cost 12
- cookie flags when we use a cookie
- access token about 15 minutes
- refresh token stored as a hash and rotated
- reuse revokes the family
- the session id is not placed in the URL

```ts
const passwordHash = await hash(plain, 12);
await compare(plain, passwordHash);
// session subject f_2
```

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
```

- homework
```ts
// 5a  stored password material for f_2 is the hash
// 5b  three flags
// 5c  reuse after rotation revokes the family
// 5d  logout revokes the refresh token. clearing the screen does not
```

- example 6. session for u_3
- cost 12
- cookie flags when we use a cookie
- access token about 15 minutes
- refresh token stored as a hash and rotated
- reuse revokes the family
- the session id is not placed in the URL

```ts
const passwordHash = await hash(plain, 12);
await compare(plain, passwordHash);
// session subject u_3
```

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
```

- homework
```ts
// 6a  stored password material for u_3 is the hash
// 6b  three flags
// 6c  reuse after rotation revokes the family
// 6d  logout revokes the refresh token. clearing the screen does not
```

- example 7. session for pay_8
- cost 12
- cookie flags when we use a cookie
- access token about 15 minutes
- refresh token stored as a hash and rotated
- reuse revokes the family
- the session id is not placed in the URL

```ts
const passwordHash = await hash(plain, 12);
await compare(plain, passwordHash);
// session subject pay_8
```

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
```

- homework
```ts
// 7a  stored password material for pay_8 is the hash
// 7b  three flags
// 7c  reuse after rotation revokes the family
// 7d  logout revokes the refresh token. clearing the screen does not
```

- example 8. session for room_2
- cost 12
- cookie flags when we use a cookie
- access token about 15 minutes
- refresh token stored as a hash and rotated
- reuse revokes the family
- the session id is not placed in the URL

```ts
const passwordHash = await hash(plain, 12);
await compare(plain, passwordHash);
// session subject room_2
```

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
```

- homework
```ts
// 8a  stored password material for room_2 is the hash
// 8b  three flags
// 8c  reuse after rotation revokes the family
// 8d  logout revokes the refresh token. clearing the screen does not
```

- example 9. session for vs_7
- cost 12
- cookie flags when we use a cookie
- access token about 15 minutes
- refresh token stored as a hash and rotated
- reuse revokes the family
- the session id is not placed in the URL

```ts
const passwordHash = await hash(plain, 12);
await compare(plain, passwordHash);
// session subject vs_7
```

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
```

- homework
```ts
// 9a  stored password material for vs_7 is the hash
// 9b  three flags
// 9c  reuse after rotation revokes the family
// 9d  logout revokes the refresh token. clearing the screen does not
```

- example 10. session for sc_3
- cost 12
- cookie flags when we use a cookie
- access token about 15 minutes
- refresh token stored as a hash and rotated
- reuse revokes the family
- the session id is not placed in the URL

```ts
const passwordHash = await hash(plain, 12);
await compare(plain, passwordHash);
// session subject sc_3
```

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
```

- homework
```ts
// 10a  stored password material for sc_3 is the hash
// 10b  three flags
// 10c  reuse after rotation revokes the family
// 10d  logout revokes the refresh token. clearing the screen does not
```

- example 11. session for tm_2
- cost 12
- cookie flags when we use a cookie
- access token about 15 minutes
- refresh token stored as a hash and rotated
- reuse revokes the family
- the session id is not placed in the URL

```ts
const passwordHash = await hash(plain, 12);
await compare(plain, passwordHash);
// session subject tm_2
```

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
```

- homework
```ts
// 11a  stored password material for tm_2 is the hash
// 11b  three flags
// 11c  reuse after rotation revokes the family
// 11d  logout revokes the refresh token. clearing the screen does not
```

- example 12. session for up_6
- cost 12
- cookie flags when we use a cookie
- access token about 15 minutes
- refresh token stored as a hash and rotated
- reuse revokes the family
- the session id is not placed in the URL

```ts
const passwordHash = await hash(plain, 12);
await compare(plain, passwordHash);
// session subject up_6
```

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
```

- homework
```ts
// 12a  stored password material for up_6 is the hash
// 12b  three flags
// 12c  reuse after rotation revokes the family
// 12d  logout revokes the refresh token. clearing the screen does not
```

- example 13. session for st_1
- cost 12
- cookie flags when we use a cookie
- access token about 15 minutes
- refresh token stored as a hash and rotated
- reuse revokes the family
- the session id is not placed in the URL

```ts
const passwordHash = await hash(plain, 12);
await compare(plain, passwordHash);
// session subject st_1
```

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
```

- homework
```ts
// 13a  stored password material for st_1 is the hash
// 13b  three flags
// 13c  reuse after rotation revokes the family
// 13d  logout revokes the refresh token. clearing the screen does not
```

- example 14. session for n_2
- cost 12
- cookie flags when we use a cookie
- access token about 15 minutes
- refresh token stored as a hash and rotated
- reuse revokes the family
- the session id is not placed in the URL

```ts
const passwordHash = await hash(plain, 12);
await compare(plain, passwordHash);
// session subject n_2
```

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
```

- homework
```ts
// 14a  stored password material for n_2 is the hash
// 14b  three flags
// 14c  reuse after rotation revokes the family
// 14d  logout revokes the refresh token. clearing the screen does not
```

- example 15. session for b_3
- cost 12
- cookie flags when we use a cookie
- access token about 15 minutes
- refresh token stored as a hash and rotated
- reuse revokes the family
- the session id is not placed in the URL

```ts
const passwordHash = await hash(plain, 12);
await compare(plain, passwordHash);
// session subject b_3
```

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
```

- homework
```ts
// 15a  stored password material for b_3 is the hash
// 15b  three flags
// 15c  reuse after rotation revokes the family
// 15d  logout revokes the refresh token. clearing the screen does not
```

- example 16. session for se_1
- cost 12
- cookie flags when we use a cookie
- access token about 15 minutes
- refresh token stored as a hash and rotated
- reuse revokes the family
- the session id is not placed in the URL

```ts
const passwordHash = await hash(plain, 12);
await compare(plain, passwordHash);
// session subject se_1
```

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
```

- homework
```ts
// 16a  stored password material for se_1 is the hash
// 16b  three flags
// 16c  reuse after rotation revokes the family
// 16d  logout revokes the refresh token. clearing the screen does not
```

- example 17. session for q_1
- cost 12
- cookie flags when we use a cookie
- access token about 15 minutes
- refresh token stored as a hash and rotated
- reuse revokes the family
- the session id is not placed in the URL

```ts
const passwordHash = await hash(plain, 12);
await compare(plain, passwordHash);
// session subject q_1
```

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
```

- homework
```ts
// 17a  stored password material for q_1 is the hash
// 17b  three flags
// 17c  reuse after rotation revokes the family
// 17d  logout revokes the refresh token. clearing the screen does not
```

- example 18. session for r_1
- cost 12
- cookie flags when we use a cookie
- access token about 15 minutes
- refresh token stored as a hash and rotated
- reuse revokes the family
- the session id is not placed in the URL

```ts
const passwordHash = await hash(plain, 12);
await compare(plain, passwordHash);
// session subject r_1
```

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
```

- homework
```ts
// 18a  stored password material for r_1 is the hash
// 18b  three flags
// 18c  reuse after rotation revokes the family
// 18d  logout revokes the refresh token. clearing the screen does not
```

- example 19. session for pc_12
- cost 12
- cookie flags when we use a cookie
- access token about 15 minutes
- refresh token stored as a hash and rotated
- reuse revokes the family
- the session id is not placed in the URL

```ts
const passwordHash = await hash(plain, 12);
await compare(plain, passwordHash);
// session subject pc_12
```

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
```

- homework
```ts
// 19a  stored password material for pc_12 is the hash
// 19b  three flags
// 19c  reuse after rotation revokes the family
// 19d  logout revokes the refresh token. clearing the screen does not
```

- example 20. session for m_1
- cost 12
- cookie flags when we use a cookie
- access token about 15 minutes
- refresh token stored as a hash and rotated
- reuse revokes the family
- the session id is not placed in the URL

```ts
const passwordHash = await hash(plain, 12);
await compare(plain, passwordHash);
// session subject m_1
```

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
```

- homework
```ts
// 20a  stored password material for m_1 is the hash
// 20b  three flags
// 20c  reuse after rotation revokes the family
// 20d  logout revokes the refresh token. clearing the screen does not
```

- example 21. session for t_9
- cost 12
- cookie flags when we use a cookie
- access token about 15 minutes
- refresh token stored as a hash and rotated
- reuse revokes the family
- the session id is not placed in the URL

```ts
const passwordHash = await hash(plain, 12);
await compare(plain, passwordHash);
// session subject t_9
```

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
```

- homework
```ts
// 21a  stored password material for t_9 is the hash
// 21b  three flags
// 21c  reuse after rotation revokes the family
// 21d  logout revokes the refresh token. clearing the screen does not
```

- example 22. session for v_4
- cost 12
- cookie flags when we use a cookie
- access token about 15 minutes
- refresh token stored as a hash and rotated
- reuse revokes the family
- the session id is not placed in the URL

```ts
const passwordHash = await hash(plain, 12);
await compare(plain, passwordHash);
// session subject v_4
```

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
```

- homework
```ts
// 22a  stored password material for v_4 is the hash
// 22b  three flags
// 22c  reuse after rotation revokes the family
// 22d  logout revokes the refresh token. clearing the screen does not
```

- example 23. session for f_2
- cost 12
- cookie flags when we use a cookie
- access token about 15 minutes
- refresh token stored as a hash and rotated
- reuse revokes the family
- the session id is not placed in the URL

```ts
const passwordHash = await hash(plain, 12);
await compare(plain, passwordHash);
// session subject f_2
```

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
```

- homework
```ts
// 23a  stored password material for f_2 is the hash
// 23b  three flags
// 23c  reuse after rotation revokes the family
// 23d  logout revokes the refresh token. clearing the screen does not
```

- example 24. session for u_3
- cost 12
- cookie flags when we use a cookie
- access token about 15 minutes
- refresh token stored as a hash and rotated
- reuse revokes the family
- the session id is not placed in the URL

```ts
const passwordHash = await hash(plain, 12);
await compare(plain, passwordHash);
// session subject u_3
```

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
```

- homework
```ts
// 24a  stored password material for u_3 is the hash
// 24b  three flags
// 24c  reuse after rotation revokes the family
// 24d  logout revokes the refresh token. clearing the screen does not
```

- example 25. session for pay_8
- cost 12
- cookie flags when we use a cookie
- access token about 15 minutes
- refresh token stored as a hash and rotated
- reuse revokes the family
- the session id is not placed in the URL

```ts
const passwordHash = await hash(plain, 12);
await compare(plain, passwordHash);
// session subject pay_8
```

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
```

- homework
```ts
// 25a  stored password material for pay_8 is the hash
// 25b  three flags
// 25c  reuse after rotation revokes the family
// 25d  logout revokes the refresh token. clearing the screen does not
```

- example 26. session for room_2
- cost 12
- cookie flags when we use a cookie
- access token about 15 minutes
- refresh token stored as a hash and rotated
- reuse revokes the family
- the session id is not placed in the URL

```ts
const passwordHash = await hash(plain, 12);
await compare(plain, passwordHash);
// session subject room_2
```

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
```

- homework
```ts
// 26a  stored password material for room_2 is the hash
// 26b  three flags
// 26c  reuse after rotation revokes the family
// 26d  logout revokes the refresh token. clearing the screen does not
```

- example 27. session for vs_7
- cost 12
- cookie flags when we use a cookie
- access token about 15 minutes
- refresh token stored as a hash and rotated
- reuse revokes the family
- the session id is not placed in the URL

```ts
const passwordHash = await hash(plain, 12);
await compare(plain, passwordHash);
// session subject vs_7
```

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
```

- homework
```ts
// 27a  stored password material for vs_7 is the hash
// 27b  three flags
// 27c  reuse after rotation revokes the family
// 27d  logout revokes the refresh token. clearing the screen does not
```

- example 28. session for sc_3
- cost 12
- cookie flags when we use a cookie
- access token about 15 minutes
- refresh token stored as a hash and rotated
- reuse revokes the family
- the session id is not placed in the URL

```ts
const passwordHash = await hash(plain, 12);
await compare(plain, passwordHash);
// session subject sc_3
```

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
```

- homework
```ts
// 28a  stored password material for sc_3 is the hash
// 28b  three flags
// 28c  reuse after rotation revokes the family
// 28d  logout revokes the refresh token. clearing the screen does not
```

- example 29. session for tm_2
- cost 12
- cookie flags when we use a cookie
- access token about 15 minutes
- refresh token stored as a hash and rotated
- reuse revokes the family
- the session id is not placed in the URL

```ts
const passwordHash = await hash(plain, 12);
await compare(plain, passwordHash);
// session subject tm_2
```

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
```

- homework
```ts
// 29a  stored password material for tm_2 is the hash
// 29b  three flags
// 29c  reuse after rotation revokes the family
// 29d  logout revokes the refresh token. clearing the screen does not
```

- example 30. session for up_6
- cost 12
- cookie flags when we use a cookie
- access token about 15 minutes
- refresh token stored as a hash and rotated
- reuse revokes the family
- the session id is not placed in the URL

```ts
const passwordHash = await hash(plain, 12);
await compare(plain, passwordHash);
// session subject up_6
```

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
```

- homework
```ts
// 30a  stored password material for up_6 is the hash
// 30b  three flags
// 30c  reuse after rotation revokes the family
// 30d  logout revokes the refresh token. clearing the screen does not
```

- example 31. session for st_1
- cost 12
- cookie flags when we use a cookie
- access token about 15 minutes
- refresh token stored as a hash and rotated
- reuse revokes the family
- the session id is not placed in the URL

```ts
const passwordHash = await hash(plain, 12);
await compare(plain, passwordHash);
// session subject st_1
```

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
```

- homework
```ts
// 31a  stored password material for st_1 is the hash
// 31b  three flags
// 31c  reuse after rotation revokes the family
// 31d  logout revokes the refresh token. clearing the screen does not
```

- example 32. session for n_2
- cost 12
- cookie flags when we use a cookie
- access token about 15 minutes
- refresh token stored as a hash and rotated
- reuse revokes the family
- the session id is not placed in the URL

```ts
const passwordHash = await hash(plain, 12);
await compare(plain, passwordHash);
// session subject n_2
```

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
```

- homework
```ts
// 32a  stored password material for n_2 is the hash
// 32b  three flags
// 32c  reuse after rotation revokes the family
// 32d  logout revokes the refresh token. clearing the screen does not
```

- example 33. session for b_3
- cost 12
- cookie flags when we use a cookie
- access token about 15 minutes
- refresh token stored as a hash and rotated
- reuse revokes the family
- the session id is not placed in the URL

```ts
const passwordHash = await hash(plain, 12);
await compare(plain, passwordHash);
// session subject b_3
```

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
```

- homework
```ts
// 33a  stored password material for b_3 is the hash
// 33b  three flags
// 33c  reuse after rotation revokes the family
// 33d  logout revokes the refresh token. clearing the screen does not
```

- example 34. session for se_1
- cost 12
- cookie flags when we use a cookie
- access token about 15 minutes
- refresh token stored as a hash and rotated
- reuse revokes the family
- the session id is not placed in the URL

```ts
const passwordHash = await hash(plain, 12);
await compare(plain, passwordHash);
// session subject se_1
```

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
```

- homework
```ts
// 34a  stored password material for se_1 is the hash
// 34b  three flags
// 34c  reuse after rotation revokes the family
// 34d  logout revokes the refresh token. clearing the screen does not
```

- example 35. session for q_1
- cost 12
- cookie flags when we use a cookie
- access token about 15 minutes
- refresh token stored as a hash and rotated
- reuse revokes the family
- the session id is not placed in the URL

```ts
const passwordHash = await hash(plain, 12);
await compare(plain, passwordHash);
// session subject q_1
```

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
```

- homework
```ts
// 35a  stored password material for q_1 is the hash
// 35b  three flags
// 35c  reuse after rotation revokes the family
// 35d  logout revokes the refresh token. clearing the screen does not
```

- example 36. session for r_1
- cost 12
- cookie flags when we use a cookie
- access token about 15 minutes
- refresh token stored as a hash and rotated
- reuse revokes the family
- the session id is not placed in the URL

```ts
const passwordHash = await hash(plain, 12);
await compare(plain, passwordHash);
// session subject r_1
```

```http
Set-Cookie: sid=...; HttpOnly; Secure; SameSite=Lax
```

- homework
```ts
// 36a  stored password material for r_1 is the hash
// 36b  three flags
// 36c  reuse after rotation revokes the family
// 36d  logout revokes the refresh token. clearing the screen does not
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

- example 1. checks on a JWT for pc_12
- signature, expiry, expected algorithm
- payload holds sub and roles. it does not hold a password
- OAuth secret stays on the server
- redirect URI is an exact allowlist
- state is checked when the browser returns

```text
sub pc_12
exp required
algorithm is the one we sign with
no password in the payload
vesselName is not a claim
```

- homework
```text
# 1a  the signature does not hide the payload
# 1b  three checks
# 1c  the OAuth secret is not in the browser
# 1d  an open redirect would hand the code to someone else. the allowlist prevents that
```

- example 2. checks on a JWT for m_1
- signature, expiry, expected algorithm
- payload holds sub and roles. it does not hold a password
- OAuth secret stays on the server
- redirect URI is an exact allowlist
- state is checked when the browser returns

```text
sub m_1
exp required
algorithm is the one we sign with
no password in the payload
home is not a claim
```

- homework
```text
# 2a  the signature does not hide the payload
# 2b  three checks
# 2c  the OAuth secret is not in the browser
# 2d  an open redirect would hand the code to someone else. the allowlist prevents that
```

- example 3. checks on a JWT for t_9
- signature, expiry, expected algorithm
- payload holds sub and roles. it does not hold a password
- OAuth secret stays on the server
- redirect URI is an exact allowlist
- state is checked when the browser returns

```text
sub t_9
exp required
algorithm is the one we sign with
no password in the payload
name is not a claim
```

- homework
```text
# 3a  the signature does not hide the payload
# 3b  three checks
# 3c  the OAuth secret is not in the browser
# 3d  an open redirect would hand the code to someone else. the allowlist prevents that
```

- example 4. checks on a JWT for v_4
- signature, expiry, expected algorithm
- payload holds sub and roles. it does not hold a password
- OAuth secret stays on the server
- redirect URI is an exact allowlist
- state is checked when the browser returns

```text
sub v_4
exp required
algorithm is the one we sign with
no password in the payload
title is not a claim
```

- homework
```text
# 4a  the signature does not hide the payload
# 4b  three checks
# 4c  the OAuth secret is not in the browser
# 4d  an open redirect would hand the code to someone else. the allowlist prevents that
```

- example 5. checks on a JWT for f_2
- signature, expiry, expected algorithm
- payload holds sub and roles. it does not hold a password
- OAuth secret stays on the server
- redirect URI is an exact allowlist
- state is checked when the browser returns

```text
sub f_2
exp required
algorithm is the one we sign with
no password in the payload
kind is not a claim
```

- homework
```text
# 5a  the signature does not hide the payload
# 5b  three checks
# 5c  the OAuth secret is not in the browser
# 5d  an open redirect would hand the code to someone else. the allowlist prevents that
```

- example 6. checks on a JWT for u_3
- signature, expiry, expected algorithm
- payload holds sub and roles. it does not hold a password
- OAuth secret stays on the server
- redirect URI is an exact allowlist
- state is checked when the browser returns

```text
sub u_3
exp required
algorithm is the one we sign with
no password in the payload
email is not a claim
```

- homework
```text
# 6a  the signature does not hide the payload
# 6b  three checks
# 6c  the OAuth secret is not in the browser
# 6d  an open redirect would hand the code to someone else. the allowlist prevents that
```

- example 7. checks on a JWT for pay_8
- signature, expiry, expected algorithm
- payload holds sub and roles. it does not hold a password
- OAuth secret stays on the server
- redirect URI is an exact allowlist
- state is checked when the browser returns

```text
sub pay_8
exp required
algorithm is the one we sign with
no password in the payload
eventId is not a claim
```

- homework
```text
# 7a  the signature does not hide the payload
# 7b  three checks
# 7c  the OAuth secret is not in the browser
# 7d  an open redirect would hand the code to someone else. the allowlist prevents that
```

- example 8. checks on a JWT for room_2
- signature, expiry, expected algorithm
- payload holds sub and roles. it does not hold a password
- OAuth secret stays on the server
- redirect URI is an exact allowlist
- state is checked when the browser returns

```text
sub room_2
exp required
algorithm is the one we sign with
no password in the payload
sessionId is not a claim
```

- homework
```text
# 8a  the signature does not hide the payload
# 8b  three checks
# 8c  the OAuth secret is not in the browser
# 8d  an open redirect would hand the code to someone else. the allowlist prevents that
```

- example 9. checks on a JWT for vs_7
- signature, expiry, expected algorithm
- payload holds sub and roles. it does not hold a password
- OAuth secret stays on the server
- redirect URI is an exact allowlist
- state is checked when the browser returns

```text
sub vs_7
exp required
algorithm is the one we sign with
no password in the payload
name is not a claim
```

- homework
```text
# 9a  the signature does not hide the payload
# 9b  three checks
# 9c  the OAuth secret is not in the browser
# 9d  an open redirect would hand the code to someone else. the allowlist prevents that
```

- example 10. checks on a JWT for sc_3
- signature, expiry, expected algorithm
- payload holds sub and roles. it does not hold a password
- OAuth secret stays on the server
- redirect URI is an exact allowlist
- state is checked when the browser returns

```text
sub sc_3
exp required
algorithm is the one we sign with
no password in the payload
points is not a claim
```

- homework
```text
# 10a  the signature does not hide the payload
# 10b  three checks
# 10c  the OAuth secret is not in the browser
# 10d  an open redirect would hand the code to someone else. the allowlist prevents that
```

- example 11. checks on a JWT for tm_2
- signature, expiry, expected algorithm
- payload holds sub and roles. it does not hold a password
- OAuth secret stays on the server
- redirect URI is an exact allowlist
- state is checked when the browser returns

```text
sub tm_2
exp required
algorithm is the one we sign with
no password in the payload
name is not a claim
```

- homework
```text
# 11a  the signature does not hide the payload
# 11b  three checks
# 11c  the OAuth secret is not in the browser
# 11d  an open redirect would hand the code to someone else. the allowlist prevents that
```

- example 12. checks on a JWT for up_6
- signature, expiry, expected algorithm
- payload holds sub and roles. it does not hold a password
- OAuth secret stays on the server
- redirect URI is an exact allowlist
- state is checked when the browser returns

```text
sub up_6
exp required
algorithm is the one we sign with
no password in the payload
key is not a claim
```

- homework
```text
# 12a  the signature does not hide the payload
# 12b  three checks
# 12c  the OAuth secret is not in the browser
# 12d  an open redirect would hand the code to someone else. the allowlist prevents that
```

- example 13. checks on a JWT for st_1
- signature, expiry, expected algorithm
- payload holds sub and roles. it does not hold a password
- OAuth secret stays on the server
- redirect URI is an exact allowlist
- state is checked when the browser returns

```text
sub st_1
exp required
algorithm is the one we sign with
no password in the payload
player is not a claim
```

- homework
```text
# 13a  the signature does not hide the payload
# 13b  three checks
# 13c  the OAuth secret is not in the browser
# 13d  an open redirect would hand the code to someone else. the allowlist prevents that
```

- example 14. checks on a JWT for n_2
- signature, expiry, expected algorithm
- payload holds sub and roles. it does not hold a password
- OAuth secret stays on the server
- redirect URI is an exact allowlist
- state is checked when the browser returns

```text
sub n_2
exp required
algorithm is the one we sign with
no password in the payload
port is not a claim
```

- homework
```text
# 14a  the signature does not hide the payload
# 14b  three checks
# 14c  the OAuth secret is not in the browser
# 14d  an open redirect would hand the code to someone else. the allowlist prevents that
```

- example 15. checks on a JWT for b_3
- signature, expiry, expected algorithm
- payload holds sub and roles. it does not hold a password
- OAuth secret stays on the server
- redirect URI is an exact allowlist
- state is checked when the browser returns

```text
sub b_3
exp required
algorithm is the one we sign with
no password in the payload
round is not a claim
```

- homework
```text
# 15a  the signature does not hide the payload
# 15b  three checks
# 15c  the OAuth secret is not in the browser
# 15d  an open redirect would hand the code to someone else. the allowlist prevents that
```

- example 16. checks on a JWT for se_1
- signature, expiry, expected algorithm
- payload holds sub and roles. it does not hold a password
- OAuth secret stays on the server
- redirect URI is an exact allowlist
- state is checked when the browser returns

```text
sub se_1
exp required
algorithm is the one we sign with
no password in the payload
userId is not a claim
```

- homework
```text
# 16a  the signature does not hide the payload
# 16b  three checks
# 16c  the OAuth secret is not in the browser
# 16d  an open redirect would hand the code to someone else. the allowlist prevents that
```

- example 17. checks on a JWT for q_1
- signature, expiry, expected algorithm
- payload holds sub and roles. it does not hold a password
- OAuth secret stays on the server
- redirect URI is an exact allowlist
- state is checked when the browser returns

```text
sub q_1
exp required
algorithm is the one we sign with
no password in the payload
name is not a claim
```

- homework
```text
# 17a  the signature does not hide the payload
# 17b  three checks
# 17c  the OAuth secret is not in the browser
# 17d  an open redirect would hand the code to someone else. the allowlist prevents that
```

- example 18. checks on a JWT for r_1
- signature, expiry, expected algorithm
- payload holds sub and roles. it does not hold a password
- OAuth secret stays on the server
- redirect URI is an exact allowlist
- state is checked when the browser returns

```text
sub r_1
exp required
algorithm is the one we sign with
no password in the payload
name is not a claim
```

- homework
```text
# 18a  the signature does not hide the payload
# 18b  three checks
# 18c  the OAuth secret is not in the browser
# 18d  an open redirect would hand the code to someone else. the allowlist prevents that
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

- example 1. secrets and headers around pc_12
- a secret in git remains in history
- the database user is not a superuser
- Content-Security-Policy names script sources
- nosniff and HTTPS stay headers are part of the response

```text
Content-Security-Policy: default-src 'self'
X-Content-Type-Options: nosniff
env holds the key. the row pc_12 does not
least privilege on the role and on the database user
```

- homework
```text
# 1a  rotate after a secret was committed
# 1b  the app user cannot drop the cluster
# 1c  the policy has to match how port-calls actually loads script
```

- example 2. secrets and headers around m_1
- a secret in git remains in history
- the database user is not a superuser
- Content-Security-Policy names script sources
- nosniff and HTTPS stay headers are part of the response

```text
Content-Security-Policy: default-src 'self'
X-Content-Type-Options: nosniff
env holds the key. the row m_1 does not
least privilege on the role and on the database user
```

- homework
```text
# 2a  rotate after a secret was committed
# 2b  the app user cannot drop the cluster
# 2c  the policy has to match how matches actually loads script
```

- example 3. secrets and headers around t_9
- a secret in git remains in history
- the database user is not a superuser
- Content-Security-Policy names script sources
- nosniff and HTTPS stay headers are part of the response

```text
Content-Security-Policy: default-src 'self'
X-Content-Type-Options: nosniff
env holds the key. the row t_9 does not
least privilege on the role and on the database user
```

- homework
```text
# 3a  rotate after a secret was committed
# 3b  the app user cannot drop the cluster
# 3c  the policy has to match how tournaments actually loads script
```

- example 4. secrets and headers around v_4
- a secret in git remains in history
- the database user is not a superuser
- Content-Security-Policy names script sources
- nosniff and HTTPS stay headers are part of the response

```text
Content-Security-Policy: default-src 'self'
X-Content-Type-Options: nosniff
env holds the key. the row v_4 does not
least privilege on the role and on the database user
```

- homework
```text
# 4a  rotate after a secret was committed
# 4b  the app user cannot drop the cluster
# 4c  the policy has to match how videos actually loads script
```

- example 5. secrets and headers around f_2
- a secret in git remains in history
- the database user is not a superuser
- Content-Security-Policy names script sources
- nosniff and HTTPS stay headers are part of the response

```text
Content-Security-Policy: default-src 'self'
X-Content-Type-Options: nosniff
env holds the key. the row f_2 does not
least privilege on the role and on the database user
```

- homework
```text
# 5a  rotate after a secret was committed
# 5b  the app user cannot drop the cluster
# 5c  the policy has to match how facts actually loads script
```

- example 6. secrets and headers around u_3
- a secret in git remains in history
- the database user is not a superuser
- Content-Security-Policy names script sources
- nosniff and HTTPS stay headers are part of the response

```text
Content-Security-Policy: default-src 'self'
X-Content-Type-Options: nosniff
env holds the key. the row u_3 does not
least privilege on the role and on the database user
```

- homework
```text
# 6a  rotate after a secret was committed
# 6b  the app user cannot drop the cluster
# 6c  the policy has to match how users actually loads script
```

- example 7. secrets and headers around pay_8
- a secret in git remains in history
- the database user is not a superuser
- Content-Security-Policy names script sources
- nosniff and HTTPS stay headers are part of the response

```text
Content-Security-Policy: default-src 'self'
X-Content-Type-Options: nosniff
env holds the key. the row pay_8 does not
least privilege on the role and on the database user
```

- homework
```text
# 7a  rotate after a secret was committed
# 7b  the app user cannot drop the cluster
# 7c  the policy has to match how payments actually loads script
```

- example 8. secrets and headers around room_2
- a secret in git remains in history
- the database user is not a superuser
- Content-Security-Policy names script sources
- nosniff and HTTPS stay headers are part of the response

```text
Content-Security-Policy: default-src 'self'
X-Content-Type-Options: nosniff
env holds the key. the row room_2 does not
least privilege on the role and on the database user
```

- homework
```text
# 8a  rotate after a secret was committed
# 8b  the app user cannot drop the cluster
# 8c  the policy has to match how rooms actually loads script
```

- example 9. secrets and headers around vs_7
- a secret in git remains in history
- the database user is not a superuser
- Content-Security-Policy names script sources
- nosniff and HTTPS stay headers are part of the response

```text
Content-Security-Policy: default-src 'self'
X-Content-Type-Options: nosniff
env holds the key. the row vs_7 does not
least privilege on the role and on the database user
```

- homework
```text
# 9a  rotate after a secret was committed
# 9b  the app user cannot drop the cluster
# 9c  the policy has to match how vessels actually loads script
```

- example 10. secrets and headers around sc_3
- a secret in git remains in history
- the database user is not a superuser
- Content-Security-Policy names script sources
- nosniff and HTTPS stay headers are part of the response

```text
Content-Security-Policy: default-src 'self'
X-Content-Type-Options: nosniff
env holds the key. the row sc_3 does not
least privilege on the role and on the database user
```

- homework
```text
# 10a  rotate after a secret was committed
# 10b  the app user cannot drop the cluster
# 10c  the policy has to match how scores actually loads script
```

- example 11. secrets and headers around tm_2
- a secret in git remains in history
- the database user is not a superuser
- Content-Security-Policy names script sources
- nosniff and HTTPS stay headers are part of the response

```text
Content-Security-Policy: default-src 'self'
X-Content-Type-Options: nosniff
env holds the key. the row tm_2 does not
least privilege on the role and on the database user
```

- homework
```text
# 11a  rotate after a secret was committed
# 11b  the app user cannot drop the cluster
# 11c  the policy has to match how teams actually loads script
```

- example 12. secrets and headers around up_6
- a secret in git remains in history
- the database user is not a superuser
- Content-Security-Policy names script sources
- nosniff and HTTPS stay headers are part of the response

```text
Content-Security-Policy: default-src 'self'
X-Content-Type-Options: nosniff
env holds the key. the row up_6 does not
least privilege on the role and on the database user
```

- homework
```text
# 12a  rotate after a secret was committed
# 12b  the app user cannot drop the cluster
# 12c  the policy has to match how uploads actually loads script
```

- example 13. secrets and headers around st_1
- a secret in git remains in history
- the database user is not a superuser
- Content-Security-Policy names script sources
- nosniff and HTTPS stay headers are part of the response

```text
Content-Security-Policy: default-src 'self'
X-Content-Type-Options: nosniff
env holds the key. the row st_1 does not
least privilege on the role and on the database user
```

- homework
```text
# 13a  rotate after a secret was committed
# 13b  the app user cannot drop the cluster
# 13c  the policy has to match how standings actually loads script
```

- example 14. secrets and headers around n_2
- a secret in git remains in history
- the database user is not a superuser
- Content-Security-Policy names script sources
- nosniff and HTTPS stay headers are part of the response

```text
Content-Security-Policy: default-src 'self'
X-Content-Type-Options: nosniff
env holds the key. the row n_2 does not
least privilege on the role and on the database user
```

- homework
```text
# 14a  rotate after a secret was committed
# 14b  the app user cannot drop the cluster
# 14c  the policy has to match how notices actually loads script
```

- example 15. secrets and headers around b_3
- a secret in git remains in history
- the database user is not a superuser
- Content-Security-Policy names script sources
- nosniff and HTTPS stay headers are part of the response

```text
Content-Security-Policy: default-src 'self'
X-Content-Type-Options: nosniff
env holds the key. the row b_3 does not
least privilege on the role and on the database user
```

- homework
```text
# 15a  rotate after a secret was committed
# 15b  the app user cannot drop the cluster
# 15c  the policy has to match how brackets actually loads script
```

- example 16. secrets and headers around se_1
- a secret in git remains in history
- the database user is not a superuser
- Content-Security-Policy names script sources
- nosniff and HTTPS stay headers are part of the response

```text
Content-Security-Policy: default-src 'self'
X-Content-Type-Options: nosniff
env holds the key. the row se_1 does not
least privilege on the role and on the database user
```

- homework
```text
# 16a  rotate after a secret was committed
# 16b  the app user cannot drop the cluster
# 16c  the policy has to match how sessions actually loads script
```

- example 17. secrets and headers around q_1
- a secret in git remains in history
- the database user is not a superuser
- Content-Security-Policy names script sources
- nosniff and HTTPS stay headers are part of the response

```text
Content-Security-Policy: default-src 'self'
X-Content-Type-Options: nosniff
env holds the key. the row q_1 does not
least privilege on the role and on the database user
```

- homework
```text
# 17a  rotate after a secret was committed
# 17b  the app user cannot drop the cluster
# 17c  the policy has to match how queues actually loads script
```

- example 18. secrets and headers around r_1
- a secret in git remains in history
- the database user is not a superuser
- Content-Security-Policy names script sources
- nosniff and HTTPS stay headers are part of the response

```text
Content-Security-Policy: default-src 'self'
X-Content-Type-Options: nosniff
env holds the key. the row r_1 does not
least privilege on the role and on the database user
```

- homework
```text
# 18a  rotate after a secret was committed
# 18b  the app user cannot drop the cluster
# 18c  the policy has to match how roles actually loads script
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

- example 1. limit and validate vesselName
- 429 on too many logins
- a flood on the pipe is handled in front of the app
- Zod checks type, length, and range
- the database still has its constraints

```ts
const Body = z.object({
  vesselName: z.string().min(1).max(120),
});
// value Ocean Star for row pc_12
// login limit throws 429 past the budget
```

- homework
```ts
// 1a  status 429
// 1b  the limiter is not the whole answer to a flood
// 1c  max length on vesselName
// 1d  a unique index still rejects a duplicate pc_12
```

- example 2. limit and validate home
- 429 on too many logins
- a flood on the pipe is handled in front of the app
- Zod checks type, length, and range
- the database still has its constraints

```ts
const Body = z.object({
  home: z.string().min(1).max(120),
});
// value Ada for row m_1
// login limit throws 429 past the budget
```

- homework
```ts
// 2a  status 429
// 2b  the limiter is not the whole answer to a flood
// 2c  max length on home
// 2d  a unique index still rejects a duplicate m_1
```

- example 3. limit and validate name
- 429 on too many logins
- a flood on the pipe is handled in front of the app
- Zod checks type, length, and range
- the database still has its constraints

```ts
const Body = z.object({
  name: z.string().min(1).max(120),
});
// value Rajshahi Open for row t_9
// login limit throws 429 past the budget
```

- homework
```ts
// 3a  status 429
// 3b  the limiter is not the whole answer to a flood
// 3c  max length on name
// 3d  a unique index still rejects a duplicate t_9
```

- example 4. limit and validate title
- 429 on too many logins
- a flood on the pipe is handled in front of the app
- Zod checks type, length, and range
- the database still has its constraints

```ts
const Body = z.object({
  title: z.string().min(1).max(120),
});
// value Episode 1 for row v_4
// login limit throws 429 past the budget
```

- homework
```ts
// 4a  status 429
// 4b  the limiter is not the whole answer to a flood
// 4c  max length on title
// 4d  a unique index still rejects a duplicate v_4
```

- example 5. limit and validate kind
- 429 on too many logins
- a flood on the pipe is handled in front of the app
- Zod checks type, length, and range
- the database still has its constraints

```ts
const Body = z.object({
  kind: z.string().min(1).max(120),
});
// value NOR for row f_2
// login limit throws 429 past the budget
```

- homework
```ts
// 5a  status 429
// 5b  the limiter is not the whole answer to a flood
// 5c  max length on kind
// 5d  a unique index still rejects a duplicate f_2
```

- example 6. limit and validate email
- 429 on too many logins
- a flood on the pipe is handled in front of the app
- Zod checks type, length, and range
- the database still has its constraints

```ts
const Body = z.object({
  email: z.string().min(1).max(120),
});
// value a@example.com for row u_3
// login limit throws 429 past the budget
```

- homework
```ts
// 6a  status 429
// 6b  the limiter is not the whole answer to a flood
// 6c  max length on email
// 6d  a unique index still rejects a duplicate u_3
```

- example 7. limit and validate eventId
- 429 on too many logins
- a flood on the pipe is handled in front of the app
- Zod checks type, length, and range
- the database still has its constraints

```ts
const Body = z.object({
  eventId: z.string().min(1).max(120),
});
// value evt_1 for row pay_8
// login limit throws 429 past the budget
```

- homework
```ts
// 7a  status 429
// 7b  the limiter is not the whole answer to a flood
// 7c  max length on eventId
// 7d  a unique index still rejects a duplicate pay_8
```

- example 8. limit and validate sessionId
- 429 on too many logins
- a flood on the pipe is handled in front of the app
- Zod checks type, length, and range
- the database still has its constraints

```ts
const Body = z.object({
  sessionId: z.string().min(1).max(120),
});
// value s_9 for row room_2
// login limit throws 429 past the budget
```

- homework
```ts
// 8a  status 429
// 8b  the limiter is not the whole answer to a flood
// 8c  max length on sessionId
// 8d  a unique index still rejects a duplicate room_2
```

- example 9. limit and validate name
- 429 on too many logins
- a flood on the pipe is handled in front of the app
- Zod checks type, length, and range
- the database still has its constraints

```ts
const Body = z.object({
  name: z.string().min(1).max(120),
});
// value North Wind for row vs_7
// login limit throws 429 past the budget
```

- homework
```ts
// 9a  status 429
// 9b  the limiter is not the whole answer to a flood
// 9c  max length on name
// 9d  a unique index still rejects a duplicate vs_7
```

- example 10. limit and validate points
- 429 on too many logins
- a flood on the pipe is handled in front of the app
- Zod checks type, length, and range
- the database still has its constraints

```ts
const Body = z.object({
  points: z.string().min(1).max(120),
});
// value 11 for row sc_3
// login limit throws 429 past the budget
```

- homework
```ts
// 10a  status 429
// 10b  the limiter is not the whole answer to a flood
// 10c  max length on points
// 10d  a unique index still rejects a duplicate sc_3
```

- example 11. limit and validate name
- 429 on too many logins
- a flood on the pipe is handled in front of the app
- Zod checks type, length, and range
- the database still has its constraints

```ts
const Body = z.object({
  name: z.string().min(1).max(120),
});
// value Blue for row tm_2
// login limit throws 429 past the budget
```

- homework
```ts
// 11a  status 429
// 11b  the limiter is not the whole answer to a flood
// 11c  max length on name
// 11d  a unique index still rejects a duplicate tm_2
```

- example 12. limit and validate key
- 429 on too many logins
- a flood on the pipe is handled in front of the app
- Zod checks type, length, and range
- the database still has its constraints

```ts
const Body = z.object({
  key: z.string().min(1).max(120),
});
// value videos/u_1/a.mp4 for row up_6
// login limit throws 429 past the budget
```

- homework
```ts
// 12a  status 429
// 12b  the limiter is not the whole answer to a flood
// 12c  max length on key
// 12d  a unique index still rejects a duplicate up_6
```

- example 13. limit and validate player
- 429 on too many logins
- a flood on the pipe is handled in front of the app
- Zod checks type, length, and range
- the database still has its constraints

```ts
const Body = z.object({
  player: z.string().min(1).max(120),
});
// value player_a for row st_1
// login limit throws 429 past the budget
```

- homework
```ts
// 13a  status 429
// 13b  the limiter is not the whole answer to a flood
// 13c  max length on player
// 13d  a unique index still rejects a duplicate st_1
```

- example 14. limit and validate port
- 429 on too many logins
- a flood on the pipe is handled in front of the app
- Zod checks type, length, and range
- the database still has its constraints

```ts
const Body = z.object({
  port: z.string().min(1).max(120),
});
// value Chattogram for row n_2
// login limit throws 429 past the budget
```

- homework
```ts
// 14a  status 429
// 14b  the limiter is not the whole answer to a flood
// 14c  max length on port
// 14d  a unique index still rejects a duplicate n_2
```

- example 15. limit and validate round
- 429 on too many logins
- a flood on the pipe is handled in front of the app
- Zod checks type, length, and range
- the database still has its constraints

```ts
const Body = z.object({
  round: z.string().min(1).max(120),
});
// value semi for row b_3
// login limit throws 429 past the budget
```

- homework
```ts
// 15a  status 429
// 15b  the limiter is not the whole answer to a flood
// 15c  max length on round
// 15d  a unique index still rejects a duplicate b_3
```

- example 16. limit and validate userId
- 429 on too many logins
- a flood on the pipe is handled in front of the app
- Zod checks type, length, and range
- the database still has its constraints

```ts
const Body = z.object({
  userId: z.string().min(1).max(120),
});
// value u_3 for row se_1
// login limit throws 429 past the budget
```

- homework
```ts
// 16a  status 429
// 16b  the limiter is not the whole answer to a flood
// 16c  max length on userId
// 16d  a unique index still rejects a duplicate se_1
```

- example 17. limit and validate name
- 429 on too many logins
- a flood on the pipe is handled in front of the app
- Zod checks type, length, and range
- the database still has its constraints

```ts
const Body = z.object({
  name: z.string().min(1).max(120),
});
// value laytime for row q_1
// login limit throws 429 past the budget
```

- homework
```ts
// 17a  status 429
// 17b  the limiter is not the whole answer to a flood
// 17c  max length on name
// 17d  a unique index still rejects a duplicate q_1
```

- example 18. limit and validate name
- 429 on too many logins
- a flood on the pipe is handled in front of the app
- Zod checks type, length, and range
- the database still has its constraints

```ts
const Body = z.object({
  name: z.string().min(1).max(120),
});
// value operator for row r_1
// login limit throws 429 past the budget
```

- homework
```ts
// 18a  status 429
// 18b  the limiter is not the whole answer to a flood
// 18c  max length on name
// 18d  a unique index still rejects a duplicate r_1
```

- example 19. limit and validate vesselName
- 429 on too many logins
- a flood on the pipe is handled in front of the app
- Zod checks type, length, and range
- the database still has its constraints

```ts
const Body = z.object({
  vesselName: z.string().min(1).max(120),
});
// value Ocean Star for row pc_12
// login limit throws 429 past the budget
```

- homework
```ts
// 19a  status 429
// 19b  the limiter is not the whole answer to a flood
// 19c  max length on vesselName
// 19d  a unique index still rejects a duplicate pc_12
```

- example 20. limit and validate home
- 429 on too many logins
- a flood on the pipe is handled in front of the app
- Zod checks type, length, and range
- the database still has its constraints

```ts
const Body = z.object({
  home: z.string().min(1).max(120),
});
// value Ada for row m_1
// login limit throws 429 past the budget
```

- homework
```ts
// 20a  status 429
// 20b  the limiter is not the whole answer to a flood
// 20c  max length on home
// 20d  a unique index still rejects a duplicate m_1
```

- example 21. limit and validate name
- 429 on too many logins
- a flood on the pipe is handled in front of the app
- Zod checks type, length, and range
- the database still has its constraints

```ts
const Body = z.object({
  name: z.string().min(1).max(120),
});
// value Rajshahi Open for row t_9
// login limit throws 429 past the budget
```

- homework
```ts
// 21a  status 429
// 21b  the limiter is not the whole answer to a flood
// 21c  max length on name
// 21d  a unique index still rejects a duplicate t_9
```

- example 22. limit and validate title
- 429 on too many logins
- a flood on the pipe is handled in front of the app
- Zod checks type, length, and range
- the database still has its constraints

```ts
const Body = z.object({
  title: z.string().min(1).max(120),
});
// value Episode 1 for row v_4
// login limit throws 429 past the budget
```

- homework
```ts
// 22a  status 429
// 22b  the limiter is not the whole answer to a flood
// 22c  max length on title
// 22d  a unique index still rejects a duplicate v_4
```

- example 23. limit and validate kind
- 429 on too many logins
- a flood on the pipe is handled in front of the app
- Zod checks type, length, and range
- the database still has its constraints

```ts
const Body = z.object({
  kind: z.string().min(1).max(120),
});
// value NOR for row f_2
// login limit throws 429 past the budget
```

- homework
```ts
// 23a  status 429
// 23b  the limiter is not the whole answer to a flood
// 23c  max length on kind
// 23d  a unique index still rejects a duplicate f_2
```

- example 24. limit and validate email
- 429 on too many logins
- a flood on the pipe is handled in front of the app
- Zod checks type, length, and range
- the database still has its constraints

```ts
const Body = z.object({
  email: z.string().min(1).max(120),
});
// value a@example.com for row u_3
// login limit throws 429 past the budget
```

- homework
```ts
// 24a  status 429
// 24b  the limiter is not the whole answer to a flood
// 24c  max length on email
// 24d  a unique index still rejects a duplicate u_3
```

- example 25. limit and validate eventId
- 429 on too many logins
- a flood on the pipe is handled in front of the app
- Zod checks type, length, and range
- the database still has its constraints

```ts
const Body = z.object({
  eventId: z.string().min(1).max(120),
});
// value evt_1 for row pay_8
// login limit throws 429 past the budget
```

- homework
```ts
// 25a  status 429
// 25b  the limiter is not the whole answer to a flood
// 25c  max length on eventId
// 25d  a unique index still rejects a duplicate pay_8
```

- example 26. limit and validate sessionId
- 429 on too many logins
- a flood on the pipe is handled in front of the app
- Zod checks type, length, and range
- the database still has its constraints

```ts
const Body = z.object({
  sessionId: z.string().min(1).max(120),
});
// value s_9 for row room_2
// login limit throws 429 past the budget
```

- homework
```ts
// 26a  status 429
// 26b  the limiter is not the whole answer to a flood
// 26c  max length on sessionId
// 26d  a unique index still rejects a duplicate room_2
```

- example 27. limit and validate name
- 429 on too many logins
- a flood on the pipe is handled in front of the app
- Zod checks type, length, and range
- the database still has its constraints

```ts
const Body = z.object({
  name: z.string().min(1).max(120),
});
// value North Wind for row vs_7
// login limit throws 429 past the budget
```

- homework
```ts
// 27a  status 429
// 27b  the limiter is not the whole answer to a flood
// 27c  max length on name
// 27d  a unique index still rejects a duplicate vs_7
```

- example 28. limit and validate points
- 429 on too many logins
- a flood on the pipe is handled in front of the app
- Zod checks type, length, and range
- the database still has its constraints

```ts
const Body = z.object({
  points: z.string().min(1).max(120),
});
// value 11 for row sc_3
// login limit throws 429 past the budget
```

- homework
```ts
// 28a  status 429
// 28b  the limiter is not the whole answer to a flood
// 28c  max length on points
// 28d  a unique index still rejects a duplicate sc_3
```

- example 29. limit and validate name
- 429 on too many logins
- a flood on the pipe is handled in front of the app
- Zod checks type, length, and range
- the database still has its constraints

```ts
const Body = z.object({
  name: z.string().min(1).max(120),
});
// value Blue for row tm_2
// login limit throws 429 past the budget
```

- homework
```ts
// 29a  status 429
// 29b  the limiter is not the whole answer to a flood
// 29c  max length on name
// 29d  a unique index still rejects a duplicate tm_2
```

- example 30. limit and validate key
- 429 on too many logins
- a flood on the pipe is handled in front of the app
- Zod checks type, length, and range
- the database still has its constraints

```ts
const Body = z.object({
  key: z.string().min(1).max(120),
});
// value videos/u_1/a.mp4 for row up_6
// login limit throws 429 past the budget
```

- homework
```ts
// 30a  status 429
// 30b  the limiter is not the whole answer to a flood
// 30c  max length on key
// 30d  a unique index still rejects a duplicate up_6
```

- example 31. limit and validate player
- 429 on too many logins
- a flood on the pipe is handled in front of the app
- Zod checks type, length, and range
- the database still has its constraints

```ts
const Body = z.object({
  player: z.string().min(1).max(120),
});
// value player_a for row st_1
// login limit throws 429 past the budget
```

- homework
```ts
// 31a  status 429
// 31b  the limiter is not the whole answer to a flood
// 31c  max length on player
// 31d  a unique index still rejects a duplicate st_1
```

- example 32. limit and validate port
- 429 on too many logins
- a flood on the pipe is handled in front of the app
- Zod checks type, length, and range
- the database still has its constraints

```ts
const Body = z.object({
  port: z.string().min(1).max(120),
});
// value Chattogram for row n_2
// login limit throws 429 past the budget
```

- homework
```ts
// 32a  status 429
// 32b  the limiter is not the whole answer to a flood
// 32c  max length on port
// 32d  a unique index still rejects a duplicate n_2
```

- example 33. limit and validate round
- 429 on too many logins
- a flood on the pipe is handled in front of the app
- Zod checks type, length, and range
- the database still has its constraints

```ts
const Body = z.object({
  round: z.string().min(1).max(120),
});
// value semi for row b_3
// login limit throws 429 past the budget
```

- homework
```ts
// 33a  status 429
// 33b  the limiter is not the whole answer to a flood
// 33c  max length on round
// 33d  a unique index still rejects a duplicate b_3
```

- example 34. limit and validate userId
- 429 on too many logins
- a flood on the pipe is handled in front of the app
- Zod checks type, length, and range
- the database still has its constraints

```ts
const Body = z.object({
  userId: z.string().min(1).max(120),
});
// value u_3 for row se_1
// login limit throws 429 past the budget
```

- homework
```ts
// 34a  status 429
// 34b  the limiter is not the whole answer to a flood
// 34c  max length on userId
// 34d  a unique index still rejects a duplicate se_1
```

- example 35. limit and validate name
- 429 on too many logins
- a flood on the pipe is handled in front of the app
- Zod checks type, length, and range
- the database still has its constraints

```ts
const Body = z.object({
  name: z.string().min(1).max(120),
});
// value laytime for row q_1
// login limit throws 429 past the budget
```

- homework
```ts
// 35a  status 429
// 35b  the limiter is not the whole answer to a flood
// 35c  max length on name
// 35d  a unique index still rejects a duplicate q_1
```

- example 36. limit and validate name
- 429 on too many logins
- a flood on the pipe is handled in front of the app
- Zod checks type, length, and range
- the database still has its constraints

```ts
const Body = z.object({
  name: z.string().min(1).max(120),
});
// value operator for row r_1
// login limit throws 429 past the budget
```

- homework
```ts
// 36a  status 429
// 36b  the limiter is not the whole answer to a flood
// 36c  max length on name
// 36d  a unique index still rejects a duplicate r_1
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

- example 1. lockfile and a reading list
- npm ci installs the pin
- a bug in a parser we feed user input is this week
- a dev-tool note can wait
- do not force-upgrade the tree on a Friday because the count looked bad

```bash
npm ci
npm audit --omit=dev
# review before merge. row pc_12 is unchanged by the audit itself
```

- homework
```bash
# 1a  npm ci respects the lockfile
# 1b  patch a parser we feed from port-calls this week
# 1c  force is not the plan
```

- example 2. lockfile and a reading list
- npm ci installs the pin
- a bug in a parser we feed user input is this week
- a dev-tool note can wait
- do not force-upgrade the tree on a Friday because the count looked bad

```bash
npm ci
npm audit --omit=dev
# review before merge. row m_1 is unchanged by the audit itself
```

- homework
```bash
# 2a  npm ci respects the lockfile
# 2b  patch a parser we feed from matches this week
# 2c  force is not the plan
```

- example 3. lockfile and a reading list
- npm ci installs the pin
- a bug in a parser we feed user input is this week
- a dev-tool note can wait
- do not force-upgrade the tree on a Friday because the count looked bad

```bash
npm ci
npm audit --omit=dev
# review before merge. row t_9 is unchanged by the audit itself
```

- homework
```bash
# 3a  npm ci respects the lockfile
# 3b  patch a parser we feed from tournaments this week
# 3c  force is not the plan
```

- example 4. lockfile and a reading list
- npm ci installs the pin
- a bug in a parser we feed user input is this week
- a dev-tool note can wait
- do not force-upgrade the tree on a Friday because the count looked bad

```bash
npm ci
npm audit --omit=dev
# review before merge. row v_4 is unchanged by the audit itself
```

- homework
```bash
# 4a  npm ci respects the lockfile
# 4b  patch a parser we feed from videos this week
# 4c  force is not the plan
```

- example 5. lockfile and a reading list
- npm ci installs the pin
- a bug in a parser we feed user input is this week
- a dev-tool note can wait
- do not force-upgrade the tree on a Friday because the count looked bad

```bash
npm ci
npm audit --omit=dev
# review before merge. row f_2 is unchanged by the audit itself
```

- homework
```bash
# 5a  npm ci respects the lockfile
# 5b  patch a parser we feed from facts this week
# 5c  force is not the plan
```

- example 6. lockfile and a reading list
- npm ci installs the pin
- a bug in a parser we feed user input is this week
- a dev-tool note can wait
- do not force-upgrade the tree on a Friday because the count looked bad

```bash
npm ci
npm audit --omit=dev
# review before merge. row u_3 is unchanged by the audit itself
```

- homework
```bash
# 6a  npm ci respects the lockfile
# 6b  patch a parser we feed from users this week
# 6c  force is not the plan
```

- example 7. lockfile and a reading list
- npm ci installs the pin
- a bug in a parser we feed user input is this week
- a dev-tool note can wait
- do not force-upgrade the tree on a Friday because the count looked bad

```bash
npm ci
npm audit --omit=dev
# review before merge. row pay_8 is unchanged by the audit itself
```

- homework
```bash
# 7a  npm ci respects the lockfile
# 7b  patch a parser we feed from payments this week
# 7c  force is not the plan
```

- example 8. lockfile and a reading list
- npm ci installs the pin
- a bug in a parser we feed user input is this week
- a dev-tool note can wait
- do not force-upgrade the tree on a Friday because the count looked bad

```bash
npm ci
npm audit --omit=dev
# review before merge. row room_2 is unchanged by the audit itself
```

- homework
```bash
# 8a  npm ci respects the lockfile
# 8b  patch a parser we feed from rooms this week
# 8c  force is not the plan
```

- example 9. lockfile and a reading list
- npm ci installs the pin
- a bug in a parser we feed user input is this week
- a dev-tool note can wait
- do not force-upgrade the tree on a Friday because the count looked bad

```bash
npm ci
npm audit --omit=dev
# review before merge. row vs_7 is unchanged by the audit itself
```

- homework
```bash
# 9a  npm ci respects the lockfile
# 9b  patch a parser we feed from vessels this week
# 9c  force is not the plan
```

- example 10. lockfile and a reading list
- npm ci installs the pin
- a bug in a parser we feed user input is this week
- a dev-tool note can wait
- do not force-upgrade the tree on a Friday because the count looked bad

```bash
npm ci
npm audit --omit=dev
# review before merge. row sc_3 is unchanged by the audit itself
```

- homework
```bash
# 10a  npm ci respects the lockfile
# 10b  patch a parser we feed from scores this week
# 10c  force is not the plan
```

- example 11. lockfile and a reading list
- npm ci installs the pin
- a bug in a parser we feed user input is this week
- a dev-tool note can wait
- do not force-upgrade the tree on a Friday because the count looked bad

```bash
npm ci
npm audit --omit=dev
# review before merge. row tm_2 is unchanged by the audit itself
```

- homework
```bash
# 11a  npm ci respects the lockfile
# 11b  patch a parser we feed from teams this week
# 11c  force is not the plan
```

- example 12. lockfile and a reading list
- npm ci installs the pin
- a bug in a parser we feed user input is this week
- a dev-tool note can wait
- do not force-upgrade the tree on a Friday because the count looked bad

```bash
npm ci
npm audit --omit=dev
# review before merge. row up_6 is unchanged by the audit itself
```

- homework
```bash
# 12a  npm ci respects the lockfile
# 12b  patch a parser we feed from uploads this week
# 12c  force is not the plan
```

- example 13. lockfile and a reading list
- npm ci installs the pin
- a bug in a parser we feed user input is this week
- a dev-tool note can wait
- do not force-upgrade the tree on a Friday because the count looked bad

```bash
npm ci
npm audit --omit=dev
# review before merge. row st_1 is unchanged by the audit itself
```

- homework
```bash
# 13a  npm ci respects the lockfile
# 13b  patch a parser we feed from standings this week
# 13c  force is not the plan
```

- example 14. lockfile and a reading list
- npm ci installs the pin
- a bug in a parser we feed user input is this week
- a dev-tool note can wait
- do not force-upgrade the tree on a Friday because the count looked bad

```bash
npm ci
npm audit --omit=dev
# review before merge. row n_2 is unchanged by the audit itself
```

- homework
```bash
# 14a  npm ci respects the lockfile
# 14b  patch a parser we feed from notices this week
# 14c  force is not the plan
```

- example 15. lockfile and a reading list
- npm ci installs the pin
- a bug in a parser we feed user input is this week
- a dev-tool note can wait
- do not force-upgrade the tree on a Friday because the count looked bad

```bash
npm ci
npm audit --omit=dev
# review before merge. row b_3 is unchanged by the audit itself
```

- homework
```bash
# 15a  npm ci respects the lockfile
# 15b  patch a parser we feed from brackets this week
# 15c  force is not the plan
```

- example 16. lockfile and a reading list
- npm ci installs the pin
- a bug in a parser we feed user input is this week
- a dev-tool note can wait
- do not force-upgrade the tree on a Friday because the count looked bad

```bash
npm ci
npm audit --omit=dev
# review before merge. row se_1 is unchanged by the audit itself
```

- homework
```bash
# 16a  npm ci respects the lockfile
# 16b  patch a parser we feed from sessions this week
# 16c  force is not the plan
```

- example 17. lockfile and a reading list
- npm ci installs the pin
- a bug in a parser we feed user input is this week
- a dev-tool note can wait
- do not force-upgrade the tree on a Friday because the count looked bad

```bash
npm ci
npm audit --omit=dev
# review before merge. row q_1 is unchanged by the audit itself
```

- homework
```bash
# 17a  npm ci respects the lockfile
# 17b  patch a parser we feed from queues this week
# 17c  force is not the plan
```

- example 18. lockfile and a reading list
- npm ci installs the pin
- a bug in a parser we feed user input is this week
- a dev-tool note can wait
- do not force-upgrade the tree on a Friday because the count looked bad

```bash
npm ci
npm audit --omit=dev
# review before merge. row r_1 is unchanged by the audit itself
```

- homework
```bash
# 18a  npm ci respects the lockfile
# 18b  patch a parser we feed from roles this week
# 18c  force is not the plan
```

- example 19. lockfile and a reading list
- npm ci installs the pin
- a bug in a parser we feed user input is this week
- a dev-tool note can wait
- do not force-upgrade the tree on a Friday because the count looked bad

```bash
npm ci
npm audit --omit=dev
# review before merge. row pc_12 is unchanged by the audit itself
```

- homework
```bash
# 19a  npm ci respects the lockfile
# 19b  patch a parser we feed from port-calls this week
# 19c  force is not the plan
```

- example 20. lockfile and a reading list
- npm ci installs the pin
- a bug in a parser we feed user input is this week
- a dev-tool note can wait
- do not force-upgrade the tree on a Friday because the count looked bad

```bash
npm ci
npm audit --omit=dev
# review before merge. row m_1 is unchanged by the audit itself
```

- homework
```bash
# 20a  npm ci respects the lockfile
# 20b  patch a parser we feed from matches this week
# 20c  force is not the plan
```

- example 21. lockfile and a reading list
- npm ci installs the pin
- a bug in a parser we feed user input is this week
- a dev-tool note can wait
- do not force-upgrade the tree on a Friday because the count looked bad

```bash
npm ci
npm audit --omit=dev
# review before merge. row t_9 is unchanged by the audit itself
```

- homework
```bash
# 21a  npm ci respects the lockfile
# 21b  patch a parser we feed from tournaments this week
# 21c  force is not the plan
```

- example 22. lockfile and a reading list
- npm ci installs the pin
- a bug in a parser we feed user input is this week
- a dev-tool note can wait
- do not force-upgrade the tree on a Friday because the count looked bad

```bash
npm ci
npm audit --omit=dev
# review before merge. row v_4 is unchanged by the audit itself
```

- homework
```bash
# 22a  npm ci respects the lockfile
# 22b  patch a parser we feed from videos this week
# 22c  force is not the plan
```

- example 23. lockfile and a reading list
- npm ci installs the pin
- a bug in a parser we feed user input is this week
- a dev-tool note can wait
- do not force-upgrade the tree on a Friday because the count looked bad

```bash
npm ci
npm audit --omit=dev
# review before merge. row f_2 is unchanged by the audit itself
```

- homework
```bash
# 23a  npm ci respects the lockfile
# 23b  patch a parser we feed from facts this week
# 23c  force is not the plan
```

- example 24. lockfile and a reading list
- npm ci installs the pin
- a bug in a parser we feed user input is this week
- a dev-tool note can wait
- do not force-upgrade the tree on a Friday because the count looked bad

```bash
npm ci
npm audit --omit=dev
# review before merge. row u_3 is unchanged by the audit itself
```

- homework
```bash
# 24a  npm ci respects the lockfile
# 24b  patch a parser we feed from users this week
# 24c  force is not the plan
```

- example 25. lockfile and a reading list
- npm ci installs the pin
- a bug in a parser we feed user input is this week
- a dev-tool note can wait
- do not force-upgrade the tree on a Friday because the count looked bad

```bash
npm ci
npm audit --omit=dev
# review before merge. row pay_8 is unchanged by the audit itself
```

- homework
```bash
# 25a  npm ci respects the lockfile
# 25b  patch a parser we feed from payments this week
# 25c  force is not the plan
```

- example 26. lockfile and a reading list
- npm ci installs the pin
- a bug in a parser we feed user input is this week
- a dev-tool note can wait
- do not force-upgrade the tree on a Friday because the count looked bad

```bash
npm ci
npm audit --omit=dev
# review before merge. row room_2 is unchanged by the audit itself
```

- homework
```bash
# 26a  npm ci respects the lockfile
# 26b  patch a parser we feed from rooms this week
# 26c  force is not the plan
```

- example 27. lockfile and a reading list
- npm ci installs the pin
- a bug in a parser we feed user input is this week
- a dev-tool note can wait
- do not force-upgrade the tree on a Friday because the count looked bad

```bash
npm ci
npm audit --omit=dev
# review before merge. row vs_7 is unchanged by the audit itself
```

- homework
```bash
# 27a  npm ci respects the lockfile
# 27b  patch a parser we feed from vessels this week
# 27c  force is not the plan
```

- example 28. lockfile and a reading list
- npm ci installs the pin
- a bug in a parser we feed user input is this week
- a dev-tool note can wait
- do not force-upgrade the tree on a Friday because the count looked bad

```bash
npm ci
npm audit --omit=dev
# review before merge. row sc_3 is unchanged by the audit itself
```

- homework
```bash
# 28a  npm ci respects the lockfile
# 28b  patch a parser we feed from scores this week
# 28c  force is not the plan
```

- example 29. lockfile and a reading list
- npm ci installs the pin
- a bug in a parser we feed user input is this week
- a dev-tool note can wait
- do not force-upgrade the tree on a Friday because the count looked bad

```bash
npm ci
npm audit --omit=dev
# review before merge. row tm_2 is unchanged by the audit itself
```

- homework
```bash
# 29a  npm ci respects the lockfile
# 29b  patch a parser we feed from teams this week
# 29c  force is not the plan
```

- example 30. lockfile and a reading list
- npm ci installs the pin
- a bug in a parser we feed user input is this week
- a dev-tool note can wait
- do not force-upgrade the tree on a Friday because the count looked bad

```bash
npm ci
npm audit --omit=dev
# review before merge. row up_6 is unchanged by the audit itself
```

- homework
```bash
# 30a  npm ci respects the lockfile
# 30b  patch a parser we feed from uploads this week
# 30c  force is not the plan
```

- example 31. lockfile and a reading list
- npm ci installs the pin
- a bug in a parser we feed user input is this week
- a dev-tool note can wait
- do not force-upgrade the tree on a Friday because the count looked bad

```bash
npm ci
npm audit --omit=dev
# review before merge. row st_1 is unchanged by the audit itself
```

- homework
```bash
# 31a  npm ci respects the lockfile
# 31b  patch a parser we feed from standings this week
# 31c  force is not the plan
```

- example 32. lockfile and a reading list
- npm ci installs the pin
- a bug in a parser we feed user input is this week
- a dev-tool note can wait
- do not force-upgrade the tree on a Friday because the count looked bad

```bash
npm ci
npm audit --omit=dev
# review before merge. row n_2 is unchanged by the audit itself
```

- homework
```bash
# 32a  npm ci respects the lockfile
# 32b  patch a parser we feed from notices this week
# 32c  force is not the plan
```

- example 33. lockfile and a reading list
- npm ci installs the pin
- a bug in a parser we feed user input is this week
- a dev-tool note can wait
- do not force-upgrade the tree on a Friday because the count looked bad

```bash
npm ci
npm audit --omit=dev
# review before merge. row b_3 is unchanged by the audit itself
```

- homework
```bash
# 33a  npm ci respects the lockfile
# 33b  patch a parser we feed from brackets this week
# 33c  force is not the plan
```

- example 34. lockfile and a reading list
- npm ci installs the pin
- a bug in a parser we feed user input is this week
- a dev-tool note can wait
- do not force-upgrade the tree on a Friday because the count looked bad

```bash
npm ci
npm audit --omit=dev
# review before merge. row se_1 is unchanged by the audit itself
```

- homework
```bash
# 34a  npm ci respects the lockfile
# 34b  patch a parser we feed from sessions this week
# 34c  force is not the plan
```

- example 35. lockfile and a reading list
- npm ci installs the pin
- a bug in a parser we feed user input is this week
- a dev-tool note can wait
- do not force-upgrade the tree on a Friday because the count looked bad

```bash
npm ci
npm audit --omit=dev
# review before merge. row q_1 is unchanged by the audit itself
```

- homework
```bash
# 35a  npm ci respects the lockfile
# 35b  patch a parser we feed from queues this week
# 35c  force is not the plan
```

- example 36. lockfile and a reading list
- npm ci installs the pin
- a bug in a parser we feed user input is this week
- a dev-tool note can wait
- do not force-upgrade the tree on a Friday because the count looked bad

```bash
npm ci
npm audit --omit=dev
# review before merge. row r_1 is unchanged by the audit itself
```

- homework
```bash
# 36a  npm ci respects the lockfile
# 36b  patch a parser we feed from roles this week
# 36c  force is not the plan
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

- example 1. a scoped test, and a model boundary, for pc_12
- a penetration test is permitted, scoped, and followed by fixes
- we do not point experiments at systems we do not operate
- untrusted model text is data
- tools check the role
- the number comes from the function
- we do not list trick phrases. the boundary holds when the wording changes

```text
scope: hosts we named, test accounts, no denial of service
source id pc_12
tool checks the caller
money comes from laytime(), not from a paragraph
value Ocean Star is data in the user message
```

- homework
```text
# 1a  two roles of test account, the routes, the hosts
# 1b  we do not run this against someone else's system
# 1c  the tool still checks the role for pc_12
# 1d  7500 for 72, 84, and 15000 comes from the function
```

- example 2. a scoped test, and a model boundary, for m_1
- a penetration test is permitted, scoped, and followed by fixes
- we do not point experiments at systems we do not operate
- untrusted model text is data
- tools check the role
- the number comes from the function
- we do not list trick phrases. the boundary holds when the wording changes

```text
scope: hosts we named, test accounts, no denial of service
source id m_1
tool checks the caller
money comes from laytime(), not from a paragraph
value Ada is data in the user message
```

- homework
```text
# 2a  two roles of test account, the routes, the hosts
# 2b  we do not run this against someone else's system
# 2c  the tool still checks the role for m_1
# 2d  7500 for 72, 84, and 15000 comes from the function
```

- example 3. a scoped test, and a model boundary, for t_9
- a penetration test is permitted, scoped, and followed by fixes
- we do not point experiments at systems we do not operate
- untrusted model text is data
- tools check the role
- the number comes from the function
- we do not list trick phrases. the boundary holds when the wording changes

```text
scope: hosts we named, test accounts, no denial of service
source id t_9
tool checks the caller
money comes from laytime(), not from a paragraph
value Rajshahi Open is data in the user message
```

- homework
```text
# 3a  two roles of test account, the routes, the hosts
# 3b  we do not run this against someone else's system
# 3c  the tool still checks the role for t_9
# 3d  7500 for 72, 84, and 15000 comes from the function
```

- example 4. a scoped test, and a model boundary, for v_4
- a penetration test is permitted, scoped, and followed by fixes
- we do not point experiments at systems we do not operate
- untrusted model text is data
- tools check the role
- the number comes from the function
- we do not list trick phrases. the boundary holds when the wording changes

```text
scope: hosts we named, test accounts, no denial of service
source id v_4
tool checks the caller
money comes from laytime(), not from a paragraph
value Episode 1 is data in the user message
```

- homework
```text
# 4a  two roles of test account, the routes, the hosts
# 4b  we do not run this against someone else's system
# 4c  the tool still checks the role for v_4
# 4d  7500 for 72, 84, and 15000 comes from the function
```

- example 5. a scoped test, and a model boundary, for f_2
- a penetration test is permitted, scoped, and followed by fixes
- we do not point experiments at systems we do not operate
- untrusted model text is data
- tools check the role
- the number comes from the function
- we do not list trick phrases. the boundary holds when the wording changes

```text
scope: hosts we named, test accounts, no denial of service
source id f_2
tool checks the caller
money comes from laytime(), not from a paragraph
value NOR is data in the user message
```

- homework
```text
# 5a  two roles of test account, the routes, the hosts
# 5b  we do not run this against someone else's system
# 5c  the tool still checks the role for f_2
# 5d  7500 for 72, 84, and 15000 comes from the function
```

- example 6. a scoped test, and a model boundary, for u_3
- a penetration test is permitted, scoped, and followed by fixes
- we do not point experiments at systems we do not operate
- untrusted model text is data
- tools check the role
- the number comes from the function
- we do not list trick phrases. the boundary holds when the wording changes

```text
scope: hosts we named, test accounts, no denial of service
source id u_3
tool checks the caller
money comes from laytime(), not from a paragraph
value a@example.com is data in the user message
```

- homework
```text
# 6a  two roles of test account, the routes, the hosts
# 6b  we do not run this against someone else's system
# 6c  the tool still checks the role for u_3
# 6d  7500 for 72, 84, and 15000 comes from the function
```

- example 7. a scoped test, and a model boundary, for pay_8
- a penetration test is permitted, scoped, and followed by fixes
- we do not point experiments at systems we do not operate
- untrusted model text is data
- tools check the role
- the number comes from the function
- we do not list trick phrases. the boundary holds when the wording changes

```text
scope: hosts we named, test accounts, no denial of service
source id pay_8
tool checks the caller
money comes from laytime(), not from a paragraph
value evt_1 is data in the user message
```

- homework
```text
# 7a  two roles of test account, the routes, the hosts
# 7b  we do not run this against someone else's system
# 7c  the tool still checks the role for pay_8
# 7d  7500 for 72, 84, and 15000 comes from the function
```

- example 8. a scoped test, and a model boundary, for room_2
- a penetration test is permitted, scoped, and followed by fixes
- we do not point experiments at systems we do not operate
- untrusted model text is data
- tools check the role
- the number comes from the function
- we do not list trick phrases. the boundary holds when the wording changes

```text
scope: hosts we named, test accounts, no denial of service
source id room_2
tool checks the caller
money comes from laytime(), not from a paragraph
value s_9 is data in the user message
```

- homework
```text
# 8a  two roles of test account, the routes, the hosts
# 8b  we do not run this against someone else's system
# 8c  the tool still checks the role for room_2
# 8d  7500 for 72, 84, and 15000 comes from the function
```

- example 9. a scoped test, and a model boundary, for vs_7
- a penetration test is permitted, scoped, and followed by fixes
- we do not point experiments at systems we do not operate
- untrusted model text is data
- tools check the role
- the number comes from the function
- we do not list trick phrases. the boundary holds when the wording changes

```text
scope: hosts we named, test accounts, no denial of service
source id vs_7
tool checks the caller
money comes from laytime(), not from a paragraph
value North Wind is data in the user message
```

- homework
```text
# 9a  two roles of test account, the routes, the hosts
# 9b  we do not run this against someone else's system
# 9c  the tool still checks the role for vs_7
# 9d  7500 for 72, 84, and 15000 comes from the function
```

- example 10. a scoped test, and a model boundary, for sc_3
- a penetration test is permitted, scoped, and followed by fixes
- we do not point experiments at systems we do not operate
- untrusted model text is data
- tools check the role
- the number comes from the function
- we do not list trick phrases. the boundary holds when the wording changes

```text
scope: hosts we named, test accounts, no denial of service
source id sc_3
tool checks the caller
money comes from laytime(), not from a paragraph
value 11 is data in the user message
```

- homework
```text
# 10a  two roles of test account, the routes, the hosts
# 10b  we do not run this against someone else's system
# 10c  the tool still checks the role for sc_3
# 10d  7500 for 72, 84, and 15000 comes from the function
```

- example 11. a scoped test, and a model boundary, for tm_2
- a penetration test is permitted, scoped, and followed by fixes
- we do not point experiments at systems we do not operate
- untrusted model text is data
- tools check the role
- the number comes from the function
- we do not list trick phrases. the boundary holds when the wording changes

```text
scope: hosts we named, test accounts, no denial of service
source id tm_2
tool checks the caller
money comes from laytime(), not from a paragraph
value Blue is data in the user message
```

- homework
```text
# 11a  two roles of test account, the routes, the hosts
# 11b  we do not run this against someone else's system
# 11c  the tool still checks the role for tm_2
# 11d  7500 for 72, 84, and 15000 comes from the function
```

- example 12. a scoped test, and a model boundary, for up_6
- a penetration test is permitted, scoped, and followed by fixes
- we do not point experiments at systems we do not operate
- untrusted model text is data
- tools check the role
- the number comes from the function
- we do not list trick phrases. the boundary holds when the wording changes

```text
scope: hosts we named, test accounts, no denial of service
source id up_6
tool checks the caller
money comes from laytime(), not from a paragraph
value videos/u_1/a.mp4 is data in the user message
```

- homework
```text
# 12a  two roles of test account, the routes, the hosts
# 12b  we do not run this against someone else's system
# 12c  the tool still checks the role for up_6
# 12d  7500 for 72, 84, and 15000 comes from the function
```

- example 13. a scoped test, and a model boundary, for st_1
- a penetration test is permitted, scoped, and followed by fixes
- we do not point experiments at systems we do not operate
- untrusted model text is data
- tools check the role
- the number comes from the function
- we do not list trick phrases. the boundary holds when the wording changes

```text
scope: hosts we named, test accounts, no denial of service
source id st_1
tool checks the caller
money comes from laytime(), not from a paragraph
value player_a is data in the user message
```

- homework
```text
# 13a  two roles of test account, the routes, the hosts
# 13b  we do not run this against someone else's system
# 13c  the tool still checks the role for st_1
# 13d  7500 for 72, 84, and 15000 comes from the function
```

- example 14. a scoped test, and a model boundary, for n_2
- a penetration test is permitted, scoped, and followed by fixes
- we do not point experiments at systems we do not operate
- untrusted model text is data
- tools check the role
- the number comes from the function
- we do not list trick phrases. the boundary holds when the wording changes

```text
scope: hosts we named, test accounts, no denial of service
source id n_2
tool checks the caller
money comes from laytime(), not from a paragraph
value Chattogram is data in the user message
```

- homework
```text
# 14a  two roles of test account, the routes, the hosts
# 14b  we do not run this against someone else's system
# 14c  the tool still checks the role for n_2
# 14d  7500 for 72, 84, and 15000 comes from the function
```

- example 15. a scoped test, and a model boundary, for b_3
- a penetration test is permitted, scoped, and followed by fixes
- we do not point experiments at systems we do not operate
- untrusted model text is data
- tools check the role
- the number comes from the function
- we do not list trick phrases. the boundary holds when the wording changes

```text
scope: hosts we named, test accounts, no denial of service
source id b_3
tool checks the caller
money comes from laytime(), not from a paragraph
value semi is data in the user message
```

- homework
```text
# 15a  two roles of test account, the routes, the hosts
# 15b  we do not run this against someone else's system
# 15c  the tool still checks the role for b_3
# 15d  7500 for 72, 84, and 15000 comes from the function
```

- example 16. a scoped test, and a model boundary, for se_1
- a penetration test is permitted, scoped, and followed by fixes
- we do not point experiments at systems we do not operate
- untrusted model text is data
- tools check the role
- the number comes from the function
- we do not list trick phrases. the boundary holds when the wording changes

```text
scope: hosts we named, test accounts, no denial of service
source id se_1
tool checks the caller
money comes from laytime(), not from a paragraph
value u_3 is data in the user message
```

- homework
```text
# 16a  two roles of test account, the routes, the hosts
# 16b  we do not run this against someone else's system
# 16c  the tool still checks the role for se_1
# 16d  7500 for 72, 84, and 15000 comes from the function
```

- example 17. a scoped test, and a model boundary, for q_1
- a penetration test is permitted, scoped, and followed by fixes
- we do not point experiments at systems we do not operate
- untrusted model text is data
- tools check the role
- the number comes from the function
- we do not list trick phrases. the boundary holds when the wording changes

```text
scope: hosts we named, test accounts, no denial of service
source id q_1
tool checks the caller
money comes from laytime(), not from a paragraph
value laytime is data in the user message
```

- homework
```text
# 17a  two roles of test account, the routes, the hosts
# 17b  we do not run this against someone else's system
# 17c  the tool still checks the role for q_1
# 17d  7500 for 72, 84, and 15000 comes from the function
```

- example 18. a scoped test, and a model boundary, for r_1
- a penetration test is permitted, scoped, and followed by fixes
- we do not point experiments at systems we do not operate
- untrusted model text is data
- tools check the role
- the number comes from the function
- we do not list trick phrases. the boundary holds when the wording changes

```text
scope: hosts we named, test accounts, no denial of service
source id r_1
tool checks the caller
money comes from laytime(), not from a paragraph
value operator is data in the user message
```

- homework
```text
# 18a  two roles of test account, the routes, the hosts
# 18b  we do not run this against someone else's system
# 18c  the tool still checks the role for r_1
# 18d  7500 for 72, 84, and 15000 comes from the function
```
