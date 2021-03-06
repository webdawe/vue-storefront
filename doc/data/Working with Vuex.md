# Working with Vuex

All data processing and remote requests should be managed by Vuex data stores. Core module contains more than [10 default data stores](https://github.com/DivanteLtd/vue-storefront/tree/master/core/store/modules) and can be easily extend by extension developers by adding [extension stores](https://github.com/DivanteLtd/vue-storefront/blob/master/doc/extensions/Working%20with%20extensions.md)

One can modify the existing store actions by responding to events. The events are specified in the docs below and can be easily found in the [core module](https://github.com/DivanteLtd/vue-storefront/tree/master/core) - where `EventBus.$emit` has been used mostly in Vuex Actions.

## Vuex modules
 * [Product](Product%20Store.md)
 * [Category](Category%20Store.md)
 * ...
 
 ## Related

* [Working with data](https://github.com/DivanteLtd/vue-storefront/blob/master/doc/Working%20with%20data.md)
