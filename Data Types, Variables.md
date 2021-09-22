# VARIABLES:

    fn main() {
    let name = "John";
    let mut age = 25; // Creating a mutable variable
    println!("My name is {} and I am {} years old",name,age);
    age=26;
    println!("My name is {} and I am {} years old",name,age);

## Defining Constants:
    const ID: i32= 1;  
    println!("ID is {}",ID);

## Assigning multiple vars:
    let (my_name , my_age)=("Brad",30);
    println!("I am {} and I am {}",my_name,my_age);



# DATA TYPES:


## Integer:
### For integer, default is 'i32'
    let x=1;

## Float:
### For float, default is 'f64'
    let y=3.5;

## Explicit: 
### For Explicit type
    let z: i64 =459075;
    println!("x is {}, y is {}, z is {}",x,y,z);

### To Find max size
    println!("Max i32 is {}", std::i32::MAX);
    println!("Max i64 is {}", std::i64::MAX);

## Boolean:

    let is_active bool = true;
    println!("{:?}",is_active);

### To Get Boolean from expression
    let is_greater = 50>100;
    println!("{:?}",is_greater);


## Unicode charachter (char):

    let a1= 'a';
    println!("{:?}",a1);

    let face= '\u{1F600}'; //For printing smile emoticon
    println!("{:?}",face); 


## Strings:

    let mut hello= String::from("Hello ");
    println!("Length is {}",hello.len()); //To print the length of string

### To push char
    hello.push('W'); //Pushing char W into 'Hello '
    println!("{}",hello);
    
### To push string
    hello.push_str("orld!");
    println!("{}",hello);

### Capacity in bytes
    println!("Capacity is {}",hello.capacity());

### To check whether variable 'hello' is empty
    println!("Is Empty {}",hello.is_empty());

### To check for substring
    println("Contains 'World' {}",hello.contains("World"));

### To replace a string
    println!("Replace: {}",hello.replace("World","There")); //World will be replaced by There

### Loop through string by whitespace
    for word in hello.split_whitespace() {
        println!("{}",word);
    }

### Create string with capacity method
    let s= String::with_capacity(10);
    s.push('a');
    s.push('b');
    println!("{}",s);


}
