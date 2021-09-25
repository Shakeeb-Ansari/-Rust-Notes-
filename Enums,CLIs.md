# ENUMS

*Enums* are types which have a few definitive values.

Let's create an enum named 'Movement' :

    enum Movement {
### Variants:
        Up,
        Down,
        Left,
        Right
    }

    fn move_avatar(m: Movement) {
### Perform action depending on info
        match m {
            Movement::Up => println!("Avatar moving up"),
            Movement::Down => println!("Avatar moving down"),
            Movement::Left => println!("Avatar moving left"),
            Movement::Right => println!("Avatar moving right")
        }
    }

    fn main() {
        let avatar1 = Movement::Up;
        let avatar2 = Movement::Down;
        let avatar3 = Movement::Left;
        let avatar4 = Movement::Right;

        move_avatar(avatar1);
        move_avatar(avatar2);
        move_avatar(avatar3);
        move_avatar(avatar4);
    }


# CLIs

    fn main() {
        let args: Vec<String> = std::env::args().collect();

        println!("Args: {}", args);
    }

So it gives us the vector and the first element/value of the vector will be the target of the executable which is always on the 0th index of the vector. e.g, ["target/debug/-Rust-Notes-"].
If we type something after 'cargo run' command and then run it. e.g., **cargo run Hello**, it's gonna print the target of the executable as shown above as well as "Hello".

    fn main() {
        let args: Vec<String> = std::env::args().collect();
        let command = args[1].clone();          //Hello is present on 1st index.So,'Command: Hello' will print.
                                                //As Target of exe is present on 0th index.
        println!("Command: {}", command);

    fn main() {
        let args: Vec<String> = std::env::args().collect();
        let command = args[1].clone();
        let name = "Ezio";
        let status = "100%";

        if command == "Hello" {
            println!("Fratello mio,Requescant in pace,", name);
        }   else if command == "status" {
            println!("Status is {}", status);
        }   else {
            println!("That is not a valid command!");
        }
    }