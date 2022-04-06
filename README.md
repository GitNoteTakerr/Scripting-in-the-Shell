# Streams and Redirection
Every command in the terminal in linux runs on three main connections: 

>stdin: where the command gets its input

>stdout: where the normal output is printed

>sterr: all output concering errors is printed here

stdin is connected to our keyboard normally, while stdout and stderr are connected to the terminal (since the output of commands and any error is printed onto the terminal).

stdin is denoted by 0, stdout is denoted by 1 and stderr is denoted by 2

![Screenshot (439)](https://user-images.githubusercontent.com/102430622/161391221-f8740172-51f7-4278-8468-dbf111bb2bdc.png)

# Redirection

The most common forms of redircetion is the greater and less than signs. 

- source s <: denotes reading from the source s
- \> dest d: denotes writing to a destination d
- \>> dest d: denotes appending to a destination d

the command <input comm>output can be seen in the following manner in accordance to the following graph

![Screenshot (441)](https://user-images.githubusercontent.com/102430622/161391342-75ee7e80-4dd3-4fac-837e-08e529fbbdd7.png)

The following table illustrates the redirection process:

![Screenshot (443)](https://user-images.githubusercontent.com/102430622/161391547-8cdc4abf-9e70-45b7-a677-2f6603f71680.png)

# Remote Computing:

Bash can be used to access computer remotely. A computer can be accessed remotely using ssh (secure shell), scp (secure copy) and rsync commands. rsync is the most efficient out of them since it will keep retrying incase of network failure. scp and rsync work the same by providing copies of the files on the remote computer however rsync will provide a single copy of a file rather than sending duplicate files (lise scp) and it will keep retrying to copyy all files in the case of network failure.

# ftp
File Transfer Protocol: this utility helps you to connect and login to remote hosts. It allows one computer to get (download) and put (upload) files and data from and to another computer. 

$ ftp hostname or ip-address

the aboe command will prompt the user for a login and password

# Some More Commands

![Screenshot (446)](https://user-images.githubusercontent.com/102430622/161391873-03016e5c-e759-4a1a-a78c-c6af9c37bb6e.png)

# Scripting in the Shell

Variables in the shell can be Scalar (capable of holding a single value numeric or string) and array (capable of holding multiple values)

For example, we can declare varibales by simply giving a name (ex. duration=10). If a strong does not have any spaces, no need to quote them, however if it contains spaces, it needs to be quoted (ex. artist=Baauer; song="Harlem Shake").

To declare an array we can simply use the brackets (ex. cart=(apples oranges bananas))

To reference variables we need to preceed the name with a dollar symbol $ ex...

str='$song by ${artist}' --the curlies are optional; echo $str--the single quotes will not print the values of the variables but rather print the word "$song" (they do not interpolate)

str="$song by $artist" will print the values of the variables

echo ${cart[0]} --here the curly brackets are required, this displays the first element in the array (apple)

To print the whole array we can use echo ${cart[\*]} or echo ${cart[@]}

-> print string length: echo ${#str}

- substring: ${str:7}--prints from char 8 till the end. ${str:7:8} will print starting from char 8 and only 8 characters. so $str="hello my name is kamil". echo ${str:7:8} will print "y name i" (y is the 8th character and the total length of the substring is 8 characters)

- echo ${str: -6} will only print the last 6 characters. the space before the -6 is necessory for it to work

- echo ${str#?} will print everything except the first character

- echo ${str%?} will print everything except the last character

- to find and replace just use echo ${str//Harlem//UMBC}--this will find Harlem and replace it with UMBC

- It should be noted that environment variables (reserved variables such as $PATH and $HOME) are always in all caps while local script variables tend to be in lowercase. vairiable naming is case sensitive

If a script file let's say called args.sh takes arguments I can echo those arguments. For examgple $./args.sh foo bar... I can echo the name of the file by echo $0; echo the number of arguments by echo $# (2); echo the arguments using echo $1 for the 1st argument ($n for the nth argument). If I have more than 10 arguments I use the curly bracelets (echo ${11}--will echo the 11th argument). to print all the arguments just do echo $*
# Command Line Arguments
example: ./command arg1 arg2 arg3
$0= ./command
$1= arg1
$2=arg2
$n is the nth command line argument passed to a certain command or a file. These can be useful when we want to write more complex scripts in a file and need input from the command line.
# Some Special Variables

- $$ will print the pid of the current process 
- $PPID will the PID of the Parent Process of the current process
- $? will print the exit status of the process. If the exit status is 0 then the process terminated without successfully. If it is greater than 0 then it terminated unsuccessfully

# Globbing

Globbing is similar to REGEX. 

- A question mark ? will denote a single character in this position. so ls ?.txt will print all txt files that have names of a single character

- \* 0 or more occurences. so ls \*.txt will match all files with the txt extension

- [-] will match anything in the character class  

- {---,---,---} will match anything (atleast 1) in this set.
- We can combine the globbing like ls \*{.txt,.sh} to print all files that are either txt files or shell files

# Pipes in Script

We can use pipes as a way to redirct output of one command to another. 

echo -n $str|wc -c will return the the number of character of $str.

find -type f -size +10M|wc -l will return the number of files that have a size greater than 10M

# Control Structures

we can use the test command to test for a certain condition. The condition is writter in the form of [ expression ]. The spaces are essential. They are required for the expression to work.

![Screenshot (462)](https://user-images.githubusercontent.com/102430622/161949576-39635312-cbf2-46de-9281-19d99ba8e88c.png)

![Screenshot (463)](https://user-images.githubusercontent.com/102430622/161949600-b51394cd-42f2-47c4-bf94-63e1c257df1a.png)

# Conditional Statements

- if [ expression ] then (task) fi
- if [ expression ] then (task) else (another task) fi
- if [ expression ] (task) elifn then [ another expression ] (another task) fi
The statements are written in the form case.....esac

case word in
  pattern1)
    task1 is executed if word matches pattern 1
    ;;
  pattern2)
    task2 is executed if word matches pattern 2
    ;;
  pattern3)
    task3 is executed if word matches pattern 3
    ;;
 esac
 
# Looping
1. For Loop:
    for var in some range or file;
    
    do
     
      echo $var ( or whatever task is in here lol)
    
    done
    
    for k in [1-5];
    
    do
   
      echo "hello_$k">>file_$k;
    
    done
    
    The semi column will end the command the same way return would
    
    
    for ((x=30; x<=45; x+=5));
    
    do
      
      echo $x;
    
    done

2. While Loop:
    
    a=0
    
    while [ $a -lt 10 ]
    
    do
      
      echo $a
      
      a=\`expr $a+1\`
    
    done
    
    The while loop will execute until the expression is false
    
3. Until Loop:
  
  until [ ! $a -lt 10 ]
  
  do
    
    echo $a
    
    a=\`expr $a +1\`
  
  done
  
  It will keep executing the statements until a is not less than 10 or a is greater than 10. SO until will keep executing so long the expression is false. When it   becomes true, it stops executing.

4. Select Loop:
  The select loop provides an easy way to create a numbered menu from which users can select options.
  ex....
  
  select DRINK in tea coffee water juice appe all none
  
  do
    
    case $DRINK in 
        tea|coffee|water|all)
          echo "Go to canteen"
          ;;
        juice|appe)
            echo "Available at home";;
        none)
            break;;
        *) echo "ERROR: 
        
# Input/Output

We use read to take input from the user. The -p option will print a statement and prompt input, we use -s option to hide what we are typing (useful for passwords), we use the -t <seconds> to timeout the input request after the specified number of seconds.
  
printf command: this command is used to print out on the screen (stdout).
printf "%s %s %d %d...%s will reference a string, %d will reference a digit or int...printf"10%d%10d%10d" 1 2 3....will print 1 2 and 3 with 10 10 spaces between each number. 
  
printf "My name is \"%s\".\nIt's a pleasure to meet you." "John"...the %s will be replaced by "John"
  
printf "%d plus %5f %s %.3f." 5 5.05 "equals" 10.05
  
%d: 5
  
%5f: 5.050000

%s: equals

%.3f: 10.05
  
# The source command:

takes a path and executes the commands specified in that path ex...

# Functions:
A function can be defined by the name of the function followed by brackets 
  ex... function()
  then open curly brackets 
  function(){
  \> ls -la
  \> echo "Directory listing"
  \> PWD
  \> dat
  \>}
Indentation has no special meaning in function definition

Spaces however are critical...when assigning variables no spaces between the equal signs 

we need spaces when we use the square backets for expressions [ expression ]

#: for comments in the script
  
We can also pass arguments when we run a script through ./script arg1 arg2 arg3

arg1=$1

arg2=$2

# Arithematic Operations:

we must surround our arithematic expression with $((arithematic))

echo $((2*2)) will output 4
  
we can also use expr
expr 2 \* 2 will output 4. The spaces are essential and the multiplication sign must be escaped using the back slash

Bash is very weak when it comes to arithematic operations and it is advised not to be used when you want to handle more complex mathematical operations.
...

  
