## 📖 Overview

In Go, variables are used to store values that can change during program execution, while constants hold values that remain fixed. Go emphasizes simplicity in variable declarations and provide multiple ways to declare and initialize them.

---

## 💡 Key Points

- Variables must be declared before use.
- The `var` keyword is used for explicit declaration.
- The `:=` operator provides shorthand declaration inside functions.
- Constants are declared with `const` cannot be changed.
- Variable names follow camelCase by convention.
- Go is statically typed, but type inference is supported.

---

## 📝 Example

```go
package main

import "fmt"

func main() {
    // Explicit declaration with type
    var age int = 25
    fmt.Println("Age:", age)

    // Declaration without initialization → default zero value
    var score int
    fmt.Println("Score:", score) // 0

    // Type inference
    var name = "Alice"
    fmt.Println("Name:", name)

    // Shorthand declaration (only inside functions)
    city := "New York"
    fmt.Println("City:", city)

    // Constant declaration
    const Pi = 3.14159
    fmt.Println("Pi:", Pi)

    // Multiple variable declaration
    var x, y = 10, 20
    fmt.Println("x + y =", x+y)
}
```

---

## 🔗 Related Topics

- [[Data Types]]
- [[Zero Values]]
- [[Variable Shadowing]]
- [[Iota]]
- [[Golang/Fundamentals/Program Structure]]

---

## 📚 References

- [Official Go Docs](https://go.dev/doc/)
- [Go by Example](https://gobyexample.com/)
