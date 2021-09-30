# REFERENCE POINTERS

A *Reference Pointer* points to a resource in memory.

For 'Primitive values' like **arrays**, you can assign another variable to a piece of data without using any reference pointer. For example, the primitive array has been shown as an example:

    let arr1 = [1,2,3];
    let arr2 = arr1;
    println!("Arrays: {:?}, (arr1,arr2));

With 'Non-primitives', if you assign another variable to a piece of data, the first variable will no longer hold the value. You'll need a reference (&) to point to the resource.
Let's setup a **vector** which is an example of 'Non-primitives':

    let vec1 = vec![1,2,3];
    let vec2 = &vec1;               //& is used for reference pointer
    println!("Vectors: {:?}", (&vec1,vec2));


# STRUCTS

*Structs* are used to create custom data types.

## Traditional Struct:
Let's create a struct 'Color':

    struct Color {              //First alphabet of struct being in Upper case in a convention
        red: u8,
        green: u8,              //u8 has values 0-255, rgb also has values 0-255
        blue: u8,                
    }
    
    fn main() {
        let mut c = Color {
            red: 255,
            green: 0,
            blue: 0,
        };

        c.red = 200;            //Mutating value of 'red' from 255 to 200

        println!("Color: {} {} {}", c.red, c.green, c.blue);            
    }

## Tuple Struct:

    struct Color(u8, u8, u8);

    fn main() {
        let mut c = Color(255,0,0);

        c.red = 200;            //Mutating value of 'red' from 255 to 200 just like before

        println!("Color: {} {} {}", c.0, c.1, c.2);
    }

### Creating another Struct, 'Person Stuct':

    struct Person {
        first_name: String,
        last_name: String
    }

### Now let's create some functions which are associated with 'Person' struct,

    impl Person {
        fn new(first: &str, last: &str) -> Person {
            Person {
                first_name: first.to_string(),    //Since we used String in 'first_name',we've to tack-on(.to) 
                last_name: last.to_string()
            }
        }

### Making a Method to Create a full name:

        fn full_name(&self) -> String {     //%self,Referencing the struct Person to replace it with 'Person'
            format!("{} {}", self.first_name, self.last_name)
        }

### Making a Method to Mutate or Change the Last name:

        fn set_last_name(&mut self, last: &str) {
            self.last_name = last.to_string();
        }

### Making a Method for Name to Tuple, we want to return first and last name:

        fn to_tuple(self) -> (String, String) {
            (self.first_name, self.last_name)
        }
    }

    fn main() {
        let mut p = Person::new("Lara","Croft");
        println!("Person: {} {}", p.first_name, p.last_name);

### To Print with full_name() method we made under impl Person:
        println!("Person: {}", p.full_name());

### Mutating the last name here through mut function:
        let mut p = Person::new("Lara","Croft);
        p.set_last_name("Williams");
        println!("Person: {}", p.full_name());

### Printing first and last name through Name to tuple we created:
        println!("Person Tuple: {:?}", p.to_tuple());
    }


