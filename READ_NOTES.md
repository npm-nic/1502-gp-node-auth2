# Using JSON Web Tokens (JWT)

- Today's [Training Kit](https://learn.lambdaschool.com/web4node/module/reciCHdNjavSKaaLt/#guided-project)

---

:question: What is a HTTP Cookie :question:

> A small package of data used to exchange information between the server and client

- just some data saved in storage on the server

- re-watch [ 10:11 - 10:16 Luis-Time ] :eyes:

note :memo:

- cannot really do a logout with JWT
  - have white/black lists on server & check JWT against it
  - once you are doing this...think about using sessions

why did we use sessions yesterday :question:

- credit card + server
- JWT is cash

what did we use bcrypt for :question:

- hashing strings
- password stuff ... unrelated to sessions and JWT

We don't talk about them, but there are multiple types of tokens

- JWT -- access token
- Identity Tokens
  - google & other services
- refresh tokens
  - [ 10:28 Luis-Time]

---

Set it up in [auth-router](auth/auth-router.js)

- [ 10:33 - 10:43 Luis Time ]

- `npm i jsonwebtoken` + import at top

- inside login endpoint

  - `const token = signToken(user)`
  - return it to client

- build out signToken()

  ```javascript
  function signToken(user) {
    const payload = {
      subject: user.id,
      username: user.username,
      role: user.role,
    };
    const secret = process.env.JWT_SECRET || `it's a secret, very safe..`;
    const options = {
      expiresIn: `1d`,
    };
    return jwt.sign(payload, secret, options);
  }
  ```

`knex migrate:latest`
`knex seed:run`
