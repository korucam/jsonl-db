# jsonl-db

Simple JSONL-based key-value store. Uses an append-only file to store the data. With support for database dumps and compressing the db file.

## Usage

Load the module:

```ts
import { DB } from "jsonl-db";
```

Open or create a database file:

```ts
const db = new DB("/path/to/file");
await db.open();
```

Use the database like you would use a [`Map`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map).

The data is persisted asynchronously, so make sure to `close()` the DB when you no longer need it:

```ts
await db.close();
```

To create a compressed copy of the database in `/path/to/file.dump`, use the `dump()` method. If any data is written to the db during the dump, it is appended to the dump but most likely compressed.

```ts
await db.dump();
```

After a while, the main db file may contain unnecessary entries. To remove them, use the `compress()` method.

```ts
await db.compress();
```

**Note:** During this call, `/path/to/file.dump` is overwritten and then renamed, `/path/to/file.bak` is overwritten and then deleted. So make sure you don't have any important data in these files.

## Changelog

<!--
	Placeholder for next release:
	### __WORK IN PROGRESS__
-->

### **WORK IN PROGRESS**

First official release
