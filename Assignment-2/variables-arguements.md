# Shell scripting - Variables and Arguements

## Variables

### Rules for variable definition
1. variable can contain any alphabet, any digits and an underscore.
2. A variable must start with an alphabet or underscore. Thus it can never start with a number

### Defining a variable
variable_name=random_variable

### Accessing a variable
```bash
var1="bash";
echo "$bash";
```
### Unsetting a variable
The unset command deletes the variable and its stored data. `unset var1`

### Readonly variables
adding a `readonly` in front of the variable makes them read only which means they cannot be modified later on

## Arguements
These are passed to the shell script on runtime and can be accessed as variables inside the script. Consider the example below
```bash
echo "arg1 is $1";
echo "arg2 is $2";
```
when this script is run like `bash script.sh john doe`, $1 is replaced with john and $2 is replaced with doe.

`$0` represents the name of the script and $ represents all the arguements as a single string

`$#` represents the total number of arguements

`$$` PID of the script

