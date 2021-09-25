# CONDITIONALS

*Conditionals* are used to check the condition of something and act on it.

Let's create a conditional based upon 3 conditions:

    let age: u8 = 18;
    let check_id: bool = true;
    let knows_person = true;

### Using If/Else:
if age>=20 && check_id || knows_person {                    //&&=and , ||=or
    println!("Bartender: What would you like to drink?");
}   else if age < 20 && check_id {
    println!("Bartender: Sorry, you are not welcomed here.");
}   else {
    println!("Bartender: Please show me your ID");
}

### Shorthand If:
    let is_of_age = if age >= 20 {true} else {false};
    println!("Is of Age: {}", is_of_age);


# LOOPS

*Loops* are used to iterate until a condition is met.

Let's just create a mutable variable first:

    let mut count = 0;

## Infinite Loop:
    loop {
        count += 1;
        println!("Number: {}", count);

        if count == 10 {                //Keeping the count '10' so that it doesn't loop forever
            break;
        }
    }

## While Loop (FizzBuzz):
So we are gonna generate numbers from 0 to 100. Numbers divisible by '3','5','15' will be printed as **Fizz**,**Buzz** and **FizzBuzz** respectively.

    while count <= 100 {
        if count % 15 == 0 {
            println!("FizzBuzz");
        }else if count % 3 == 0 {
            println!("Fizz");
        }else if count % 5 == 0 {
            println!("Buzz");
        }else {
            println!("{}", count);
        }
        
        count += 1;
    }

## For Range:
    for x in 0..100 {
      if x % 15 == 0 {
            println!("FizzBuzz");
        }else if x % 3 == 0 {
            println!("Fizz");
        }else if x % 5 == 0 {
            println!("Buzz");
        }else {
            println!("{}", x);
        }      
    }


# FUNCTIONS:

*Functions* are used to store blocks of code for re-use.

    fn main() {
        greeting("Hi", "John");

### Bind function values to variables:
    let get_sum = add(5,5);
    println!("Sum: {}", get_sum);

## Closures:
They are compact functions which can be used outside variables unlike normal functions which are block scoped.

    let num3: i32 = 15;
    let add_nums = |num1: i32, num2: i32| num1 + num2 + num3;
    println!("Closure Sum: {}", add_nums(6,6));

    }

A basic function named 'greeting' can be created as follows and will be called in **fn main** as shown above.

    fn greeting(greet: &str, name: &str) {
        println!("{} {}, nice to meet you!", greet, name);
    }

A function to *return* the addition of two numbers rather than *printing* can be created as:

    fn add(num1: i32, num2: i32) -> i32 {
        num1 + num2
    }

We can bind function values as shown in **fn main**.

