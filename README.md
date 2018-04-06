# Custom goxml2json

Go package that converts XML to JSON


### Changes

This version has removed prefixes in front of arguments and contents on decoding xmls.

It also parses ints(64bit), floats(64 bit) and booleans. If the ints or floats has a leading 0, it is considered a string.


### Install

    go get -u github.com/oisann/goxml2json

### Importing

    import github.com/oisann/goxml2json

### Usage

**Code example**

```go
  package main

  import (
  	"fmt"
  	"strings"

  	xj "github.com/oisann/goxml2json"
  )

  func main() {
  	// xml is an io.Reader
  	xml := strings.NewReader(`<?xml version="1.0" encoding="UTF-8"?><hello>world</hello>`)
  	json, err := xj.Convert(xml)
  	if err != nil {
  		panic("That's embarrassing...")
  	}

  	fmt.Println(json.String())
  	// {"hello": "world"}
  }

```

**Input**

```xml
  <?xml version="1.0" encoding="UTF-8"?>
  <osm version="0.6" generator="CGImap 0.0.2">
   <bounds minlat="54.0889580" minlon="12.2487570" maxlat="54.0913900" maxlon="12.2524800"/>
   <foo>bar</foo>
   <data type="04" value="4"/>
  </osm>
```

**Output**

```json
  {
    "osm": {
      "version": "0.6",
      "generator": "CGImap 0.0.2",
      "bounds": {
        "minlat": 54.0889580,
        "minlon": 12.2487570,
        "maxlat": 54.0913900,
        "maxlon": 12.2524800
      },
      "foo": "bar",
      "data": {
        "type": "04",
        "value": 4
      }
    }
  }
```

### Contributing
Feel free to contribute to this project if you want to fix/extend/improve it.

### Contributors

  - [DirectX](https://github.com/directx)
  - [samuelhug](https://github.com/samuelhug)

### TODO
   * ~~Remove prefixes~~
   * ~~Extract data types in JSON (numbers, boolean, ...)~~
   * Categorise errors
   * Option to prettify the JSON output
   * Benchmark
