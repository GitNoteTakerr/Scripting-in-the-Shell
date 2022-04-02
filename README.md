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
- > dest d: denotes writing to a destination d
- >> dest d: denotes appending to a destination d

the command <input comm>output can be seen in the following manner in accordance to the following graph

![Screenshot (441)](https://user-images.githubusercontent.com/102430622/161391342-75ee7e80-4dd3-4fac-837e-08e529fbbdd7.png)

The following table illustrates the redirection process:

![Screenshot (443)](https://user-images.githubusercontent.com/102430622/161391547-8cdc4abf-9e70-45b7-a677-2f6603f71680.png)



