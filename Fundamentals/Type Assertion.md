## 📖 Overview

Type assertions in Go are used to retrieve the **dynamic value** of an `interface{}` as a specific concrete type.  
They are a safe way to access the underlying value stored in an interface and are essential when working with **polymorphic types**.

---

## 💡 Key Points

- Syntax: `value, ok := x.(T)` where `x` is an interface and `T` is the target type.  
- The boolean `ok` indicates whether the assertion succeeded.  
- Using `x.(T)` without the `ok` form will panic if the type does not match.  
- Type assertions are commonly used with `interface{}` and in functions returning `interface{}` values.  
- Can also be used in **type switches** to handle multiple possible types dynamically.

---

## 📝 Example

```go
package main

import "fmt"

func main() {
    var x interface{} = "hello"
	
    // Safe type assertion
    str, ok := x.(string)
    if ok {
        fmt.Println("String value:", str)
    } else {
        fmt.Println("Not a string")
    }
	
    // Unsafe type assertion (will panic if wrong type)
    // num := x.(int) // Uncommenting this line would panic
	
    // Type switch example
    switch v := x.(type) {
    case string:
        fmt.Println("String:", v)
    case int:
        fmt.Println("Int:", v)
    default:
        fmt.Println("Unknown type")
    }
}
```

---

## 🔗 Related Topics

- [[Data Types]]
- [[Type Conversion]]

---

## 📚 References

- [Official Go Docs](https://go.dev/doc/)
- [Go by Example](https://gobyexample.com/)
