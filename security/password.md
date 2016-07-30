
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
