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
  RepoOwner string = "Yitsushi"
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

It does not return with the full Release response object
but only with useful fields that related to an application update request.
