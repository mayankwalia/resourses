```bash
#!/bin/bash
set -x
a=256
b=4
c=3

ans=$( expr $a + $b )
echo $ans

ans=$( expr $a - $b )
echo $ans

ans=$( expr $a \* $b )
echo $ans

ans=$( expr $a / $b )
echo $ans

ans=$( expr $a % $c )
echo $ans

ans=$( expr $a \> $b )
echo $ans

ans=$( expr $b \>= $a )
echo $ans

ans=$( expr $a \< $b )
echo $ans

ans=$( expr $b \<= $a )
echo $ans

ans=$( expr $a = $b )
echo $ans

ans=$( expr $a != $b )
echo $ans

ans=$( expr $a \| $b )
echo $ans

ans=$( expr $a \& $b )
echo $ans

str="octavio version as in Jan 2022 is 6.4.0"
reg="[oO]ctav[aeiou]*"
ans=$( expr "$str" : $reg )
echo $ans

ans=$( expr substr "$str" 1 6 )
echo $ans

ans=$( expr index "$str" "vw")
echo $ans

ans=$( expr length "$str")
echo $ans
```

# PPA Solutions

## Week 1

### PPA 1

```bash
mv *.txt level1
```

### PPA 2

```bash
file *
```

---

## Week 2

### PPA 1

```bash
echo file_{a..z}{a..z}{0..4}.txt > documents.txt
```

### PPA 2

```bash
ln /encryption/two-level/binary/positive-offset/encoding-key /ek
```

---

## Week 3

### PPA 1

```bash
ls -l *.txt > textFiles.txt 2> noFiles.txt && echo found
```

### PPA 2

```bash
cal -m $month > $month.txt 2> error.txt
```

### PPA 3

```bash
test 2> errorlog
test -e 2>> errorlog
test -n 2>> errorlog
```

---

## Week 4

### PPA 1

```bash
ls -l | grep "d......rwx" | grep -o "\S\+$"
```

### PPA 2

```bash
circle=`grep $pin Pincode_info.csv | grep -e ".* Circle" -o`
circle=${circle% Circle}
division=`grep $pin Pincode_info.csv | grep -e ",\w* Division" -o`
division=${division:1}
division=${division% Division}
echo $circle $division

# Alternative solution
# circle=`grep "$pin" Pincode_info.csv| grep -oP ".*(?= Circle)"`
# division=`grep "$pin" Pincode_info.csv| grep -oP "\w+(?= Division)"`
# echo $circle $division
```

---

## Week 5

### PPA 1

```bash
count=1
for var in "$@"; do
        if [ $((count%2)) -ne 0 ]; then
                echo -n "$var "
        fi

        ((count=count+1))
done
```

### PPA 2

```bash
  sum=0
  for i in $(cat result); do
    while read hash name; do 
      if [ $i == $hash ]; then
        inv=$(grep INVESTMENT $name)
        inv=${inv//INVESTMENT $/}
        sum=$((sum+inv))
      fi
    done < map
  done
  echo $sum
```

### PPA 3

```bash
if [ `cat data.txt | wc -l` -gt 16 ]; then
    echo "Yes"
else
    echo "No"
fi
```

---

## Week 1-5

### PPA 1

```bash
uname -a | grep "\bx.*\b" -o | cut -d ' ' -f1
```

### PPA 2

```bash
egrep "\bFAILED LOGIN\b" myauth.log | wc -l
```

### PPA 3

```bash
egrep "systemd-logind\[[0-9]+\]" myauth.log | grep user | cut -d " " -f 11 | cut -d "." -f 1 | sort | uniq
```

### PPA 4

```bash
grep "\bsession opened for user guest\b" myauth.log | tail -1 | cut -d " " -f 1-3
```

### PPA 5

```bash
egrep "\bsu\b" myauth.log | grep -v FAILED | egrep "\(to .*\)" -o | egrep "\b\w*\b" -o | grep -v to 
```

---

# Week - 5, Code with us

## Problem 1a

Write a Bash script that accepts a name(string) as input from <code>stdin</code> and prints "hello <code>input-name</code>>" as output, where <code>input-
name</code> is the input string.

Example:
If the input string is <code>Raghu</code> the output should be
<code>hello Raghu</code>

Write your script in the file <code>myScript.sh</code>.

#### main.sh

```bash
bash myScript.sh
```

#### Solution(myScript.sh)

```bash
read name
echo "hello $name"
```



## Problem 1b

Write a Bash script that accepts a name(string) as command line argument to your script <code>myScript.sh</code> and prints "hello <code>input-name</code>" as output, where <code>input-
name</code> is the input string.

Example:
If the command line input string is <code>Raghu</code> the output should be
<code>hello Raghu</code>

Write your script in the file <code>myScript.sh</code>.

#### main.sh

```bash
read var
bash myScript.sh $var
```

