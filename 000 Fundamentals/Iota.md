D## 📖 Overview

In Go, iota is a special built-in pre-declared identifier that simplifies the definition of incrementing constants. It is particularly useful when you need to define a series of related constants that follow a predictable pattern.

---

## 💡 Key Points

- Iota is a keyword that holds an integer value.
- Usually used within constant declarations to generate a series of related values.
- Avoid manually assigning values to each constant, making your code more concise.

---

## 📝 Example

```go
package main

import "fmt"

const (
	Sunday    = iota // 0
	Monday    = iota // 1
	Tuesday   = iota // 2
	Wednesday = iota // 3
	Thursday  = iota // 4
	Friday    = iota // 5
	Saturday  = iota // 6
)

// Note that you can reduce the number of times you need to assign the iota value to constants by simply assigning one of them

const (
	Sunday = iota // 0
	Monday        // 1
	Tuesday       // 2
	Wednesday     // 3
	Thursday      // 4
	Friday        // 5
	Saturday      // 6
)
```

---

## 🔗 Related Topics

- [[Variables and Constants]]

---

## 📚 References

- [Official Go Docs](https://go.dev/doc/)
- [Go by Example](https://gobyexample.com/)
