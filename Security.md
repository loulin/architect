## HTTPS
Free SSL agent: [StartSSL™](http://www.startssl.com/)

## Password
Use a single field `password` in db with generated salt:
```js
var bcrypt = require('bcryptjs');
bcrypt.genSalt(...);
bcrypt.hash(password, salt);
```
Compare password:
```js
bcrypt.compare(user.password, req.body.password);
```

## CSRF

## XSS

## SQL Injection

## DoS

## Best Practices
- Subscribe [Node Security Project](https://nodesecurity.io/)
- Find out out-of-date modules by [retire](https://www.npmjs.com/package/retire) module
- Select reliable packages. Try `npm-dependents` module
- Shrinkwrapping production dependencies with `shrinkwrap`
- `helmet` module can help to protect against common web attacks like XSS
