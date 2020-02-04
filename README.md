# @cyca/simple-create-resource

Super basic create-resource for use with React Suspense with basic global cache.
Note that this doesn't respect [HTTP Caching](https://gist.github.com/ryanflorence/e10cc9dbc0e259759ec942ba82e5b57c#gistcomment-3114667).

This project was bootstrapped with [TSDX](https://github.com/jaredpalmer/tsdx).

```js

Usage:

// resources.js
import { createResource } from "@cyca/simple-create-resource";

const API = createResource(url => (
  fetch(url).then(res => res.json())
);

const FirebaseDoc = createResource(path => (
  firebase.firestore().doc(path).get()
))

export { API, FirebaseDoc }

```

```js
// somefile.js
import { API } from './resources';

API.preload('/thing');
const stuff = API.read('/thing');
API.clear('/thing');
API.clear(); // all keys
```
