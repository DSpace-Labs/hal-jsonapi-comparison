# HAL & JSON API Comparison
> Mocks of selected REST endpoints to compare HAL and JSON API

This repository contains a few endpoints mocked out in both HAL and JSON API to be able to compare them in order to choose a format for the DSpace 7 REST API


## JSON API
- Responses to a `GET` on the following endpoints: 
	- [`/collections`](json-api/json-api-collections.json)
	- [`/items`](json-api/json-api-items.json)
	- [`/bitstreams`](json-api/json-api-bitstreams.json)
	- [`/bundles`](json-api/json-api-bundles.json)
- Inclusion of Related Resources: A request to fetch everything needed to render an item view page would look similar to this:
	- `/items/21539b1d-9ef1-4eda-9c77-49565b5bfb78?include=collections&fields[name,handle],bundles,bundles.bitstreams`
	- This `GET`s the item with id `21539b1d-9ef1-4eda-9c77-49565b5bfb78` 
	- and asks to include its collections, but only their names and handles, for use in the trail for example:  `include=collections&fields[name,handle]…`
	- to include the item's bundles: `include=…,bundles…`
	- and to include the bitstreams of those bundles: `include=…,bundles.bitstreams`
	- [response](json-api/json-api-items-included.json)


