## Problem-1
Write a Bash command to print the details of the CPU of the system. Example in the format: `Intel(R) Core(TM) i5-1035G1 CPU @ 1.00GHz`

There is a file named `final.txt` in the current working directory, that contains some text that you do not want it to be edited.
Write a bash command to remove write permissions of user from this file. Do not edit any other file permissions.

## Problem 2

A school teaches from first to twelfth standard, each standard has 5 sections named as `A` to `E`. The class room number is represented as standard(as number) followed by the section, for example `12E`, `3C`, etc..

Your task is to create a directory for every class room. All the directories should be located inside the current directory.


## Problem 3

A school teaches from first to twelfth standard, each standard has 5 sections named as `A` to `E`. The class room number is represented as standard(as number) followed by the section, for example `12E`, `3C`, etc..
Each classroom has 40 students. There is a directory for every classroom. All the directories are located inside the current directory. 

Write a Bash command to create a file for each student, namet the files from 1 to 40 in every directory.


## Problem 4

A school teaches from first to twelfth standard, each standard has 5 sections named as `A` to `E`. The class room number is represented as standard(as number) followed by the section, for example `12E`, `3C`, etc..
Each classroom has 40 students. There is a directory for every classroom. All the directories are located inside the current directory. There is a file for every student named from 1 to 40 in every classroom directory.

Suddenly the school experienced 40% drop in first and sixth standard so they reduced the number of students in each class room to 32. 

Your task is to remove the extra files in the respective directories, i.e. named from 33 to 40.


## Problem 6
Find the mime type of `somefile`. 
Hint: Use `file`. Refer manual of `file` or `file --help`

## Problem 7
Find the day of week of April 1st of 2024 and print it to the output in full format with first letter capitalised. Ex: `Wednesday`
Hint: Use `date` command.

## Problem 8
The shell variable `logfile` contains the absolute path to some file. Your task is to print two lines, where first line is the filename alone and the second line is the path of the directory in which the file `logfile` is located(print the path without the trail slash `/`).

Example shell variable: `logfile=/home/student78/daily.log`

**Output**

```
daily.log
/home/student78
```



A shell varialbe named `TOTALCOST` contaisn a string which is in the format `XYZ_ABC_PQR`, where `XYZ`, `ABC` and `PQR` are three digit numbers. Underscore `_` is used to separate the three digit numbers

Write a bash script that replaces all the underscores(`_`) with commas(`,`) in the variable `TOTALCOST` and displays the final string on the screen.

Example: `TOTALCOST=198_890_128`

**Output**

```
198,890,128
```

Display only the filename without extension whose absolute path is stored in a shell variable named `file`. The extension should not include the dot `.`.

Example: `file=/home/student56/tmp/artic.jpg`

**Output**

```
artic
```


The array `colors` contains the name of the colors. Your task is to remove all vowels present in the array and display them.

Example: `colors=(violet indigo blue green yellow orange red)`

**Output**

```
vlt ndg bl grn yllw rng rd
```

Write a Bash command that displays the name and size in bytes of all the files/directory present in the current directory.

Hint: Refer man page of `stat`

Example:

**Output**

```bash
au 0
other 4096
temp.sh 259
```

Write a command to display the today's date in a format `18th Jan 2022`.

# Week - 2, Code with us
## Problem 1

Find the CPU used in the machine and print it. Ex: `Intel(R) Core(TM) i5-1035G1 CPU @ 1.00GHz`

### Solution
```bash
# It will be different for every user. Read the file /proc/cpuinfo. The cpu used will be mention after `model name`
echo AMD EPYC 7B12
```

---
## Problem file perms
There is a file named `final.txt` in the current working directory, that contains some text that you do not want it to be edited.
Write a bash command to remove write permissions of user from this file. Do not edit any other file permissions.

### Solution
```bash
chmod u-w final1.txt
```


---
## Problem 2

In a school consists of first to twelfth standard, each standard have 5 sections named from `A` to `E`. So the class room number is given as standard in number followed by section, for an example `12E`, `3C`, etc..

