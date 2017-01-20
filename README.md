# cloudant-search

This is a [CouchDB 2.0](http://couchdb.apache.org/) with full text search capabilities that follows the steps from this [blog post](https://cloudant.com/blog/enable-full-text-search-in-apache-couchdb/#.Vly24SCrQbV) from [Cloudant](https://cloudant.com/).

View the [Dockerfile](https://github.com/homerjam/cloudant-search/blob/latest/Dockerfile).

## Prerequisites

You need to have a recent version of [Docker](https://www.docker.com/) installed

## Executing the Stack

Build the CouchDB image from the Dockerfile and run using the following:
```
$ docker build --tag="couchdb:search" ${PWD}

$ docker run -p 15984:15984 couchdb:search

or with persistent storage:

$ docker run -d -p 15984:15984 -v /tmp/couchdb:/usr/src/couchdb/dev/lib --name couchdb couchdb:search
```

There will be a Fauxton console available at http://localhost:15984/_utils

Full text searching is enabled and fully functional.  See the Cloudant [documentation](https://cloudant.com/for-developers/search/) for more info on how to test use the full text searching capabilities.

## Running tests

It uses [Serverspec](http://serverspec.org/) to test the Dockerfile:
```
$ bundle
$ bundle exec rspec
```
