# Github Release Check

This is a simple Go lib to handle updates. Small and easy to use lib.

``` sh
go get github.com/yitsushi/github-release-check
```

### Sample code

``` go
package main

import GRC "github.com/yitsushi/github-release-check"
import "fmt"

const (
  RepoOwner string = "yitsushi"
  RepoName  string = "Server-For-React"
  Version   string = "v1.0"
)

func main() {
  needUpdate, releaseInfo, err := GRC.Check(RepoOwner, RepoName, Version)

  if err != nil {
    panic(err)
  }

  if needUpdate {
    fmt.Printf("Please update from %s to %s at %s", Version, releaseInfo.TagName, releaseInfo.HTMLURL)
  } else {
    fmt.Println("Application status: Up to date.")
  }
}
```

It does not return with the full [Release response object](https://developer.github.com/v3/repos/releases/)
but only with useful fields that related to an application update request.

### Why release?

Because I need to test the API Endpoint somewhere and why not with the same repo. So nothing more (yet)
