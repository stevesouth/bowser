## Bowser
A Browser detector. Because sometimes, there is no other way, and not even good modern browsers always provide good feature detection mechanisms.

[![bowser ci](https://secure.travis-ci.org/ded/bowser.png)](https://travis-ci.org/ded/bowser/)

So... it works like this:

``` js
if (bowser.msie && bowser.version <= 6) {
  alert('Hello China');
}
```

## 1.0.0 breaking changes
`browser = require('bowser').browser;` becomes `browser = require('bowser');`

## Bowser Flags
Your mileage may vary, but these flags should be set.  See Contributing below.

``` js
alert('Hello ' + bowser.name + ' ' + bowser.version);
```

### All detected browsers
These flags are set for all detected browsers:

* `name` - A human readable name for this browser.  E.g. 'Chrome', ''
* `version` - Version number for the browser.  E.g. '32.0'

For unknown browsers, Bowser makes a best guess from the UA string.  So, these may not be set.

### Engine flags
If detected, one of these flags may be set to true:

  * `webkit` - Chrome, Android, iOs, BB, etc.
  * `gecko` - Firefox, etc.
  * `msie`  - IE <= 11
  * `msedge` - IE > 11

Safari, Chrome and some other minor browsers will report that they have `webkit` engines.
Firefox and Seamonkey will report that they have `gecko` engines.

``` js
if (bowser.webkit) {
  // do stuff with safari & chrome & opera & android & blackberry & webos & silk
}
```

### Device flags
If detected, one of these flags may be set to true:

  * `mobile` - All detected mobile OSes are additionally flagged `mobile`, **unless it's a tablet**
  * `tablet` - If a tablet device is detected, the flag `tablet` is **set instead of `mobile`**.

### Browser flags
If detected, one of these flags may be set to true.  The engine flag is shown in []'s:

  * `chrome` - [`webkit`]
  * `firefox` - [`gecko`]
  * `msie`
  * `msedge`
  * `safari` - [`webkit`]
  * `android` - native browser - [`webkit`]
  * `ios` - native browser - [`webkit`]
  * `opera` - [`webkit` if >12]
  * `phantom` - [`webkit`]
  * `blackberry` - native browser - [`webkit`]
  * `webos` - native browser - [`webkit`]
  * `silk` - Amazon Kindle browser  - [`webkit`]
  * `bada` - [`webkit`]
  * `tizen` - [`webkit`]
  * `seamonkey` - [`gecko`]
  * `sailfish` - [`gecko`]

For all detected browsers the browser version is set in the `version` field.

### OS Flags
If detected, one of these flags may be set to true:

  * `mac`
  * `windows` - other than Windows Phone
  * `windowsphone`
  * `linux` - other than `android`, `chromeos`, `webos`, `tizen`, and `sailfish`
  * `chromeos`
  * `android`
  * `ios` - also sets one of `iphone`/`ipad`/`ipod`
  * `blackberry`
  * `firefoxos`
  * `webos` - may also set `touchpad`
  * `bada`
  * `tizen`
  * `sailfish`

`osversion` may also be set:

  * `osversion` - for Android, iOS, Windows Phone, WebOS, Bada, and Tizen.  If included in UA string.

iOS is always reported as `ios` and additionally as `iphone`/`ipad`/`ipod`, whichever one matches best.
If WebOS device is an HP TouchPad the flag `touchpad` is additionally set.

### Browser capability grading
One of these flags may be set:

  * `a` - This browser has full capabilities
  * `c` - This browser has degraded capabilities.  Serve simpler version
  * `x` - This browser has minimal capabilities and is probably not well detected.

There is no `b`.  For unknown browsers, none of these flags may be set.

### Ender Support

`package.json`

``` json
"dependencies": {
  "bowser": "x.x.x"
}
```

``` js
if (require('bowser').chrome) {
  alert('Hello Silicon Valley')
}
```

### Contributing
If you'd like to contribute a change to bowser, modify the files in `src/`, then run the following (you'll need node + npm installed):

``` sh
$ npm install
$ make test
```

Please do not check-in the built files `bowser.js` and `bowser.min.js` in pull requests.

### Adding tests
See the list in `src/useragents.js` with example user agents and their expected bowser object.

Whenever you add support for new browsers or notice a bug / mismatch, please update the list and
check if all tests are still passing.

### License
Licensed as MIT. All rights not explicitly granted in the MIT license are reserved. See the included LICENSE file for more details.
