## 📖 Introduction

Data types in go specify the kinds of values that particular variables will store when you are writing a program. The data type also determines what operations can be perform on the data.

---

## 🔍 Concepts and Details

### 1. Integers

Integers are fundamental numeric types that can be signed (`int`) or unsigned (`uint`). The distinction is crucial because it determines whether negative values are allowed and how much memory the type consumes. Go provides both **architecture-dependent** integer types (`int`, `uint`) and **explicitly sized** integer types (`int8`, `int16`, `int32`, `int64`, and their unsigned counterparts).

#### 1.1 Signed vs Unsigned

- **Signed (`int`)**: can represent both negative and positive numbers.
- **Unsigned (`uint`)**: can only represent non-negative numbers (0 and above).

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

- On a **32-bit system**: `int` and `uint` are 32 bits (4 bytes).
- On a **64-bit system**: `int` and `uint` are 64 bits (8 bytes).

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

- **`float32`**: 32-bit floating point, about 6-7 decimal digits of precision.
- **`float64`**: 64-bit floating point, about 15-16 decimal digits of precision (default and recommended in most cases). 

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
* `+Inf` and `-Inf`: positive and negative infinity.
* `NaN`: "Not a Number", e.g., result of invalid operations like `0.0/0.0`.

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













## 📝 Extended Examples

Show longer, practical code snippets with explanations.

```go

```

---

## 🔗 Related Topics

- 

---

## 📚 References

- [Official Go Docs](https://go.dev/doc/)
- [Go by Example](https://gobyexample.com/)
