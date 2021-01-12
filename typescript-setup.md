# Simple .ts file with linting and test

``` bash
npm init -y 
npm i -D typescript ts-node  # run .ts file by ts-node
npm i -D eslint @typescript-eslint/parser @typescript-eslint/eslint-plugin eslint-config-airbnb-typescript eslint-plugin-jsx-a11y eslint-plugin-react eslint-plugin-import eslint-plugin-react-hooks # linting package
./node_modules/.bin/tsc --init # create tsconfig.json file
touch .eslintrc.js
mkdir src
touch src/test.ts
#eslint will ignore file with same name(ignore main.js in favour of main.ts
npm i -D jest ts-jest @types/jest eslint-plugin-jest #jest for ts file and test linting
npx ts-jest config:init #add ts support for jest 
```

```javascript
//.eslintrc.js
module.exports = {
    root: true,
    parser: '@typescript-eslint/parser',
    plugins: [
      '@typescript-eslint',
    ],
    extends: [
      'airbnb-typescript',"plugin:jest/all"
    ],
    parserOptions: {
      project: './tsconfig.json',
    },
    ignorePatterns: ['.eslintrc.js']
  };
```

```typescript
//add.test.ts
import { add, subtract } from './add';

describe('testing add function', () => {
  it('add positive number', () => {
    expect.assertions(3);
    expect(add(1, 2)).toBe(3);
    expect(add(5, 4)).toBe(9);
    expect(add(9, 11)).toBe(20);
  });
  it('add negative number', () => {
    expect.assertions(3);
    expect(add(-1, -2)).toBe(-3);
    expect(add(-5, -4)).toBe(-9);
    expect(add(-9, -11)).toBe(-20);
  });
});

describe('testing subtract function', () => {
  it('subtract positive number', () => {
    expect.assertions(3);
    expect(subtract(1, 2)).toBe(-1);
    expect(subtract(5, 4)).toBe(1);
    expect(subtract(9, 11)).toBe(-2);
  });
});

```

```typescript
//add.ts
function add(a:number, b:number):number {
  return a + b;
}
function subtract(a:number, b:number):number {
  return a - b;
}
export { add, subtract };

```

