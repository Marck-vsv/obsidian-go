## 📖 Introduction

Data types in go specify the kinds of values that particular variables will store when you are writing a program. The data type also determines what operations can be perform on the data.

---

## 🔍 Concepts and Details
### 1. Integers

Integers are fundamental numeric types that can be signed (`int`) or unsigned (`uint`). The distinction is crucial because it determines whether negative values are allowed and how much memory the type consumes. Go provides both **architecture-dependent** integer types (`int`, `uint`) and **explicitly sized** integer types (`int8`, `int16`, `int32`, `int64`, and their unsigned counterparts).

#### 1.1 Signed vs Unsigned

- **Signed (`int`)**: can represent both negative and positive numbers
- **Unsigned (`uint`)**: can only represent non-negative numbers (0 and above)

```go
package main

import "fmt"

func main() {
    var a int = -42
    var b uint = 42

    fmt.Println("Signed int:", a)
    fmt.Println("Unsigned uint:", b)
}
```

Signed integers are generally the default choice because most applications require handling both positive and negative values.

#### 1.2 Size of `int` and `uint`

The size of `int` and `uint` depends on the target architecture:

- On a **32-bit system**: `int` and `uint` are 32 bits (4 bytes)
- On a **64-bit system**: `int` and `uint` are 64 bits (8 bytes)

This makes them _machine-dependent types_, unlike explicitly sized integers.

#### 1.3 Explicitly Sized Integers

Go defines fixed-size integer types for greater control:

| Type   | Size (bits) | Range (approx.)                    |
| ------ | ----------- | ---------------------------------- |
| int8   | 8           | -128 to 127                        |
| uint8  | 8           | 0 to 255                           |
| int16  | 16          | -32,768 to 32,767                  |
| uint16 | 16          | 0 to 65,535                        |
| int32  | 32          | -2,147,483,648 to 2,147,483,647    |
| uint32 | 32          | 0 to 4,294,967,295                 |
| int64  | 64          | -9,223,372,036,854,775,808 to 9e18 |
| uint64 | 64          | 0 to 18,446,744,073,709,551,615    |

```go
package main

import "fmt"

func main() {
    // Explicitly sized
    var small int8 = 120
    var big int64 = 1_000_000_000
    fmt.Println("int8:", small)
    fmt.Println("int64:", big)
}
```

#### 1.4 Type Conversions

Go does not allow implicit conversions between `int` and `uint` (or between different sizes). You must convert explicitly:

```go
var a int = 10
var b uint = uint(a) // explicit conversion
```

___

### 2. Floating Points

Floating-point numbers in Go represent real numbers (with fractions/decimals). They are used when integer types are not sufficient for precise or fractional values. Go provides two sizes of floating-point numbers: `float32` and `float64`.
By default, when you write a floating-point literal (e.g., `3.14`), Go treats it as a `float64`.

#### 2.1 Types of Floating Points

- **`float32`**: 32-bit floating point, about 6-7 decimal digits of precision
- **`float64`**: 64-bit floating point, about 15-16 decimal digits of precision (default and recommended in most cases)

```go
package main

import "fmt"

func main() {
	var f32 float32 = 3.141592653589793
	var f64 float64 = 3.141592653589793
	
	fmt.Println("float32:", f32) // loses some precision
	fmt.Println("float64:", f64) // more precise
}
```

#### 2.2. Precision and Rounding Errors

Floating-point numbers are **approximations** of real numbers. Operations may result in rounding errors:

```go
package main

import "fmt"

func main() {
    var a float64 = 0.1
    var b float64 = 0.2
    var c float64 = 0.3
	
    fmt.Println(a + b == c) // false due to floating-point precision
}
```

**Tip**: never rely on floats for exact comparisons (e.g., money). Use integers or `math/big` instead.

#### 2.3 Special Values

Floating-point numbers follow the **IEEE 754 standard**, so they can represent special values:
* `+Inf` and `-Inf`: positive and negative infinity
* `NaN`: "Not a Number", e.g., result of invalid operations like `0.0/0.0`

```go
package main

import (
    "fmt"
    "math"
)

func main() {
    fmt.Println("Positive Inf:", 1.0/0.0)
    fmt.Println("Negative Inf:", -1.0/0.0)
    fmt.Println("NaN:", math.Sqrt(-1))
}
```

