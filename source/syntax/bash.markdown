---
layout: page
#title: "Hall Of Syntax"
comments: true
sharing: true
footer: true
sidebar: false
---
<p style="margin-top:0.5em; margin-bottom:0.3em"><strong><a href="/syntax">Hall of Syntax</a> -> Bash content:</strong>
<ul>
    <li><a href="#source">source and export</a></li>
    <li><a href="#arguments">Arguments</a></li>
    <li><a href="#redirecting">Redirecting and piping</a></li>
    <li><a href="#cond">Conditional expressions</a></li>
    <li><a href="#loops">Loops</a></li>
    <li><a href="#funcs">Functions</a></li>
</ul>
</p>

<br><strong><a name="source"></a></strong>
Source and export are fundamental when you need to use other scripts or to be sure that child processes have see the variables they need: 
``` bash source and export
#!/bin/bash

# source executes a script in the context of the calling shell
source script.sh
# source can be called by a single dot
. script.sh
# not to be confused with a dot at the beginning of a path which means "current directory"
. ./dir1/script.sh
# not to be confused with a dot at the beginning of a filename which indicates a hidden file
. ./dir1/.script.sh

# settings variables makes them available in the current process only
FOO="HELLO WORLD"
# any child process won't see $FOO

# exported variables get passed on to child processes, non-exported variables do not
export FOO="HELLO WORLD"
# any child process now will see $FOO

unset FOO
```

<br><strong><a name="arguments"></a></strong>
The snippets below show how to use arguments inside a script:
``` bash arguments
#!/bin/bash

echo  "number of arguments     :"  $#
echo  "programname             :"  $0
echo  "1st argument            :"  $1
echo  "2nd argument            :"  $2
echo  "all arguments           :"  $*
echo  "each argument in quotes :"  "$@"
echo  "last return value       :"  $?
```

<br><strong><a name="redirecting"></a></strong>
The snippets below show how to use redirections and piping:
``` bash file redirection and piping
#!/bin/bash

make 1> log.txt 2> error.txt    # redirect std output to log.txt and error to error.txt
make > log.txt 2> error.txt     # same as above
make >> log.txt 2>> error.txt   # same as above but appending instead overwriting
make &> log.txt                 # redirect std output and error to log.txt
make 2>&1 | tee log.txt         # redirect std error to standard output, then pipe to tee
make 2>error.txt | hexdump -C   # pipe std output but redirect error to file
hexdump -C < log.txt            # redirect std input
```

<br><strong><a name="cond"></a></strong>
Conditional expressions:
``` bash conditional expressions
#!/bin/bash

# execute 'ls' if argument 1 equals 1
test $1 -eq 1 && ls

# same as above
[ $1 -eq 1 ] && ls

# strings
s1="abcdef"
s2="xyz"
if [ "$s1" =  "$s2" ];   then echo "strings are equal";     else echo "strings are not equal"; fi
if [ "$s1" != "$s2" ];   then echo "strings are not equal"; else echo "strings are equal"; fi
if [ "$s1" \<  "$s2" ];  then echo "s1 is smaller";         else echo "s1 is not smaller"; fi
if [ "$s1" \>  "$s2" ];  then echo "s1 is bigger";          else echo "s1 is not bigger"; fi
if [ -z "$s1" ]; then echo "string has zero length"; fi
if [ -n "$s1" ]; then echo "string has not zero length"; fi

# comparing numbers
if [ x -eq y ]; then echo "equal"; fi
if [ x -ne y ]; then echo "not equal"; fi
if [ x -lt y ]; then echo "less than"; fi
if [ x -gt y ]; then echo "greater than"; fi
if [ x -le y ]; then echo "less or equal"; fi
if [ x -ge y ]; then echo "greater or equal"; fi

# expressions for testing
if [ -d $1 ]; then echo "first argument is a directory"; fi
if [ -f $1 ]; then echo "first argument is an ordinary file"; fi
if [ -e $1 ]; then echo "first argument is an existing file"; fi
if [ -r $1 ]; then echo "first argument is readable"; fi
if [ -s $1 ]; then echo "first argument is a file with more than zero bytes"; fi
if [ -w $1 ]; then echo "first argument is writable"; fi
if [ -x $1 ]; then echo "first argument is executable"; fi
if [ -n $1 ]; then echo "first argument (string) is larger than zero"; fi
if [ -z $1 ]; then echo "first argument (string) has zero length"; fi
if [ -o $1 ]; then echo "first argument (option) is active"; fi
if [ file1 -nt file2 ]; then echo "file1 is newer than file2"; fi
if [ file1 -ot file2 ]; then echo "file1 is older than file2"; fi

# conjunction: -a
if [ $x -eq 1 -a $y -lt 10 ]; then echo "true"; else echo "false"; fi

# disjunction: -o
if [ $x -eq 1 -o $y -lt 10 ]; then echo "true"; else echo "false"; fi

# not: !
if [ ! -f $1 ]; then echo "true"; else echo "false"; fi

# using grep for conditional expressions
if grep -q keyword $file
then
	echo "keyword found"
else
	echo "keyword not found"
fi

# check second argument for value 's', 'c' or 'h'
case $2 in
s) echo "SHOW IT"
   cat $1;;
c) echo "COMPILE IT"
   gcc $1;;
h) echo "HEXDUMP IT"
   hexdump -C $1;;
*) echo "DO NOTHING";;
esac
```

<br><strong><a name="loops"></a></strong>
Loops:
``` bash loops
#!/bin/bash

# for loop that lists all arguments line by line
for i in $*; do
	echo $i
done

# shortcut for the loop above
for i; do
	echo $i
done

# list all arguments with index like "argument 3: ..."
j=1
for i in $*; do
	echo "argument $j:" $i
	((j++))
done

# same behaviour as the loop above
for (( i=1; i<$#+1; i++ ))
do
	echo "argument" $i":" ${!i}
done

# while loop: loop while val is not 1 and not 2
val=0
while test $val != 1 && test $val != 2
do
	echo -n "enter val (must be 1 or 2) > "
	read val
done

# until loop: loop until val is 3
val=0
until test $val = 3
do
	echo -n "enter val (must be 3) > "
	read val
done
```

<br><strong><a name="funcs"></a></strong>
Using functions in bash:
``` bash functions
#!/bin/bash

# foo prints the sum of its numerical arguments
foo()
{
	sum=0
	for i; do sum=$[ sum + $i ]; done
	echo "The sum of $* is" $sum
}

bar()
{
	echo "This is bar. I don't use arguments."
}

foo 100 5 200
bar 100 5 200
```