Your task is to create a directory for every class room. All the directories should be located inside the current directory.

### Solution
```bash
mkdir {1..12}{A..E}
```

---
## Problem 3

In a school consists of first to twelfth standard, each standard have 5 sections named from `A` to `E`. So the class room number is given as standard in number followed by section, for an example `12E`, `3C`, etc.. Each classroom have 40 students. There is a directory for every class room. All the directories can be located inside the current directory. 

Your task is to create a file for each student named from 1 to 40 in every directory.


### Solution
```bash
touch {1..12}{A..E}/{1..40}
```

---
## Problem 4

In a school consists of first to twelfth standard, each standard have 5 sections named from `A` to `E`. So the class room number is given as standard in number followed by section, for an example `12E`, `3C`, etc.. Each classroom have 40 students. There is a directory for every class room. All the directories can be located inside the current directory. There is a file for every student named from 1 to 40 in every directory.

Suddenly the school experienced 40% drop in first and sixth standard so they reduced the number of students in each class room to 32. 

Your task is to remove the extra files in the respective directories.

### Solution
```bash
rm {1,6}{A..E}/{33..40}
```

---
## Problem 6
Find the mime type of `somefile`. 
Hint: Use `file`. Refer manual of `file` or `file --help

### Solution

```bash
file somefile --mime-type
```

---
## Problem 7
Find the day of week of April 1st of 2024 and print it to the output in full format with first letter capitalised. Ex: `Wednesday`
Hint: Use `date` command.

### Solution
```bash
date -d "2024-04-01" +%A
```

---

## Problem 8
The shell variable `logfile` contains the absolute path to some file. Your task is to print two lines, where first line is the filename alone and the second line is the path of the directory in which the file `logfile` is located(print the path without the trail slash `/`).

Example shell variable: `logfile=/home/student78/daily.log`

**Output**

```
daily.log
/home/student78
```

### Solution
```bash
logfile=/home/student78/daily.log
echo "${logfile##*\/}"
echo "${logfile%\/*}"
```

---


## Problem 9
A shell varialbe named `TOTALCOST` contaisn a string which is in the format `XYZ_ABC_PQR`, where `XYZ`, `ABC` and `PQR` are three digit numbers. Underscore `_` is used to separate the three digit numbers

Write a bash script that replaces all the underscores(`_`) with commas(`,`) in the variable `TOTALCOST` and displays the final string on the screen.

Example: `TOTALCOST=198_890_128`

**Output**

```
198,890,128
```

### Solution
```bash
echo "${TOTALCOST//_/,}"
```
---

## Problem 10
Display only the filename without extension whose absolute path is stored in a shell variable named `file`. The extension should not include the dot `.`.

Example: `file=/home/student56/tmp/artic.jpg`

**Output**

```
artic
```

### Solution
```bash
temp="${file%.*}"
echo "${temp##*\/}"
```

---
## Problem 11
The array `colors` contains the name of the colors. Your task is to remove all vowels present in the array and display them.

Example: `colors=(violet indigo blue green yellow orange red)`

**Output**

```
vlt ndg bl grn yllw rng rd
```

### Solution
```bash
colors="${colors[@]//a/}"
colors="${colors[@]//e/}"
colors="${colors[@]//i/}"
colors="${colors[@]//o/}"
colors="${colors[@]//u/}"
echo "$colors"

# or

echo "${colors[@]//[aeiou]/}" 
```

---

## Problem 13
Write a Bash command that displays the name and size in bytes of all the files/directory present in the current directory.

Hint: Refer man page of `stat`

Example:

**Output**

```bash
au 0
other 4096
temp.sh 259
```

### Solution

```bash
stat -c "%n %s" *
```

---
## Problem 14
Write a command to display the today's date in a format `18th Jan 2022`.

### Solution

```bash
date +"%dth %b %Y"
```



# Week 7, Code with us

## Problem-1

A software company has published some best practices for writing the code. One of the best practices mentioned is that no line in your code should exceed 50 characters in total including all types of characters or spaces.

Write a bash script using sed that prints the names of all .c files that contain one or more lines with a length of more than 50 characters(as specified above).

**Hint:** Use q [exit code]

### Solution

```bash
for file in *.c; do
  sed -nE '/.{51,}/ q 51' $file || echo $file
