# Config
Config module is flexible for Node.js, while json/yaml/xml config file is platform independant.

Use nconf

## Examples:
config.development.js
```javascript
module.exports = {
  server: {
    host: '127.0.0.1',
    port: 2368
  },
  mysql: {
    host: '127.0.0.1',
    database: 'demo',
    user: 'demo',
    password: '850119',
    charset: 'utf8'
  },
  mongodb: {
    url: 'mongodb://localhost:27017/demo'
  },
  sessionSecret: 'loulin',
  debug: true
};
```

config.js
```javascript
process.env.NODE_ENV = process.env.NODE_ENV || 'development';
module.exports = (function (env) {
  var config = {};
  switch (env) {
    case 'production':
      config = require('../config.production');
      break;
    case 'development':
      config = require('../config.development');
      break;
    case 'testing':
      config = require('../config.testing');
      break;
    case 'staging':
      config = require('../config.staging');
      break;
    default:
      console.error('NODE_ENV environment variable not set');
      process.exit(1);
  }
  return config;
})(process.env.NODE_ENV);
```