#### 2.4 Complex Numbers

Although not strictly "floating point", Go also provides **complex numbers** (`complex64`, `complex128`) which are built from floating points:

```go
package main

import "fmt"

func main() {
    c1 := complex(1, 2)   // complex128 by default
    c2 := complex(3, 4)
    fmt.Println("c1:", c1)
    fmt.Println("c2:", c2)
    fmt.Println("Sum:", c1+c2)
}
```

---

### 3. Complex

Go has built-in support for **complex numbers**, which are numbers that have both real and an imaginary part. These are particularly useful in fields like signal processing, scientific computing, and electrical engineering.

Go provides two complex types:
- **`complex64`**: real and imaginary parts are `float32`
- **`complex128`**: real and imaginary parts are `float64` (default when using literals)

#### 3.1 Declaring Complex Numbers

You can create a complex number using the built-in `complex` function or by directly writing with `i` as the imaginary unit.

```go
package main

import "fmt"

func main() {
	// Using complex (real, imag)
	c1 := complex(3, 4) // 3 + 4i
	fmt.Println("c1:", c1)
	
	// Direct declaration
	c2 := 5 + 6i
	fmt.Println("c2:", c2)
}
```

#### 3.2 Operations with Complex Numbers

Complex numbers support the usual arithmetic operators: `+`, `=`, `*`, `/`.

```go
package main

import "fmt"

func main() {
    c1 := 2 + 3i
    c2 := 1 + 4i
	
    fmt.Println("Sum:", c1+c2)
    fmt.Println("Difference:", c1-c2)
    fmt.Println("Product:", c1*c2)
    fmt.Println("Quotient:", c1/c2)
}
```

#### 3.3 Extracting Real and Imaginary Parts

Go provides the built-in functions `real()` and `imag()` to extract components of a complex number:

```go
package main

import "fmt"

func main() {
    c := 7 + 2i
    fmt.Println("Real part:", real(c))
    fmt.Println("Imag part:", imag(c))
}
```

#### 3.4 Magnitude and Phase (with `math/cmplx`)

The `math/cmplx` package provides advanced operations for complex numbers:
* `cmplx.Abs(z)` $\rightarrow$  magnitude (distance from origin)
* `cmplx.Phase(z)` $\rightarrow$  phase (angle in radians)
* `cmplx.Conj(z)` $\rightarrow$  complex conjugate

```go
package main

import (
    "fmt"
    "math/cmplx"
)

func main() {
    c := 3 + 4i
    fmt.Println("Magnitude:", cmplx.Abs(c))   // 5
    fmt.Println("Phase:", cmplx.Phase(c))     // angle in radians
    fmt.Println("Conjugate:", cmplx.Conj(c))  // 3 - 4i
}
```

### 4. Boolean

The `bool` type in Go represent truth values: `true` or `false`. They are used in conditional logic, comparisons, and control strutctures.

#### 4.1 Declaring Booleans

A boolean can be declared directly with `true` or `false`, or it can be the result of a comparison expression.

```go
package main

import "fmt"

func main() {
    var b1 bool = true
    var b2 = false
    b3 := (10 > 5)
	
    fmt.Println("b1:", b1)
    fmt.Println("b2:", b2)
    fmt.Println("b3:", b3) // result of comparison
}
```

#### 4.2 Comparison Operators

Comparison operators always return a boolean value:
* `==` (equal)
* `!=` (not equal)
* `<`, `<=`, `>`, `>=`

```go
package main

import "fmt"

func main() {
    fmt.Println(5 == 5)   // true
    fmt.Println(5 != 3)   // true
    fmt.Println(7 < 2)    // false
    fmt.Println(10 >= 10) // true
}
```

#### 4.3 Logical Operators

Go provides three main logical operators for booleans:
* `&&` $\rightarrow$  logical AND
* `||` $\rightarrow$  logical OR
* `!` $\rightarrow$  logical NOT

```go
package main

import "fmt"

func main() {
    a := true
    b := false
	
    fmt.Println("a && b:", a && b) // false
    fmt.Println("a || b:", a || b) // true
    fmt.Println("!a:", !a)         // false
}
```

#### 4.4 Usage in Control Structures