done
```

---

## Problem-2

Write a command using sed to print the contents of file in the format `<line number>:<contents>`.

### Solution

```bash
sed '=' $filename | sed 'N; s/\n/:/'
```

---

## Problem-3

The command `cut -d " " -f 5 lsoutput` is executed to extract the size of the file. But the `lsoutput` contains multiple spaces between fields and for some reason we cannot change the cut command. Your task is to pre-process the file `lsoutput` to work with the cut command.

Hint: Use the -i option in sed to do the modification in the file.

### Solution

```bash
sed -i -E "s/ {2,}/ /g" lsoutput
```

---

## Problem-4

In python, the multiline comments can be bounded by either `'''` or `"""`. 

Write a sed script `script.sed` that converts all the comments inside the triple quotes to single-line comment (preceded by #) and remove the lines inside the triple quotes that do not have any contents.

**Sample Input:**
```
print(1)
"""
This is a comment 1
"""
print(2)
"""This is a comment 2
"""
print(3)
"""
This is a comment 3"""
print(4)
"""This is a comment 4"""
print(5)
"""This is a comment 5"""
print(6)
```

**Sample Output**
```
print(1)
#This is a comment 1
print(2)
#This is a comment 2
print(3)
#This is a comment 3
print(4)
#This is a comment 4
print(5)
#This is a comment 5
print(6)
```

### Solution

```sed
# To remove inline triple quotes
s/['"]\{3\}\(.*\)['"]\{3\}/#\1/;

# To remove multi-line triple quotes
/['"]\{3\}/, /['"]\{3\}/ s/^/#/; s/['"]\{3\}//g; /^#$/d
```

---

## Problem-5

Write a sed script `script.sed` to extract the content inside every `<td>` tags. Print all the non-empty extracted contents with leading and trail spaces trimmed in the source order.

Note: Add more options to sed execution in main.sh if required.

**Sample Input**
```
<html>
<head>
    <title>Example script for sed</title>
</head>

<body>
    <h1>Welcome to sed programming</h1>
    <p>sed is a steam editor known for manipulation of text.<br>
        sed can manipulate the text in the pipeline and can be used alond with other commands as well</p>
    <b>Frequently used options with sed</b>
    <table>
        <tr>
            <td> -n, --quiet, --silent </td>
            <td> suppress automatic printing of pattern space </td>
        </tr>
        <tr>
            <td> -e script, --expression=script </td>
            <td> add the script to the commands to be executed </td>
        </tr>
        <tr>
            <td> -f script-file, --file=script-file </td>
            <td> add the contents of script-file to the commands to be executed </td>
        </tr>
        <tr>
            <td> -i[SUFFIX], --in-place[=SUFFIX] </td>
            <td> edit files in place (makes backup if SUFFIX supplied) </td>
        </tr>
        <tr>
            <td> -l N, --line-length=N </td>
            <td> specify the desired line-wrap length for the `l' command </td>
        </tr>
        <tr>
            <td> -E, -r, --regexp-extended </td>
            <td> use extended regular expressions in the script (for portability use POSIX -E). </td>
        </tr>
    </table>
</body>
</html>
```

**Sample Output**
```
-n, --quiet, --silent
suppress automatic printing of pattern space
-e script, --expression=script
add the script to the commands to be executed
-f script-file, --file=script-file
add the contents of script-file to the commands to be executed
-i[SUFFIX], --in-place[=SUFFIX]
edit files in place (makes backup if SUFFIX supplied)
-l N, --line-length=N
specify the desired line-wrap length for the `l' command
-E, -r, --regexp-extended
use extended regular expressions in the script (for portability use POSIX -E).
```

### Solution

```bash
#!/usr/bin/sed -f

/<td>/, /<\/td>/ {
  s/<td>//
  s/<\/td>//
  s/^[[:space:]]*//g
  s/[[:space:]]*$//g
  /^$/d
  p
}
```

---




