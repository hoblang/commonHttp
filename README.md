# commonHttp – useful types for http

This library provides HTTP request and HTTP response models, request parser and utils for manipulating them.

## Usage

Request parsing

```hob
var parser = http.parser.new();
defer parser.free();

# put data in parser
parser.put("GET /hello/world").unwrap();
parser.put(" HTTP/1.1\n").unwrap();
parser.put("Content-Type: application/json\n").unwrap();
parser.put("\n").unwrap();

if !parser.finished() {
    # not enough data for fully parse request
}

final request = parser.request();
defer request.free();

# use request fields such as method, path, query and other...
```
