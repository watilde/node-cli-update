
# cli-update

 [![PayPal](https://img.shields.io/badge/%24-paypal-f39c12.svg)][paypal-donations] [![AMA](https://img.shields.io/badge/ask%20me-anything-1abc9c.svg)](https://github.com/IonicaBizau/ama) [![Version](https://img.shields.io/npm/v/cli-update.svg)](https://www.npmjs.com/package/cli-update) [![Downloads](https://img.shields.io/npm/dt/cli-update.svg)](https://www.npmjs.com/package/cli-update) [![Get help on Codementor](https://cdn.codementor.io/badges/get_help_github.svg)](https://www.codementor.io/johnnyb?utm_source=github&utm_medium=button&utm_term=johnnyb&utm_campaign=github)

> A library to update stdout output.

## :cloud: Installation

```sh
$ npm i --save cli-update
```


## :clipboard: Example



```js
// Dependencies
var CliUpdate = require("cli-update")
  , CliBox = require("cli-box")
  , Couleurs = require("couleurs")()
  , Figlet = require("figlet")
  ;

// http://stackoverflow.com/a/16426519/1420197
function getDateTime() {

    var date = new Date();

    var hour = date.getHours();
    hour = (hour < 10 ? "0" : "") + hour;

    var min  = date.getMinutes();
    min = (min < 10 ? "0" : "") + min;

    var sec  = date.getSeconds();
    sec = (sec < 10 ? "0" : "") + sec;

    return hour + " : " + min + " : " + sec;
}

// Render time in a fancy format
setInterval(function () {
    Figlet(getDateTime(), function(err, data) {
        data = data.split("\n").map(function (c) { return Couleurs.bg(c, "#c0392b") + "\u001b[45m"; }).join("\n");
        CliUpdate.render(
            CliBox({
                fullscreen: true
              , marks: {}
            }, data).split("\n").map(function (c) {
                return Couleurs.bg(c, "#2980b9");
            }).join("\n")
        );
    });
}, 1000);
```

## :memo: Documentation


### `render(output, pushHistory, data, emitChanged)`
Render the current output.

#### Params
- **String** `output`: The output that should be printed in stdout.
- **Boolean** `pushHistory`: Push or not push the output in history (default: true).
- **Object** `data`:
- **Boolean** `emitChanged`: Call or not call the changed handler (deafult: true).

#### Return
- **Object** The CliUpdate object.

### `back()`
Go to the previous output in the history.

#### Return
- **Object** The CliUpdate object.

### `next()`
Go to the next output in the history.

#### Return
- **Object** The CliUpdate object.



## :yum: How to contribute
Have an idea? Found a bug? See [how to contribute][contributing].


## :scroll: License

[MIT][license] © [Ionică Bizău][website]

[paypal-donations]: https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=RVXDDLKKLQRJW
[donate-now]: http://i.imgur.com/6cMbHOC.png

[license]: http://showalicense.com/?fullname=Ionic%C4%83%20Biz%C4%83u%20%3Cbizauionica%40gmail.com%3E%20(http%3A%2F%2Fionicabizau.net)&year=2014#license-mit
[website]: http://ionicabizau.net
[contributing]: /CONTRIBUTING.md
[docs]: /DOCUMENTATION.md