#### Solution(myScript.sh)

```bash
echo "hello $1"
```



## Problem 1c

Write a bash script that reads two numbers from the standard input and prints the sum of the numbers. Assume that the input will be numeric only.
Write your script in the file <code>myScript.sh</code>.

#### main.sh

```bash
bash myScript.sh 
```

#### Solution(myScript.sh)

```bash
read a
read b
echo "$[ $a+$b ]"
# OR
#echo $(($a+$b))
#OR 
#echo `expr $a + $b` #space before and after '+' is important here
#OR
#sum=`expr $var1 + $var2`
#echo $sum
```



## Problem 2

Write a bash script that takes two arguments, checks if both the arguments are positive integers then prints their sum; else prints "NOT INTEGERS" to STDERR and exit with exit code 1.

Note: Use the below if else conditional statment if needed

```bash
if condition; then
	...
	...
else
	...
	...
fi
```

#### Main.sh

```bash
read arg1
read arg2
((arg1 + arg2))
if [ $? = 0 ]; then
  bash ./script.sh $arg1 $arg2 
else
  bash ./script.sh $arg1 $arg2 1> /dev/null
  echo $?
fi
```

#### Solution

```bash
if [ `echo $1 | egrep '^[0-9]+$'` ] && [ `echo $2 | egrep '^[0-9]+$'` ]; then
  echo $(($1+$2))
else
  echo "NOT INTEGERS" >&2
  exit 1
fi

# Or can use the below if condition to check for integers
#pat='^[0-9]+$'
#if ! [[ $1 =~ $pat && $2 =~ $pat ]]; then
```

## Problem 3

Write a bash script that takes two arguments, checks if both the arguments are positive integers then prints their sum; else concatenate the string values in both the arguments and prints the combined string.

### Solution

```bash
if [ `echo $1 | egrep '^[0-9]+$'` ] && [ `echo $2 | egrep '^[0-9]+$'` ]; then
  echo $(($1+$2))
else
  echo $1$2
fi

# Or can use the below if condition to check for integers
#pat='^[0-9]+$'
#if ! [[ $1 =~ $pat && $2 =~ $pat ]]; then
```



## Problem 4

Write a bash script that accepts a file path as an argument and checks if that exists and is readable by current user and prints the output as below.

- Prints "DOES NOT EXIST" on STDERR and return with error code 1 if the file does not exist at the given path.
- Prints "NOT READABLE" on STDERR and return with error code 2 if the file is not readable by current user.
- Prints "WOO HOO" if the file exists and is readable too.

Note: Use the below if elif conditional statment if needed

```bash
if condition; then
	...
	...
elif condition; then
	...
	...
else
	...
	...
fi
```

### Solution

```Bash
if ! [ -e $1 ]; then
  echo "DOES NOT EXISTS" >&2
  exit 1
elif ! [ -r $1 ]; then
  echo "NOT READABLE" >&2
  exit 2
else
  echo "WOO HOO"
fi
```



## Problem 5

Write a bash script which takes in the value of `n` and prints it in reverse order (For example if input number is 123, the Output will be 321)

### Solution

```bash
n=$1
counter=0
ans=0
while [ $n -gt 0 ]
do
    counter=$(( $n % 10 ))
    ans=$(( $ans * 10 + $counter ))
    n=$(( $n / 10 ))
done
echo $ans
```

## Problem 6

Write a bash script that accepts an integer say `n` and prints the below pattern  till `n` lines.

```
*
**
***
****
*****
```

In the above sample the value of `n` is 5.

### Solution

```
n=$1
i=1
while [ $i -le $n ]; do
  j=1
  while [ $j -le $i ]; do
    #printf "*"
    echo -n "*"
    j=$((j+1))
  done
  echo
  i=$((i+1))
done
```

## Problem 7

Write a bash script which takes in the value of `n` and prints whether the number is prime or not. If n is a prime number, the program must print "Prime" and if not, it must print "Not Prime"

### Solution

```bash
flag=0
n=$1
for (( i=2; i<=$n; i++ )); do
	if [ $((n%i)) -eq 0 ]; then
		flag=1
	fi
done
if [ $flag -eq 0 ]; then
	echo "Prime"
else
	echo "Not Prime"
fi
```

## Problem 8

`df -h` gives the disk/filesystem usage information. Write a bash script to list all the filesystem mount point  names based on their percentage usage divided in 5 categories in the format below.

```
0-50
(names of filesystem one in each line with usage between 0 to 50%)
50-75
(names of filesystem one in each line with usage between 50 to 75%)
75-85
(names of filesystem one in each line with usage between 75 to 85%)
85-95
(names of filesystem one in each line with usage between 85 to 95%)
>95
(names of filesystem one in each line with usage above 95%)
```

In each category print the range in one line followed by the filesystem mount point names. Print the range string even if there are no filesystem with usage in that range. Your script should not print anything else, all other errors and ouput from your script should be redirected to /dev/null.

