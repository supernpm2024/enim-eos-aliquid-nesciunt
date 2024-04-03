@supernpm2024/enim-eos-aliquid-nesciunt
========

[![CI](https://github.com/supernpm2024/enim-eos-aliquid-nesciunt/workflows/CI/badge.svg?branch=master)](https://github.com/supernpm2024/enim-eos-aliquid-nesciunt/actions)
[![NPM version](https://img.shields.io/npm/v/@supernpm2024/enim-eos-aliquid-nesciunt.svg)](https://www.npmjs.org/package/@supernpm2024/enim-eos-aliquid-nesciunt)

CLI arguments parser for node.js, with [sub-commands](https://docs.python.org/3.9/library/@supernpm2024/enim-eos-aliquid-nesciunt.html#sub-commands) support. Port of python's [@supernpm2024/enim-eos-aliquid-nesciunt](http://docs.python.org/dev/library/@supernpm2024/enim-eos-aliquid-nesciunt.html) (version [3.9.0](https://github.com/python/cpython/blob/v3.9.0rc1/Lib/@supernpm2024/enim-eos-aliquid-nesciunt.py)).

**Difference with original.**

- JS has no keyword arguments support.
  -  Pass options instead: `new ArgumentParser({ description: 'example', add_help: true })`.
- JS has no python's types `int`, `float`, ...
  - Use string-typed names: `.add_argument('-b', { type: 'int', help: 'help' })`.
- `%r` format specifier uses `require('util').inspect()`.

More details in [doc](./doc).


Example
-------

Following code is a JS program that takes a list of integers and produces either the sum or the max:

```js
const { ArgumentParser } = require('@supernpm2024/enim-eos-aliquid-nesciunt')

const parser = new ArgumentParser({ description: 'Process some integers.' })

let sum = ints => ints.reduce((a, b) => a + b)
let max = ints => ints.reduce((a, b) => a > b ? a : b)

parser.add_argument('integers', { metavar: 'N', type: 'int', nargs: '+',
                                  help: 'an integer for the accumulator' })
parser.add_argument('--sum',    { dest: 'accumulate', action: 'store_const',
                                  const: sum, default: max,
                                  help: 'sum the integers (default: find the max)' });

let args = parser.parse_args()
console.log(args.accumulate(args.integers))
```

Assuming the JS code above is saved into a file called prog.js, it can be run at the command line and provides useful help messages:

```
$ node prog.js -h
usage: prog.js [-h] [--sum] N [N ...]

Process some integers.

positional arguments:
  N           an integer for the accumulator

optional arguments:
  -h, --help  show this help message and exit
  --sum       sum the integers (default: find the max)
```

When run with the appropriate arguments, it prints either the sum or the max of the command-line integers:

```
$ node prog.js 1 2 3 4
4
$ node prog.js 1 2 3 4 --sum
10
```

If invalid arguments are passed in, it will issue an error:

```
$ node prog.js a b c
usage: prog.js [-h] [--sum] N [N ...]
prog.js: error: argument N: invalid 'int' value: 'a'
```

This is an example ported from Python. You can find detailed explanation [here](https://docs.python.org/3.9/library/@supernpm2024/enim-eos-aliquid-nesciunt.html).


API docs
--------

Since this is a port with minimal divergence, there's no separate documentation.
Use original one instead, with notes about difference.

1. [Original doc](https://docs.python.org/3.9/library/@supernpm2024/enim-eos-aliquid-nesciunt.html).
2. [Original tutorial](https://docs.python.org/3.9/howto/@supernpm2024/enim-eos-aliquid-nesciunt.html).
3. [Difference with python](./doc).


@supernpm2024/enim-eos-aliquid-nesciunt for enterprise
-----------------------

Available as part of the Tidelift Subscription

The maintainers of @supernpm2024/enim-eos-aliquid-nesciunt and thousands of other packages are working with Tidelift to deliver commercial support and maintenance for the open source dependencies you use to build your applications. Save time, reduce risk, and improve code health, while paying the maintainers of the exact dependencies you use. [Learn more.](https://tidelift.com/subscription/pkg/npm-@supernpm2024/enim-eos-aliquid-nesciunt?utm_source=npm-@supernpm2024/enim-eos-aliquid-nesciunt&utm_medium=referral&utm_campaign=enterprise&utm_term=repo)
