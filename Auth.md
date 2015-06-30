# Authentication

## Access Token VS Session

## Passport Strategy
```js
var LocalStrategy = require('passport-local').Strategy;
var WeixinStrategy = require('passport-weixin');
var WechatStrategy = require('passport-wechat');
```

# Authorization

## Authorization DB Boilerplate

There are 3 types of permission structures.

### Permissions - Roles - Users

It has Many to Many to Many relations. Users can belong to multiple roles, so it's a little complex to build the system. But this brings convenience for client management.

### Permissions - Roles

Roles and Permissions are many to many relation. But every user can only belong to one role. For previous structure, different roles many have overlapped permissions. For this one, user can get all permissions by one query.

### Permissions - Users

No roles involved. One user can have many permissions. It is easy to understand and implement. In most cases this structure is enough, especially for medium and small projects, because usually the admin team only has several persons, maybe one for each role or module.
