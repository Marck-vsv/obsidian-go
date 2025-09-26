## 📖 Overview

Type conversion in Go is the process of creating a new value of one type from an existing value of another type.  
Go requires **explicit conversions** for safety; implicit casting is not allowed.

---

## 💡 Key Points

- Conversion syntax: `T(v)` where `T` is the target type and `v` is the value.  
- Numeric conversions must be explicit; watch out for overflow or precision loss.  
- Strings can be converted to `[]byte` or `[]rune`.  
- Use the `strconv` package for converting between strings and numbers.  
- Type assertions allow converting from `interface{}` to a concrete type.

---

## 📝 Example

```go
package main

import (
    "fmt"
    "strconv"
)

func main() {
    // Numeric conversion
    var i int = 42
    var f float64 = float64(i)
    fmt.Println("Int to Float64:", f)
	
    // Potential overflow
    var large int = 300
    var b byte = byte(large)
    fmt.Println("Int to Byte (overflow):", b)
	
    // String ↔ Number
    strNum := "123"
    num, _ := strconv.Atoi(strNum)
    fmt.Println("String to Int:", num)
    str := strconv.Itoa(456)
    fmt.Println("Int to String:", str)
	
    // Strings ↔ Bytes/Runes
    s := "Go!"
    fmt.Println("Bytes:", []byte(s))
    fmt.Println("Runes:", []rune(s))
	
    // Interface conversion (type assertion)
    var x interface{} = "hello"
    strVal, ok := x.(string)
    if ok {
        fmt.Println("Interface to String:", strVal)
    }
}

```

---

## 🔗 Related Topics

- [[Data Types]]
- [[Golang/Fundamentals/Type Assertion]]

---

## 📚 References

- [Official Go Docs](https://go.dev/doc/)
- [Go by Example](https://gobyexample.com/)
