cpu-status
========



**Note:** This repo can be found on npm here: [cpu-status](https://www.npmjs.com/package/cpu-status)

**Note:** This repo can be found on github here: [cpu-status](https://github.com/Milcondev/Node-cpu-status)

**Note:** This module only relies on the `os` module, so it should be compatible on all OS's where Node.js runs.

Install
-------

```
npm i cpu-status
```

Examples
--------

Require the module:
```
var cpustatus = require('cpu-status');
```

By default `usagePercent()` returns cpu usage percent for all cores over a period of the next 1000ms:
```
cpustatus.usagePercent(function(err, percent, seconds) {
    if (err) {
      return console.log(err);
    }

    //the percentage cpu usage over all cores
    console.log(percent);

    //the approximate number of seconds the sample was taken over
    console.log(seconds);
});
```

Get the cpu usage percent for core 0 over a sample period of 2000ms:
```
cpuStat.usagePercent({
    coreIndex: 0,
    sampleMs: 2000,
  },
  function(err, percent, seconds) {
    if (err) {
      return console.log(err);
    }

    //the percentage cpu usage for core 0
    console.log(percent);

    //the approximate number of seconds the sample was taken over (~2 seconds)
    console.log(seconds);
});
```

Get the total number of cores:
```
var totalCores = cpustatus.totalCores();
console.log(totalCores);
```

Get the average clock MHz over all cores:
```
var avgClockMHz = cpustatus.avgClockMHz();
console.log(avgClockMHz);
```

Get the clock MHz for core with index 2:
```
var avgClockMHzCore2 = cpustatus.clockMHz(2);
console.log(avgClockMHzCore2);
```

usagePercent([opts,] cb)
----------------------

Provides a callback `cb(err, percent, seconds)` giving the `percent` cpu usage and `seconds` the length of the sample time, or an error `err`

Option               | Type         | Default            | Explanation
-------------------- | -------------| ------------------ | ------------
opts                 | `Object`     | see below          | Options object, specify what you need the defaults will be filled in
opts.coreIndex       | `Number`     | all cores          | The index of the core to calculate the usage on. Can use any integer `coreIndex` such that `0 >= coreIndex < memStat.totalCores()`
opts.sampleMs        | `String`     | `1000`             | `sampleMs` is the amount of time to take the measurement over
cb                   | `Function`   | none               | Callback which has signature `cb(err, percent, seconds)`

totalCores()
------------

Returns the total number of cores available on the cpu

clockMHz(coreIndex)
-------------------

Returns the clock speed in MHz of core with index `coreIndex`

Option               | Type         | Default            | Explanation
-------------------- | -------------| ------------------ | ------------
coreIndex            | `Number`     | none               | The index of the core to calculate the usage on. Can use any integer `coreIndex` such that `0 >= coreIndex < memStat.totalCores()`

avgClockMHz()
-------------

Returns the average clock speed in MHz over all cores

Contributing
------------

Just send a PR, or create an issue if you are not sure.

Areas ripe for contribution:
- testing
- performance
- bugs



License
-------

MIT
