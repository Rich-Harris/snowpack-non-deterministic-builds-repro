# non-deterministic snowpack builds

If you have multiple files with the same name (but different extensions), Snowpack behaves oddly.

Clone this repo, install dependencies, and run `snowpack build` to see:

```bash
git clone git@github.com:Rich-Harris/snowpack-non-deterministic-builds-repro
cd snowpack-non-deterministic-builds-repro
npm i

npx snowpack build
```

The resulting [build/src/foo.js](build/src/foo.js) file might contain the contents of `src/foo.js`, or it might contain bits of both `src/foo.js` and `src/foo.ts`:

```
console.log(`
	typescript
`);
ascript
	javascript
`);
```

Ideally, these clashes would surface as soon as `snowpack dev` or `snowpack build` is invoked. At any rate, the current behaviour isn't very helpful! 🙈