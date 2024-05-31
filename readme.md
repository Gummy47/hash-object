# hash-object

> Get the hash of an object

[Original version](https://github.com/sindresorhus/hash-object) used node-specific `node:crypto` import syntax which made it incompatible with webpack.
Slightly modified it to fit my needs, that's all.

## Install

```sh
npm install @gummy47/hash-object
```

## Usage

```js
import hashObject from 'hash-object';

hashObject({'🦄': '🌈'}, {algorithm: 'sha1'});
//=> '3de3bc784035b559784fc276f47493d60555fba3'
```

## API

### hashObject(object, options?)

The output is deterministic for repeated runs on the same Node.js / browser version. It should also be fairly deterministic across JavaScript engines. However, because the stability of grapheme clusters across Unicode versions is not guaranteed, determinism cannot be guaranteed across JavaScript engines and versions. There are also other factors that can make it nondeterministic, like values with floating point numbers and dates.

#### object

Type: `object`

#### options

Type: `object`

##### encoding

Type: `'hex' | 'base64' | 'buffer' | 'latin1'`\
Default: `'hex'`

The encoding of the returned hash.

##### algorithm

Type: `string`\
Default: `'sha512'`\
Values: `'md5' | 'sha1' | 'sha256' | 'sha512' | …` *([Platform dependent](https://nodejs.org/api/crypto.html#crypto_crypto_createhash_algorithm))*

*Don't use `'md5'` or `'sha1'` for anything sensitive. [They're insecure.](http://googleonlinesecurity.blogspot.no/2014/09/gradually-sunsetting-sha-1.html)*
