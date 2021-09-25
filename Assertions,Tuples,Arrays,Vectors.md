# ASSERTIONS

Let's first create a string from capacity method:

    let mut s= String::with_capacity(10);
    s.push('a');
    s.push('b');

## Assertion testing:
We generally check whether 2 parameters are equal or not.
Here we have compared through len method:

    asser_eq!(2,s.len());
Both the parameters are equal, it's not gonna show any output. If '3' was given as a parameter rather than '2', then 'Assertion error' would be shown in the output.
Now comparing through capacity method with '10':

    asser_eq!(10,s.capacity());
Similarly, both the given parameters are equal here.


# TUPLES

*Tuples* group together differnt types of values.

Let's create a simple tuple and then print it:

    let person: (&str,&str,i8) = ("John","USA",28);
    println!("{} lives in {} and is {}", person.0, person.1, person.2);


# ARRAYS

An *Array* is a fixed list where elements are same data types.

Let's create an array and print it:

    let mut numbers: [i32;5]=[1,2,3,4,5];
    println!("{:?}",numbers);

### To print a specific single value using index:
    println!("{}",numbers[0]);

### To re-assign value of any array using indexing:
    numbers[2]=30;
    println!("{:?}",numbers);

### To get array length:
    println!("Array lenth is {}",numbers.len());

### To see how many bytes are used by arrays:
    println!("Array occupies {} bytes",std::mem::size_of_val(numbers/variable));

### To get slices of array:
    let slice: &[i32]=&numbers;
    println!("Slice is {:?}",slice);

To slice first two values, then:

    let slice: &[i32]=&numbers[0..2];
    println!("Slice is {}",slice);
To slice 1st and 2nd index's values, then:

    let slice: &[i32]=&numbers[1..3];
    println!("Slice is {}",slice);


# VECTORS

*Vectors* are resizable arrays.

To create a simple vector and print it:

    let mut numbers: Vec<i32> vec![1,2,3,4];
    println!("{:?}",numbers);

### To print a specific single value using index:
    println!("{}",numbers[0]);

### To re-assign value of any vector using indexing:
    numbers[2]=30;
    println!("{:?}",numbers);

### To add on to a vector:
    numbers.push(5);
    numbers.push(6);

### To pop off the last value:
    numbers.pop();

### To get vector length:
    println!("Vector lenth is {}",numbers.len());

### To see how many bytes are used by vector:
    println!("Vector occupies {} bytes",std::mem::size_of_val(numbers/variable));

### To get slices of vector:
    let slice: &[i32]=&numbers[0..2];
    println!("Slice is {}",slice);

### Loop through vector values:
    for x in numbers.iter() {
        println!("Number: {}", x);
    }

### Loop and mutate values:
    for x in numbers.iter_mut() {
        *x *=2;  //Multiply all vector values by 2
    }
    println!("Numbers of Vec: {:?}", numbers);

