# Open EC (Embodied Carbon) API

Open Embodied Carbon API is an open API that provides a simple interface to
access embodied carbon data from [ICE database V3.0.](https://circularecology.com/embodied-carbon-footprint-database.html)

## Why API?

API simply brings an agile way of working with EC data. You don’t need anything
but an environment where you can make a simple API call, which is possible on
popular AEC software like Grasshopper or Dynamo without additional plugins.

You can create a lightweight custom workflow to easily assess the EC of your
project without worrying about dependencies. Hosting the data on a public API
offers many advantages, especially if you are creating a tool to share with
others, or even if you just want to assess it quickly without signing up or
installing anything.

Putting the API in the public domain makes the data more reliable and ensures
everyone uses the same set. With traditional software or plugins, there is no
way to verify this as everything is hidden in a "black box".

## About this repository

This repository contains a list of API calls you can make to the API, and also
some example files that you can download and use on your favorite software like
Grasshopper or Dynamo without any additional plugins.

It also includes the csv version of the ICE database used in this API for
verification of the data. Some modifications have been made due to some errors
in the original data set. Please read the [disclaimer](#Disclaimers) below for
detail.

## Current status of the project

The project is currently at the proof-of-concept stage. The API might be taken
offline or the interface may change in the future without any notice.

## Usage policy

You may use the API for a hobby, academic, commercial, or non-commercial
purposes free of charge. The API is hosted on the free server at the moment and
may have to introduce some fees to use the API in the future depending on the
traffic. To protect the API, a certain threshold for the rate limit is applied
to the API. Currently, it is not per your IP address but per the whole service.

## API Endpoints

In the follwoing example, ":id" or ":name" is a notation for the path variable.
To maek a query, you need to chagne the whole woord with the query.

### getAllEc

`https://dla-hubs-ec-api.deno.dev/ice3.0a`

It returns the whole EC data. By default, it returns the first 25 rows of data,
and you can use the query parameter to get the next 25, which looks like:

`https://dla-hubs-ec-api.deno.dev/ice3.0a?cursor=25`

You can change the number to get the next set of data.

### getAllNames

`https://dla-hubs-ec-api.deno.dev/ice3.0a/all_names`

It returns only the id and ICE db name of the material for your reference.
'?cursor=25' to be used for pagination.

### getComentById

`https://dla-hubs-ec-api.deno.dev/ice3.0a/comment/:id`

It returns only the comment field based on a given id.

### getIdByName

`https://dla-hubs-ec-api.deno.dev/ice3.0a/comment/:name`

It returns only the comment field based on a given name.

### getEcByCategory

`https://dla-hubs-ec-api.deno.dev/ice3.0a/ec_by_category/:category`

It returns the whole EC dataset belongs to the same cateogry type of the
material. Only the follwoing keywords can be used:

- AGGREGATE_SAND
- ALUNINIUM
- BITUMEN
- CEMENT
- CLAY
- CONCRETE
- GLASS
- STEEL
- TIMBER

### getEcById

`https://dla-hubs-ec-api.deno.dev/ice3.0a/ec_by_id/:id`

It returns the whole data basesed on a given name.

### getEcByName

`https://dla-hubs-ec-api.deno.dev/ice3.0a/ec_by_name/:name`

It returns the whole data basesed on a given name.

## Disclaimers

Some data have been modified for this API due to the errors discovered while
auditing the dataset. Please raise the issue, if you find anything unreasonable
with the following modifications. The original dataset used for the API can be
found in this depository for data verification purposes.

- Embodied carbon per kg for aluminium was recalculated based on the assumption
  that all the "Weight per declared unit-kg" is 1kg. It just didn't make sense
  without this adjustment.

- Embodied carbon per kg for asphalt was recalculated based on the kg weight per
  declared unit since, the number seemed to be a result of incorrect conversion
  of the unit.