Booleans are essential in control flow statements like `if`, `for`, and `switch`.

```go
package main

import "fmt"

func main() {
    isLoggedIn := true
	
    if isLoggedIn {
        fmt.Println("Welcome back!")
    } else {
        fmt.Println("Please log in.")
    }
}
```

---

### 5. Runes

In Go, a **rune** represents a single Unicode code point It is essentially an alias for the type `int32`. Runes are useful when you need to work with individual characters in strings, especially when dealing with non-ASCII text. Unlike some languages where a "char" is just a byte, Go’s `rune` type ensures proper handling of Unicode characters, which may take more than one byte.  

#### 5.1 Declaring Runes

You can declare runes using single quotes (`''`), which represent Unicode characters 

```go
package main

import "fmt"

func main() {
    var r rune = 'A'
    fmt.Printf("Rune: %c | Code point: %U\n", r, r)
	
    smile := '😊'
    fmt.Printf("Rune: %c | Code point: %U\n", smile, smile)
}
```

#### 5.2 Difference between `byte` and `rune`

* `byte`(`uint8`) $\rightarrow$ represents a raw ASCII character (1 byte)
* `rune`(`int32`) $\rightarrow$ represents a Unicode code point (may take up to 4 bytes in UTF-8).

```go
package main

import "fmt"

func main() {
    b := byte('A')   // ASCII
    r := rune('😊')  // Unicode
	
    fmt.Println("byte:", b) // 65
    fmt.Println("rune:", r) // 128522
}
```

#### 5.3 Iterating over strings

When you iterate over a string with `for ... range`, Go decodes runes automatically (not raw bytes)

```go
package main

import "fmt"

func main() {
    s := "Olá, Go!"
	
    for i, r := range s {
        fmt.Printf("Index: %d | Rune: %c | Code point: %U\n", i, r, r)
    }
}
```

#### 5.4 Working with the `unicode` Package

The `unicode` package provides helpers to classify and manipulate runes.

```go
package main

import (
    "fmt"
    "unicode"
)

func main() {
    r := 'A'
    fmt.Println("IsLetter:", unicode.IsLetter(r)) // true
    fmt.Println("IsDigit:", unicode.IsDigit(r))   // false
}
```

### 6. Strings

Strings in Go are immutable sequences of `bytes`, typically representing text encoded in UTF-8.  
They are a fundamental type used to store and manipulate textual data. 

#### 6.1 Declaring strings

Strings can be created using either **interpreted string literals** or **raw string literals**.

```go
package main

import "fmt"

func main() {
    s1 := "Hello, Go!"
    s2 := `Raw string example`
	
    fmt.Println(s1)
    fmt.Println(s2)
}
```

#### 6.2 Interpreted string literals

Interpreted strings are enclosed in **double quotes `"..."`**.  
They support **escape sequences**:
- `\n` → newline
- `\t` → tab
- `\"` → double quote inside string
- `\\` → backslash
- `\u` / `\U` → Unicode escapes

```go
package main

import "fmt"

func main() {
    s := "Hello\nWorld\t\"Go\""
    fmt.Println(s)
}
```

#### 6.3 Raw string literals

Raw strings are enclosed in **backticks `` `...` ``**.  
They do **not** process escape sequences, so the content is preserved exactly as written. They are often used for **multiline text**, **regular expressions**, or when readability matters.

```go
package main

import "fmt"

func main() {
    raw := `Line 1
Line 2\t(with tab preserved)
Quotes: "Go"`
    fmt.Println(raw)
}
```

#### 6.4 Common operations

Strings can be concatenated with `+`, and their length can be checked with `len()`.  
Since they are UTF-8 encoded, indexing returns **bytes**, not runes.

```go
package main

import "fmt"

func main() {
    s1 := "Go"
    s2 := "Lang"
    concat := s1 + " " + s2
	
    fmt.Println("Concatenated:", concat)
    fmt.Println("Length:", len(concat))   // number of bytes
    fmt.Println("First byte:", concat[0]) // returns byte (71 -> 'G')
}
```

---

## 🔗 Related Topics

- [[Type Conversion]]
- [[Variables and Constants]]

---

## 📚 References

- [Official Go Docs](https://go.dev/doc/)
- [Go by Example](https://gobyexample.com/)
