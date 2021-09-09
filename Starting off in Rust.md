# Starting off in Rust

Before writing a code, it is recommended to make a **Projects** directory/folder in which all your projects will be kept as sub-folders. To make a directory named **Projects**:

    $ mkdir ~/Projects

For each project, make a different sub-folder. Let's say, a project named **"Hello_world"**. For this:

    $ cd ~/projects

    $ mkdir hello_world
    
    $ cd hello_world

## Writing the first program and running it!

Now that it's done, it is time to write and run our first program which will be basically printing the renowned programming statement ***Hello world!***. To do this, we have to make a new source file and call it **main.rs**. Now open the file you just created and type the following code in Listing 1-1:

    fn main() {
        println!("Hello world!");
    }

## Compiling and Running!

After saving the file, open the terminal and type the following commands:

     $ rustc main.rs
     $ ./main
     Hello world! 
     
 *Note that the compiling with **rustc** is fine for simple programs, but as the complexity of the projects increases, we'll have to consider other options*
