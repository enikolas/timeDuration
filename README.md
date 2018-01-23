# timeDuration

[![Build Status](https://travis-ci.org/msandrini/timeDuration.svg?branch=master)](https://travis-ci.org/msandrini/timeDuration)
[![Greenkeeper badge](https://badges.greenkeeper.io/msandrini/timeDuration.svg)](https://greenkeeper.io/)
[![codecov](https://codecov.io/gh/msandrini/timeDuration/branch/master/graph/badge.svg)](https://codecov.io/gh/msandrini/timeDuration)
[![Known Vulnerabilities](https://snyk.io/test/github/msandrini/timeduration/badge.svg?targetFile=package.json)](https://snyk.io/test/github/msandrini/timeduration?targetFile=package.json)
[![Maintainability](https://api.codeclimate.com/v1/badges/1acb70e8ab867c9e94e0/maintainability)](https://codeclimate.com/github/msandrini/timeDuration/maintainability)


Library to handle simple hour/minute times

## installation

`npm i time-duration` with `--save-dev` if desired


## usage

This lib is based on an instantiable class, to deal with time in the scope of minutes and hours. It supports time to be supplied to it in 4 ways:

```javascript
const td = new TimeDuration('2:30'); // string with hours and minutes
const td = new TimeDuration({ hours: 2, minutes: 30 }); // object
const td = new TimeDuration(2, 30); // two parameters: hours, minutes
const td = new TimeDuration(210); // number of minutes
```

With this class instantiated, one can process time calculations with minutes and hours and output it as a number of formats. The formats are as follows:

```javascript
const td = new TimeDuration(2, 30);
console.log(td); // outputs "2:30", equivalent of td.toString()
console.log(td + 0); // outputs 210 (integer), equivalent of td.valueOf()
console.log(td.toMinutes()); // outputs 210 just as above
console.log(td.toHours(1)); // outputs 2.5 (float -the parameter tells the round precision)
console.log(td.toObject()); // outputs an object { hours: 2, minutes: 30 }
```

The processing functions built out of the box:
_(On *add* and *subtract* the parameter will be converted to a TimeDuration)_
_(On *multiply* and *divide* the parameter will be the multiplication/division factor)_

```javascript
const td = new TimeDuration(2, 30);

console.log(td.add(10)); // outputs "2:40"
console.log(td.add('1:00')); // outputs "3:30"
console.log(td.subtract(1, 0)); // outputs "1:30"
console.log(td.subtract({ hours: 0, minutes: 20 })); // outputs "2:10"
console.log(td.multiply(3)); // outputs "7:30"
console.log(td.divide(2)); // outputs "1:15"
```

Alternatively, we can do mathematical operations with TimeDurations

```javascript
const td1 = new TimeDuration(1, 20);
const td2 = new TimeDuration(1, 00);
console.log(td1 + td2); // outputs 140 (integer)
console.log(new TimeDuration(td1 - td2)); // outputs "0:20"
```

## Linting only

```
npm run lint
```

## Testing

```
npm test
```