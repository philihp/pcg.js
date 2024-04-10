# pcg

[![Version](https://img.shields.io/npm/v/pcg.svg)](https://www.npmjs.com/package/pcg)
[![Tests](https://github.com/philihp/pcg/actions/workflows/tests.yml/badge.svg)](https://github.com/philihp/pcg/actions/workflows/tests.yml)
[![Coverage](https://coveralls.io/repos/github/philihp/pcg/badge.svg?branch=main)](https://coveralls.io/github/philihp/pcg?branch=main)
![Downloads](https://img.shields.io/npm/dt/pcg)
![License](https://img.shields.io/npm/l/pcg)

A functional implementation of the [PCG family random number generators](), written in JavaScript.

[PCG family random number generators]: http://pcg-random.org

## Getting started

To achieve frictionless reproducibility of random output results, immutable objects are used throughout the project.

First, seed a PCG state. A stream ID specifies _which_ unique periodic series of entropy to use. The state specifies _where_ in that series we start.

```
import { createPcg32 } from 'pcg'

const advancedOptions = {}
const initState = 42
const initStreamId = 54
const state0 = createPcg32(advancedOptions, initState, initStreamId)
```

After that, random outputs can be generated by calling appropriate functions as shown below:

```js
import { nextState, prevState, randomInt, randomList } from 'pcg'

const randomUint32 = randomInt(0, 2 ** 32 - 1)
const [value, nextState] = randomUint32(state0)

const listLength = 3
const listItemRng = randomUint32
const [[v1, state1], [v2, state2], [v3, state3]] = randomList(listLength, listItemRng, state0)
```

In this above example, `value === v1`, and `nextState === state1`

## Thanks

- [@kripod](https://github.com/kripod/), who wrote the original [`pcg.js`](https://github.com/kripod/pcg.js)
