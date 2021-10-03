# Ownership in Rust:

Ownership is Rust’s most unique feature, and it enables Rust to make memory safety guarantees without needing a garbage collector. Some **rules** of ownership in rust are:
- Each value in Rust has a variable that’s called its owner.
- There can only be one owner at a time.
- When the owner goes out of scope, the value will be dropped.

## Scope:
A scope is the range within a program for which an item is valid. Let’s say we have a variable that looks like this:

```rust
let s = "hello";
```
The variable ```s``` refers to a string literal.

```rust
fn main() {
    {                           // s is not valid here, it’s not yet declared
        let s = "hello";        // s is valid from this point forward

        
    }                           // this scope is now over, and s is no longer valid
}
```

So there are two points to be remembered:
- When ```s``` comes into scope, it is valid.
- It remains valid until it goes out of scope.

## The String Type:
 To illustrate the rules of ownership, we need a data type that is more complex than the ones we covered in the *Data Types* section of **Chapter 3**. The types covered previously are all stored on the stack and popped off the stack when their scope is over, but we want to look at data that is stored on the heap and explore how Rust knows when to clean up that data.
 We’ll use ```String``` as the example here and concentrate on the parts of ```String``` that relate to ownership. These aspects also apply to other complex data types.
 String literals **(&str and str)** are convenient, but they aren’t suitable for every situation in which we may want to use text. One reason is that they’re immutable. Another is that not every string value can be known when we write our code: for example, what if we want to take user input and store it? For these situations, Rust has a second string type, ```String```. This type is allocated on the **heap** and as such is able to store an amount of text that is unknown to us at compile time. You can create a ```String``` from a string literal using the from function, like so:

```rust
let s = String::from("hello");
```
This type of string can be *mutated* unlike string literals.

```rust
let mut s = String::from("hello");

 s.push_str(", world!");            // push_str() appends a literal to a String

 println!("{}", s);                 // This will print `hello, world!`
 ```
 
 So basically, the difference b/w type ```String``` and string literals is how these two types deal with memory i.e., **Stack** and **Heap**.
 
## Memory Allocation:
 We know the contents at compile time if we are talking about string literals. But with the ```String``` type, in order to support a mutable, growable piece of text, we need to allocate an amount of memory on the **heap**, unknown at compile time, to hold the contents. This means:
 - The memory must be requested from the memory allocator at runtime.
 - We need a way of returning this memory to the allocator when we’re done with our ```String```.

That first part is done by us when we call ```String::from```, its implementation requests the memory it needs. This is pretty much universal in programming languages.
However, for the second part, we know *Rust* doesn't use the algorithm of **Garbage Collector** so it takes up a different path i.e., the memory is automatically returned once the variable that owns it goes out of scope. Here’s a version of our scope example:

```rust

 {
     let s = String::from("hello"); // s is valid from this point forward

        
 }                                  // this scope is now over, and s is no longer valid
 ```
 
## Comparison between an integer and String:
 Multiple variables can interact with the same data in different ways in Rust. Let’s look at an example using an integer:
 
 ```rust
 let x = 5;
 let y = x;
 ```
Here we can see that we bind the value ```5``` to ```x``` then made a copy of the value in ```x``` and bind it to ```y```. This is possible because integers are simple values with a known, fixed size, and these two ```5``` values are pushed onto the stack.

Now let’s look at the ```String``` version:

```rust
let s1 = String::from("hello");
let s2 = s1;

println!("{}, world!", s1);
```
This looks very similar to the previous code, so we might assume that the way it works would be the same: that is, the second line would make a copy of the value in ```s1``` and bind it to ```s2```. But this isn’t quite what happens and this will also give an error like this:

```rust
$ cargo run
   Compiling ownership v0.1.0 (file:///projects/ownership)
error[E0382]: borrow of moved value: `s1`
 --> src/main.rs:5:28
  |
2 |     let s1 = String::from("hello");
  |         -- move occurs because `s1` has type `String`, which does not implement the `Copy` trait
3 |     let s2 = s1;
  |              -- value moved here
4 | 
5 |     println!("{}, world!", s1);
  |                            ^^ value borrowed here after move

error: aborting due to previous error

For more information about this error, try `rustc --explain E0382`.
error: could not compile `ownership`

To learn more, run the command again with --verbose.
```
If we want to **overcome** this and ff we do want to deeply copy the heap data of the String, not just the stack data, we can use a common method called ```clone```.
Here’s an example of the ```clone``` method in action:

```rust
fn main() {
    let s1 = String::from("hello");
    let s2 = s1.clone();

    println!("s1 = {}, s2 = {}", s1, s2);
}
```

This works just fine and the **heap** data does get copied.





 
                                       

