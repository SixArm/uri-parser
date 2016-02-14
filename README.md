# uri-parser:<br>parse a URI to its parts

Syntax:

    uri-parser [options] <uri> ...

Examples:

    $ uri-parser --host http://example.com/index.html
    example.com

    $ uri-parser --path http://example.com/index.html
    /index.html

## Options ##

General options:

  * `-h`, `--help`: show help message
  * `-V`, `--version`: show version message

Output options:

  * `--uri`: the entire URI
  * `--scheme`, `--protocol`: the scheme a.k.a. protocol, such as "http"
  * `--authority`: the authority, such as "alice:secret@www.example.com:80"
  * `--userinfo`: the username and password, such as "alice:secret"
  * `--username`: the username, such as "alice"
  * `--password`: the password, such as "secret"
  * `--hostinfo`: the host and port, such as "www.example.com:80"
  * `--host`: the host, such as "www.example.com"
  * `--port`: the port, such as "80"
  * `--path`: the path, such as "/a/b/c/index.html?key=val#123"
  * `--dirname`: the path directory name, such as "/a/b/c"
  * `--basename`: the path base name, such as "index.html"
  * `--query`: the query, such as "key=val"
  * `--fragment`, `--anchor`: the fragment a.k.a. anchor, such as an id
  * `--hierarchy`: the hierarchical part, which is the authority and path
  * `--holarchy`: the non-hierarchical part, which is the query and fragment
  * `--tld`: the TLD a.ka. top level domain, such as "com"
  * `--connection`: the connection URI, such as "http://alice:secret@www.example.com:80"
  * `--favicon`: the probable favicon URL, such as "http://www.example.com/favicon.ico"
  * `--defragment`: the entire URI except the fragment

## URI Scheme Details ##

Every URI is made of parts.

  * The parts are described in the URI RFC specification.
  * There is a summary at http://en.wikipedia.org/wiki/URI_scheme
  * This script adds some custom part names, such as "dirname" and "basename".

Example:

    http://www.example.com/index.html
    └─┬─┘  └──────┬──────┘ └───┬────┘
    scheme       host         path

Example with more parts:

    http://elizabeth:opensesame@www.example.com:10000/aa/bb/cc/index.html?key=val#identifier
    └─┬─┘  └───┬───┘ └───┬────┘ └──────┬──────┘└─┬──┘└─────────┬────────┘ └──┬──┘ └───┬────┘
    scheme  username  password        host      port          path          query   fragment
           └─────────┬────────┘ └─────────┬─────────┘└──────────────────┬──────────────────┘
                  userinfo             hostinfo                      pathinfo
           └───────────────────┬────────────────────┘
                           authority
           └───────────────────────────────┬────────────────────────────┘ └───────┬────────┘
                                        hierarchy                              holarchy

The host part may have a top level domain part:

                 host
           ┌──────┴──────┐
    http://www.example.com
                       └┬┘
                       tld

The path part may have a directory name and a base name:

                                  path
                          ┌────────┴─────────┐
    http://www.example.com/aa/bb/cc/index.html
                          └───┬───┘ └───┬────┘
                            dirname  basename

The `--defragment` option transforms the URI by deleting any fragment part and hash character:

    http://www.example.com/example.html#identifier
                                       └────┬────┘
                                        defragment deletes this

The `--connection` option gets the scheme and authority, and is typically suitable for making a network connection:

    http://www.example.com/aa/bb/cc/index.html
    └─────────┬──────────┘
          connection

The `--favicon` option transforms the URI by using the connection part then appending the typical file name `favicon.ico`:

    http://www.example.com/favicon.ico
    └────────────────┬───────────────┘
                   favicon

Synonyms:

  * scheme, protocol
  * fragment, fragment id, anchor, anchor name
