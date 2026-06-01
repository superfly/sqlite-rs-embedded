# SQLite no_std

> Note: these bindings are faithful to the base SQLite C-API as much as possible for minimum rust<->c overhead. This, however, means that the bindings are not entirely safe. E.g., the SQLite statement object will clear returned values out from under you if you step or finalize it while those references exist in your Rust program.

SQLite is lite. Its bindings should be lite too. They should be able to be used _anywhere_ SQLite is used, _not_ incur any performance impact, _not_ include any extra dependencies, and be usable against _any_ SQLite version.

This is a fork of [vlcn-io/sqlite-rs-embedded](https://github.com/vlcn-io/sqlite-rs-embedded) with additional features and fixes.

These bindings:

- Do not require the rust standard library
- Work on **stable Rust** (1.93+ required)
- Use the SQLite memory subsystem if no allocator exists
- Can be used to write SQLite extensions that compile to WASM and run in the browser
- Does 0 copying. E.g., through some tricks, Rust strings are passed directly to SQLite with no conversion to or copying to CString.
