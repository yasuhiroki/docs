# TypeScript

## tsconfig.json

### Node.js ES6 and TypeScript &gt; 2.2

```
{
  "compilerOptions": {
    "module": "ES6",
    "moduleResolution": "Node",
    "noImplicitAny": true,
    "noImplicitReturns": true,
    "noFallthroughCasesInSwitch": true,
    "strictNullChecks": true,
    "removeComments": true,
    "preserveConstEnums": true,
    "sourceMap": true
  },
  "include": [
    "lib/**/*.ts",
    "test/**/*.ts"
  ],
  "exclude": [
    "node_modules"
  ]
}
```



