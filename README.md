# queue

> A task queue for mitigating server pressure in high concurrency situations and improving task processing.

## Get

``` bash
go get -u -v github.com/hongbook/queue
```

## Usage

``` go
package main

import (
	"fmt"

	"github.com/hongbook/queue"
)

func main() {
	q := queue.NewQueue(10, 100)
	q.Run()

	defer q.Terminate()

	job := queue.NewJob("hello", func(v interface{}) {
		fmt.Printf("%s,world \n", v)
	})
	q.Push(job)

	// output: hello,world
}

```

## MIT License

    Copyright (c) 2020 hongbook
