# dtypecheck - dynamic typecheck helper

#### Note: It works with `env NODE_ENV=development`

Examples:

### Simple

```javascript
const t = require("dtypecheck");
const {expect} = require("chai");

const fn = t(
  number => `${number}`,
  number => expect(number).a(`number`),
  string => expect(string).a(`string`)
);

fn(1) // Good
fn([1, 2]) // Bad
```
### Async

```javascript
const t = require("dtypecheck");
const {expect} = require("chai");

const fn = t(
  async (number) => `${number}`,
  async (number) => expect(number).a(`number`),
  async (string) => expect(string).a(`string`)
);

(async () {
  await fn(1) // Good
  await fn([1, 2]) // Bad
})();
```
