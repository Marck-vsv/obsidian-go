## 📖 Overview

Variable shadowing occurs when a variable declared within a certain scope (like a block or function) has the same name as a variable outer scope. The inner variable effectively "shadows" the outer variable, meaning that the inner one is accessible in that scope hile the outer one is "hidden" or inaccessible  

---

## 💡 Key Points

- Shadowing is about variable visibility, the inner variable will take precedence within its scope.
- Any reference to an variable within its scope will refer to the inner variable.
- Even tho you modified a variable in the inner scope, the outer one remais unchanged.
- Once you exit the inner scope the outer variable becomes accessible again.

---

## 📝 Example

```go
package main

import "fmt"

func main() {
	x := 10             // Outer variable
	fmt.printLn(x)      // 10
	
	if true {
		x := 5          // Inner variable
		fmt.printLn(x)  // 5
	}
	
	fmt.printLn(x)      // 10 (remains unchanged)
}
```

---

## 🔗 Related Topics

- [[Variables and Constants]]

---

## 📚 References

- [Official Go Docs](https://go.dev/doc/)
- [Go by Example](https://gobyexample.com/)
