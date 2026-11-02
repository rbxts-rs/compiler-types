# @rbxts/compiler-types

## 3.0.0-types.1-ts7.0

3.0.0-types.0 with the iterable interfaces TypeScript 7 needs, so one package serves stock roblox-ts 3.0.0
(TypeScript 5.5) and compilers on TypeScript 7 (rbxts-rs).

- `Iterable`, `IterableIterator`, `AsyncIterable` and `AsyncIterableIterator` take `<T, TReturn = any, TNext = any>`
  and pass all three on to `Iterator` / `AsyncIterator`. TypeScript 7 looks these global types up with three type
  parameters; with one, it rejects `for...of` and spread over anything but an array (TS2802). The defaults keep every
  existing one-argument use (`Iterable<T>`) valid.
- TypeScript 5.5 expects one type parameter. roblox-ts 3.0.0 builds are unaffected (same output), but a plain `tsc`
  or editor on TypeScript 5.5 reports TS2317 ("Global type 'Iterable' must have 1 type parameter(s)") in
  `Iterable.d.ts` unless `skipLibCheck` is set. 3.0.0-types.0 has the opposite case: TypeScript 5.6 to 5.9 report
  TS2317 for its one-parameter forms.
