uri-parser:
parse a URI to its scheme parts.

Syntax:

   uri-parse [selector ...] <uri> ...

Example:

  $ uri-parser "http://www.example.com:80"
  scheme: http
  authority: www.example.com:80
  host: www.example.com
  port: 80

Example with a selector:

  $ uri-parser --host "http://www.example.com"
  www.example.com

## Options ##

General options:

  * `-h`, `--help`, `-?`: show help message
  * `-V`, `--version`: show version message

Parse options:

  * `--uri`
  * `--scheme`
  * `--hierarchical`
  * `--authority`
  * `--userinfo`
  * `--username`
  * `--password`
  * `--hostinfo`
  * `--host`
  * `--port`
  * `--path`
  * `--dirname`
  * `--basename`
  * `--query`
  * `--fragment`

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

Caution: this current implementation is sufficient for our internal needs;
it is generally accurate for typical URIs, but is not standards-compliant.

Command: uri-parser
Version: 3.0.0
Created: 2015-05-31
Updated: 2016-02-12
License: GPL
Contact: Joel Parker Henderson (joel@joelparkerhenderson.com)
