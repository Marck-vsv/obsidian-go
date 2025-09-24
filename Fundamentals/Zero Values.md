## 📖 Overview

Zero values in go are default values for unitialized variables, always ensuring a predictable initial state and reducing initialization errors.

---

## 💡 Key Points

- It's not always necessary to assign a value when declaring a variable or constant.
- It's an equivalent to "no value" for each different type.

---

## 📝 Example

```go
package main

import "fmt"

func main() {
	var val1 int     // 0
	var val2 float64 // 0.0
	var val3 string  // ""
	var val4 bool    // false
	var val5 rune    // 0
	var val6 []int   // []
	var val7 *string // nil
}
```

---

## 🔗 Related Topics

- [[Variables and Constants]]
- [[Types]]

---

## 📚 References

- [Official Go Docs](https://go.dev/doc/)
- [Go by Example](https://gobyexample.com/)
