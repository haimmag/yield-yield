# var o_o = yield (yield)(); [![Build Status](https://travis-ci.org/nemisj/yield-yield.svg?branch=master)](https://travis-ci.org/nemisj/yield-yield)

[![NPM](https://nodei.co/npm/yield-yield.png)](https://npmjs.org/package/yield-yield)

Double yield ( yield-yield ) helps you to organize asynchronously written code by structuring it sequentially without need to wrap or change your existing code.

```javascript
var superagent = require('superagent');
var o_o = require('yield-yield');
var fs = require('fs');

module.exports = o_o(function *() {

    //
    // Read file from fs
    //
    try {
      var content = yield fs.readFile('/etc/hosts', { encoding: 'utf8'}, yield);
    } catch (e) {
      console.log('Unable to read file', e);
    }

    //
    // Pause for a second
    //
    yield setTimeout(yield, 1000);

    //
    // Make the request to the server
    //
    var response = yield superagent
      .get('/api/pet')
      .end(yield);

    //
    // Do some more  async stuff
    //

});
```

[Read full Documentation](./docs)

* [API](./docs/API.md)
* [Using together with babel](./docs/babel.md)
* [Using together with mocha](./docs/mocha.md)
