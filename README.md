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
  * `--scheme`: the scheme part, such as "http"
  * `--authority`: the authority part, such as "alice:secret@www.example.com:80"
  * `--userinfo`: the username and password, such as "alice:secret"
  * `--username`: the username, such as "alice"
  * `--password`: the password, such as "secret"
  * `--hostinfo`: the host and port, such as "www.example.com:80"
  * `--host`: the host, such as "www.example.com"
  * `--port`: the port, such as "80"
  * `--path`: the path part, such as "/a/b/c/index.html?key=val#123"
  * `--dirname`: the path directory name, such as "/a/b/c"
  * `--basename`: the path base name, such as "index.html"
  * `--query`: the query part, such as "key=val"
  * `--fragment`: the fragment part, such as "123"
  * `--hierarchy`: the authority and path
  * `--holarchy`: the query and fragment

## Scheme Details ##

## URI Scheme Details ##

Every URI is made of parts. The parts are described in the URI RFC specification, and there is a summary at http://en.wikipedia.org/wiki/URI_scheme

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

The path part may have a directory name and a base name:

    http://www.example.com/aa/bb/cc/index.html
                          └───┬───┘ └───┬────┘
                            dirname  basename
                          └─────────┬────────┘
                                   path


## Caution ##

This software is currently alpha quality.

It is suitable for a first look by developers so we can feedback and make improvements.

Do not use this current version for production systems.
