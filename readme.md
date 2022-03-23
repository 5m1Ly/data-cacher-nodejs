### Caching
There are 2 ways of caching data with this class either globally or locally. you can cache data gobally by using the Cache constant you can import from the cache.js file if you want to cache data locally you can use the DataCacher class also imported from the cache.js file.

#### Local Caching
When you want to cache data locally you should import the DataCacher class from the cache.js file and create a new instance of the class like shown below this caches within the module (file/script) and can't be shared across files unless exported
```js
import { DataCacher } from './utils/cache';
const Cache = new DataCacher();
```

#### Global Caching
The default export Cache is a instance of the DataCacher class that has been instanciated within the cache.js file this way the cached data can be shared across diffrent modules (files/scripts).
```js
import Cache from './utils/cache';
```

#### Properties
| prop  | value   | use case                       |
|-------|---------|--------------------------------|
| temp  | Array   | temp data storage              |
| data  | Object  | cached data storage            |
| state | Boolean | true when processing temp data |

#### Methods
1. add

	<small>_With this method you can add data to the caching queue_</small>

	<strong>Info</strong>
	| call        | async | return value |
	|-------------|-------|--------------|
	| Cache.add() | no    | none         |

	<strong>Parameters</strong>
	| param    | value  | optional |
	|----------|--------|----------|
	| catagory | String | no       |
	| index    | String | no       |
	| data     | Object | no       |

	<strong>Example</strong>
	```js
	Cache.add("users", userdata.index, userdata)
	```

1. get

	<small>_With this method you can fetch cached data_</small>

	<strong>Info</strong>
	| call        | async | return value |
	|-------------|-------|--------------|
	| Cache.get() | yes   | data         |

	<strong>Parameters</strong>
	| param    | value    | optional |
	|----------|----------|----------|
	| catagory | String   | no       |
	| index    | String   | no       |
	| callback | Function | yes       |

	<strong>Example</strong>
	```js
	// without callback

	// option 1
	const userdata = Cache.get("users", "sdoa812bdo8d0a8h081");

	// option 2
	const userdata = await Cache.get("users", "sdoa812bdo8d0a8h081");

	// with callback
	Cache.get("users", "sdoa812bdo8d0a8h081", (userdata) => {
		console.log(userdata)
	})
	```