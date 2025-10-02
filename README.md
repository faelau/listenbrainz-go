# `listenbrainz-go`

[![Go Report Card](https://goreportcard.com/badge/github.com/faelau/listenbrainz-go)](https://goreportcard.com/report/github.com/faelau/listenbrainz-go)

`listenbrainz-go` is a package providing primitives to interact with the Listenbrainz API in Go. It is generated using [`oapi-codegen`](https://github.com/oapi-codegen/oapi-codegen)

## Install

```sh
$ go get github.com/faelau/listenbrainz-go/listenbrainz
```

## Usage

To use the generated API client, init it like the following:

```
package client_test

import (
	"context"
	"fmt"
	"log"
	"net/http"

	"github.com/faelau/listenbrainz-go/listenbrainz"
)

func main() {
  hc := http.Client{}
  c, err := listenbrainz.NewClientWithResponses("https://api.listenbrainz.org/", listenbrainz.WithHTTPClient(&hc))
		if err != nil {
			log.Fatal(err)
		}

		resp, err := c.GetClientWithResponse(context.TODO())
		if err != nil {
			log.Fatal(err)
		}
		if resp.StatusCode() != http.StatusOK {
			log.Fatalf("Expected HTTP 200 but received %d", resp.StatusCode())
		}

		fmt.Printf("resp.JSON200: %v\n", resp.JSON200)
}

```

Further description on how to use the generated library can be found under [github.com/oapi-codegen/oapi-codegen](https://github.com/oapi-codegen/oapi-codegen/blob/main/README.md#generating-api-clients).

## Contributors

The [following persons](https://github.com/faelau/listenbrainz-go/graphs/contributors) have contributed to the project 💜

<a href="https://github.com/faelau/listenbrainz-go/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=faelau/listenbrainz-go" />
</a>

## Stars

[![Star History Chart](https://api.star-history.com/svg?repos=faelau/listenbrainz-go&type=Date)](https://star-history.com/#faelau/listenbrainz-go&Date)
