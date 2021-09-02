# SendPulse REST client library (unofficial)
An unofficial SendPulse REST client library for Go (Golang).

API Documentation [https://sendpulse.com/api](https://sendpulse.com/api)

### Installation

```shell
go get -u github.com/zhashkevych/sendpulse-sdk-go
```

### Usage
```go
package main

import (
	"fmt"
	"github.com/zhashkevych/sendpulse-sdk-go/sendpulse"
	"net/http"
)

func main() {
	config := &sendpulse.Config{
		UserID: "",
		Secret: "",
	}
	client := sendpulse.NewClient(http.DefaultClient, config)
	
	emails := make([]*sendpulse.EmailToAdd, 0)
	emails = append(emails, &sendpulse.EmailToAdd{
		Email:     "test@test.com",
		Variables: map[string]interface{}{"age": 21, "weight": 99},
	})

	if err := client.Emails.MailingLists.SingleOptIn(1266208, emails); err != nil {
		fmt.Println(err)
	}
	fmt.Println(*emails[0])
}
```

The tests should be considered a part of the documentation.
