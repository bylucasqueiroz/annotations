### Theory 

![Initial](https://www.youtube.com/watch?v=PAAkCSZUG1c&t=3m42s)

When people hear the word _concurrency_ they often think of _parallelism_, a related but quite distinct concept.

Concurrency tasks can be executed in different intervals at time, and not necessarily in multiple cores of CPU, if you have only one core your Task can be processed asynchronously. Parallelism tasks are executed simultaneously, on separate cores at the exact same time and we have isolated executions.

Then we can create an analogy with two restaurants where one of them only have one cook, but we have two queue of people. Each person make a request, the chef will try to prepare the plate interleaved in an overlapping manner. In the other hand, if you have more than one chef, you can responsabilize each for one queue, and divide by two these requests.

In conclusion, as Andrew Gerrand wrote on [The Go Blog](https://go.dev/blog/waza-talk), "_Concurrency is about dealing with lots of things at once. Parallelism is about doing lots of things at once._"

 ![Rob Pike at Heroku's Waza Conference](https://youtu.be/oV9rvDllKEg)

### Code

``` Go
package main

import (
    "fmt"
    "runtime"
    "time"
)

func f(from string) {
    for i := 0; i < 3; i++ {
        fmt.Println(from, ":", i)
    }
}

func main() {
    runtime.GOMAXPROCS(1)
    
    f("direct")

    go f("goroutine")

    go func(msg string) {
	  fmt.Println(msg)
    }("going")

    time.Sleep(time.Second)
    fmt.Println("done")
}
```

