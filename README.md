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
	- `/items/21539b1d-9ef1-4eda-9c77-49565b5bfb78?include=collections,bundles,bundles.bitstreams&fields[collections]=name,handle`
	- This `GET`s the item with id `21539b1d-9ef1-4eda-9c77-49565b5bfb78` 
	- and asks to include its collections :`include=collections…`
	- to include the item's bundles: `include=…,bundles…`
	- to include the bitstreams of those bundles: `include=…,bundles.bitstreams`
	- 	and for collections to only include the fields name and handle, for use in the trail for example:  `&fields[collections]=name,handle`
	- [response](json-api/json-api-items-included.json)
- Errors:
	- [This is a response](json-api/json-api-errors.json) that could be returned for an item submission that doesn't contain a title, but does contain a value for dc.contributor.assistant, a field that isn't defined on the server
- Pagination:
	- [This is a response](json-api/json-api-pagination.json) that could be returned for a paginated item list
	- `/items?page[number]=7&page[size]=2&fields[items]=name,handle`
		- `page[number]=7`: ask for page 7
		- `page[size]=2`: 2 results per page
		- `fields[items]=name,handle`: only return the name and the handle of each item

