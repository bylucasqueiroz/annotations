- **Package Level Scope**

When you have multiple files that use the same package name, and you can share some information between then.

Ex:

``` Go, variable.go
package core

var color string = "Red"
```

``` Go, main.go
package core

func main() {
	fmt.Println(color)
}
```

