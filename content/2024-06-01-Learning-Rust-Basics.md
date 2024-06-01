---
title: Learning Rust Basics
description: "Took a course by Microsoft called 'Rust For Beginners', this article summarises my learning notes"
date: 2024-06-01
taxonomies:
  tags: [rust, programming, learning in public]
---

# Rust For Beginners

A systems programming language. Programs that require a higher level of control over machine resources that other languages like javascript, python, c# or go don't allow for.

## Similarity with C and C++

Rust does not require garbage collection

## Advantages of Rust over C and C++

- Memory safety 100% guaranteed
- Zero cost abstractions: Rust checks at compile time that these guarantees are upheld. Checking at compile time means that we don't pay for these guarantees with runtime performance, as is the case with using garbage collection.
- Expressive
- Modern: Auto-generated documentation, integrated build tooling, package manager, default testing framework, open-source package repository etc.
- Many uses: Systems programming, Web APIs, Tools and utilities, Gaming, Destop/Mobile applications and more.

## First Rust program

```
fn main() {
    println!("Hello world");
}
```

Compile and run in the terminal

```
rustc main.rs
./main
```

## Introducing Cargo

Cargo is rust's build tool, dependency manager, test runner and project bootstrapper all rolled into one

```
cargo new cargo-hello-world
cd cargo-hello-world
cargo build
cargo run [OR] ./target/debug/cargo-hello-world
cargo test
```

## Variables

- Varibales are bound to values using the keyword `let`
- Variable values are immutable by default
- `mut` makes a variable value mutable

### Constants

Just like with immutable variables, constants have values that can't change. They are always immutable and can't be used with the `mut` keyword.

Constants can only be set to an expression, not the result of a function call or anything with the value that is computed at program runtime.

Constants are available for the entire time a program runs within the scope they were declared in.

To declare a constant, you'd need to specify the value data type

```
const ITEMS_RETURNED: u32 = 42;
```

### Shadowing

- Creating a new variable with the same name as the old previous, creating a binding
- The new variable shadows the previous variable

```
fn main() {
    let x = 5;
    let x = x + 1; // x is now 6
}
```

## Scalar Data Types

Rust is a statically typed languge, which means the compiler must know the data type for each variable in your code.

The data type can be inferred.

Rust defaults to type `i32`, which is generally the fastest

### Integers

Integers are whole numbers. They can either be signed (+) or unsigned (-)

### Floating-point

Numbers with decimal points

### Boolean

- `true` or `false`
- keyword `bool`
- 1 byte in size

### Characters

- represent letters
- keyword `char`
- single quotes
- 4 bytes in size

## Compound Data Types

Data types composed of other data types

### Arrays

- continuous group of items
- fixed length
- length known at compile time
- heterogenous: contains items of same data type
- items are accessed with a `[]` index in brackets

### Tuples

Similar to arrays except that tuplees are homogenous; meaning that items can be of different types

- items are accessed with a `.` number dot notation following an index

## Functions

- argument types are always required
- return types are always required if a value is returned
- if not, return type defaults to `unit`, also known as the empty tuple
- return keyword is optional, the last value is one to be returned

```
fn name(args:types) -> opt_return_type {
    // function body
}
```

## Struct

Custom data type for grouping related values

- a type that is composed of other types
- can contain different types just like tuples
- you can name each piece of data, making it more flexible than tuples

### Different struct flavors

- Classic: each field has a name and type
- Tuple: fields have no names
- Unit: have no fields

```
// Definition
struct Car {
    make: String,
    mode: String,
    year: u32,
}

// Instantiation
fn main() {
    let car1 = Car {
        make: String::from("Ford"),
        model: String:from("Mustang"),
        year: 1978,
    };
}

// Get values
car1.year
```

## Enums

Custom types that list all the possible variants or enumeration of some data

- List all variations of some data
- aka. Algebraic data types
- Similar to structs but with more flexibility and advantages
  - Describe what kind of data will be stored, not the data itself
  - Each variant can have a different type
  - All variants are stored under the custom enum type
- An enum variant can include any kind of data (Stings, Structs, Numeric types etc.)

```
enum CardinalDirections {
    North(String),
    South(String),
    East(String),
    West(String),
}

fn main() {
    let west = CardinalDirections::West(String::from("Western Hemsphire"));
}
```

## Control Flow

### If / If..Else / Else

```
let price = 10
if price > 0 {
    println!("true");
}
```

### Match

Similar to switch in c

```
let boolean = true;

    let binary = match boolean {
        false => 0,
        true => 1,
    };

    println!("{}", binary);
```

## Loops

### Loop

Used to execute over a block of code forever, or until it is stopped using the `break` keyword, or the program quits

Loops are used in scenarios where you know an operation might fail and you need to give it another try.

### While

- Conditional loop
- Runs until condition is met or becomes false

Whats awesome about the while loop is that they eliminate the need for multiple if/else expressions and they conditionally repeat as opposed to the `loop`

### For

- Best for iterating over elements in a collection, such as an array
- With each pass of the for..loop, values are extracted from an iterator

A for loop is much more concise than the while loop. In addition, it eliminates the chance of bugs or errors from possibly going beyond the range of the elements in an array.

```
fn main() {
    // loop
    let mut i = 1;
    let something = loop {
        i *= 2;
        if i > 100 {
            break i;
        }
    };
    assert_eq!(something, 128);
    println!("{}", something);

    // while
    let mut counter = 0;
    while counter < 10 {
        println!("hello");
        counter += 1;
    }

    // for
    for item in 0..5 {
        println!("{}", item*2)
    }
}
```

## Error handling

Error handling is the process of anticipating and working with the possibility of failure. Learning how to manage errors effectively before they become a problem will be extremely helpful at saving you time and sanity.

### Panic

- Simplest way to handle errors
- Should only be used when a program comes to an unrecoverable state
- Rust emits a panic in some operation such as division by zero, or an attempt to access an index that isn't an array, vector or HashMap

```
panic!("Bye."); // Panic macro along with a message to print out when the program stops executing
```

### Options

### Result

## Terminal commands

`rustup`

`rustc --version`
