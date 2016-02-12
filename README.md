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
  * `--hierarchical`: the hierarchical part
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

## Scheme Details ##

See http://en.wikipedia.org/wiki/URI_scheme

Example of scheme parts:

  * uri: "http://alice:secret@www.example.com:80/a/b/c.html?d=e&f=g#hi"
  * scheme: "http"
  * hierarchical: "//alice:secret@www.example.com:80/a/b/c?d#e"
  * authority: "alice:secret@www.example.com:80"
    * userinfo: "alice:secret"
      * username: "alice"
      * password: "secret"
    * hostinfo: "www.example.com:80"
      * host: "www.example.com"
      * port: "80"
  * path: "/a/b/c"
    * dirname: "/a/b"
    * basename: "c"
  * query: "d"
  * fragment: "e"

## Caution ##

This software is currently alpha quality.

It is suitable for a first look by developers so we can feedback and make improvements.

Do not use this current version for production systems.