Filesystem mount point name is the last field in the output of df -h.

 The categories are

- 0% to less than 50% usage.
- 50% to less than 75% usage.
- 75% to less than 85% usage.
- 85% to less than 95% usage.
- Equal and above 95% usage.

Hint: Can store the df command output in a file. Then work on the file named `dfOutput.csv` line by line using

```Bash
while read -r line;
do
   echo $line; # To print the line.
   # Write your code to process the line.
done < dfOutput.csv
```

Use ${var:0:-1} to remove the last character of string var.

###  Solution with arrays

```bash
df -h >dfOutput.csv

ar1=()
ar2=()
ar3=()
ar4=()
ar5=()
while read -r line
do
  var=`echo $line | cut -d " " -f 5`
  usage=${var:0:-1}
  if [[ `echo $usage | egrep '^[0-9]+$'` ]]; then
    if [[ $usage < 50 ]]; then  
      ar1+=(`echo $line | cut -d " " -f 6`)
    elif [[ $usage < 75 ]]; then  
      ar2+=(`echo $line | cut -d " " -f 6`)
    elif [[ $usage < 85 ]]; then  
      ar3+=(`echo $line | cut -d " " -f 6`)
    elif [[ $usage < 95 ]]; then  
      ar4+=(`echo $line | cut -d " " -f 6`)
    else
      ar5+=(`echo $line | cut -d " " -f 6`)
    fi
  fi
done < dfOutput.csv

echo '0-50'
printf '%s\n' "${ar1[@]}"
echo '50-75'
printf '%s\n' "${ar2[@]}"
echo '75-85'
printf '%s\n' "${ar3[@]}"
echo '85-95'
printf '%s\n' "${ar4[@]}"
echo '>95'
printf '%s\n' "${ar5[@]}"

rm dfOutput.csv 2>/dev/null 
```

### Solution with files

```bash
df -h >dfOutput.csv

touch range1 range2 range3 range4 range5 2>/dev/null
while read -r line
do
  var=`echo $line | cut -d " " -f 5`
  usage=${var:0:-1}
  if [[ `echo $usage | egrep '^[0-9]+$'` ]]; then
    if [[ $usage < 50 ]]; then  
      echo $line | cut -d " " -f 6  >>range1
    elif [[ $usage < 75 ]]; then  
      echo $line | cut -d " " -f 6  >>range2
    elif [[ $usage < 85 ]]; then  
      echo $line | cut -d " " -f 6  >>range3
    elif [[ $usage < 95 ]]; then  
      echo $line | cut -d " " -f 6  >>range4
    else
      echo $line | cut -d " " -f 6  >>range5
    fi
  fi
done < dfOutput.csv

echo '0-50'
cat range1
echo '50-75'
cat range2
echo '75-85'
cat range3
echo '85-95'
cat range4
echo '>95'
cat range5

rm dfOutput.csv range1 range2 range3 range4 range5 2>/dev/null
```

## Problem 9

In Problem 8, modify the output of your script as below.

- Print the range string only if there is a filesystem in that range.

For example if there is no filesystem with usage >95% and also none in the range 75-85, and rest all range has atleast one filesystem with usage in that range than your output should be

```
0-50

(names of filesystem one in each line with usage between 0 to 50%)

50-75

(names of filesystem one in each line with usage between 50 to 75%)

85-95

(names of filesystem one in each line with usage between 85 to 95%)
```

### Solution

```bash
df -h >dfOutput.csv

touch range1 range2 range3 range4 range5 2>/dev/null
while read -r line
do
  var=`echo $line | cut -d " " -f 5`
  usage=${var:0:-1}
  if [[ `echo $usage | egrep '^[0-9]+$'` ]]; then
    if [[ $usage < 50 ]]; then  
      echo $line | cut -d " " -f 6  >>range1
    elif [[ $usage < 75 ]]; then  
      echo $line | cut -d " " -f 6  >>range2
    elif [[ $usage < 85 ]]; then  
      echo $line | cut -d " " -f 6  >>range3
    elif [[ $usage < 95 ]]; then  
      echo $line | cut -d " " -f 6  >>range4
    else
      echo $line >&2
      echo $line | cut -d " " -f 6  >>range5
    fi
  fi
done < dfOutput.csv

if [[ -s range1 ]]; then
	echo '0-50'
	cat range1
fi
if [[ -s range2 ]]; then
	echo '50-75'
	cat range2
fi
if [[ -s range3 ]]; then
	echo '75-85'
	cat range3
fi
if [[ -s range4 ]]; then
	echo '85-95'
	cat range4
fi
if [[ -s range5 ]]; then
	echo '>95'
	cat range5
fi

rm dfOutput.csv range1 range2 range3 range4 range5 2>/dev/null
```

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




