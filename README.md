<div align="center">
  <h1>functions-tools</h1>
  <p>
    <a href="https://www.npmjs.com/package/functions-tools"><img src="https://img.shields.io/npm/v/functions-tools?maxAge=3600" alt="NPM version" /></a>
    <a href="https://www.npmjs.com/package/functions-tools"><img src="https://img.shields.io/npm/dt/functions-tools?maxAge=3600" alt="NPM downloads" /></a>
  </p>
  <p>
    <a href="https://www.npmjs.com/package/functions-tools"><img src="https://nodei.co/npm/functions-tools.png?downloads=true&stars=true" alt="NPM Banner"></a>
  </p>
</div>

# Table of contents

- [Installation](#installation)
- [Example Usage](#examples)

# Installation
```shContact
npm i functions-tools
```

# Examples
```js
const ft = require('functions-tools'); //Define the functions-tools module
```
#### Fonctions Times
```js
ft.stringifyTime(4800000); // 1h, 20m
ft.stringifyTime(4800000, {lang: "en", long: true, separator: " | "}); // 1 hour | 20 minutes
ft.stringifyTime(4800000, {lang: "en", valueNull: true, format: "Y-MO-W-D-H-M-S-MS"}); // 0y, 0mo, 0w, 0d, 1h, 20m, 0s, 0ms
ft.stringifyTime(4800000, {lang: "en", format: "M-H-MS"}); // 20m, 1h
ft.stringifyTime(4800000, {lang: "en", suppressTag: true}); // 1, 20

ft.parseTime("2d"); // 172800000
ft.parseTime("2d",{ms: false}); // 172800
ft.parseTime("2day 5m 3hour"); // 183900000
ft.parseTime("2day -1d"); // 86400000
ft.parseTime("-2d"); // -172800000

await ft.wait(5000); 
// {startTime: 1623327459766, endTime: 1623327464766, durationTime: 5000}
await ft.wait("5s 10s -1s");
// {startTime: 1623327464827, endTime: 1623327478827, durationTime: 14000}
 
ft.formatTime(Date.now()); // june 10th 2021, 22:46:10
ft.formatTime("10/06/2021"); // june 10th 2021, 00:00:00
ft.formatTime("10/06/2021", {lang: "en", format: "Do MM, YYYY | hh:mm"}); // 06th Oct, 2021 | 00:00
```
#### Fonctions Number
```js
ft.numberToRoman(24); // XXIV

ft.romanToNumber("XXIV"); // 24
```
#### Fonctions Text
```js
ft.replaceText("Hello {user}", {user: "NewGlace"}) //Hello NewGlace
ft.replaceText("Hello {user} {suffix}", {user: "NewGlace", suffix: "vanilla"}) //Hello NewGlace vanilla
ft.replaceText("Hello {user}", {user: "NewGlace {suffix}", suffix: "vanilla"}) //Hello NewGlace vanilla
```
#### Fonctions Array
```js
ft.findArray(["H",["E",["L"],"L"],"O,"," ","W",["O",["R",["L"]]],"D"], "L");
// Map(1) { 0 => [ 1, 1, 0 ] }
ft.findArray(["H",["E",["L"],"L"],"O,"," ","W",["O",["R",["L"]]],"D"], "L", {all: true});
// Map(3) { 0 => [ 1, 1, 0 ], 1 => [ 1, 1, 2 ], 2 => [ 1, 5, 1, 1, 0 ] }
ft.findArray(["H",["E",["L"],"L"],"O,"," ","W",["O",["R",["L"]]],"D"], "P");
// Map(0) {}

ft.randomArray(["A","B","C"]); // B
ft.randomArray(["A","B","C"], {number: 4}); // ["C", "A", "B", "A"]
ft.randomArray(["A","B","C"], {number: 4, double: false}); // ["A", "C", "B"]

//To shuffle an array
const array = [1,2,3,4,5,6,7,8,9,0];
ft.randomArray(array, {number: array.length, double: false});
// [4, 3, 7, 0, 5, 6, 2, 1, 9, 8]
```
#### Fonctions multiFunctions
```js
ft.multiFunctions(ft.numberToRoman, [10, 34, 54]);
await ft.multiFunctions(ft.numberToRoman, [10, 34, 54], async: true);
// Promise { [ 'X', 'XXXIV', 'LIV' ] }

ft.multiFunctions(ft.replaceText, [["Hello {x}", {x: "World"}],["Hi {u}", {u: "World"}],["Bye {p}", {p: "World"}]]);
await ft.multiFunctions(ft.replaceText, [["Hello {x}", {x: "World"}],["Hi {u}", {u: "World"}],["Bye {p}", {p: "World"}]], async: true); 
//Promise { [ 'Hello World', 'Hi World', 'Bye World' ] }
```
# Discord
Join the [Discord](https://discord.gg/kH4X6MHu7T)