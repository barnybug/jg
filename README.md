jg
==

Simple command line tool for generating json documents.

Introduction
------------
jg takes any number of command line arguments of the form key:value or key=value, and generates corresponding json.

eg:

    $ jg 'a.b:[1,2]'

generates:

    {
      "a": {
        "b": [
          1, 
          2
        ]
      }
    }

The *key* is a . separated path describing the nested json objects to create.

The *value* can be any valid yaml value.

As a shortcut, you can follow relative to the last path by starting with a
period, eg:

    $ jg obj.field1:1 .field2:2

generates:

    {
      "obj": {
        "field1": 1,
        "field2": 2 
      }
    }

Curling
-------
To pass the json as a POST body to curl (elasticsearch) do:

    $ jg query.match_all:{} facets.myfacet.terms.field:field1 | curl localhost:9200/_search -d @-

Installation
-------------
Just copy jg into your path, eg:

    $ sudo cp jg /usr/local/bin
