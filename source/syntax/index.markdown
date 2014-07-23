---
layout: page
#title: "Hall Of Syntax"
comments: true
sharing: true
footer: true
sidebar: false
---
<p>It's the place where I write down useful syntax snippets.</p>

<p style="margin-top:0.5em; margin-bottom:0.3em">
<strong>Overview</strong></p>
<ul>
<li><a href="#bash">Bash expressions</a></li>
<li><a href="#matlab">Matlab: Manually plot lines</a></li>
<li><a href="#osxHiddenFiles">OS X: Toggle visibility of hidden files in Finder</a></li>
</ul>

<strong><a name="bash">BASH (UNIX System V.4)</a></strong>
```
$#    number of arguments
$-    current option
$?    last return value
$0    programname
$1    1st argument
$2    2nd argument
$*    all arguments
"$@"  all arguments in ""

-d file   is a directory
-f file   is a file
-r file   is readable
-s file   is a file with more than zero bytes
-w file   is writable
-x file   is executable
file1 -nt file2   file1 is newer than file2
file1 -ot file2   file1 is older than file2

-n string  string is larger than zero
-o option  the option is active
-z string  string has zero length

s1 = s2    strings equal
s1 != s2   they don't equal
s1 < s2    s1 is smaller
s1 > s2    s1 is bigger

x -eq y    equal
x -ne y    not equal
x -lt y    less than
x -gt y    greater than
x -le y    less or equal
x -ge y    greater or equal

(expr)
!expr
expr1 && expr2
expr1 || expr2

case $2 in
p) echo "PRINT IT"
   cat $1;;
c) echo "COMPILE IT"
   gcc $1;;
x) echo "HEXDUMP IT"
   hd $1;;
esac

while test $Wahl != a && test $Wahl != b
do
 echo "Auswahl: a oder b"
 read Wahl
done

until test $Wahl = c
do
  read Wahl
done
```


<strong><a name="matlab">Matlab</a></strong>
``` c hello world
% scatter(k1x,k1y,50,'blue','filled')
% scatter(k2x,k2y,50,'green','filled')
% scatter(k3x,k3y,50,'red','filled')
% scatter(k4x,k4y,50,'yellow','filled')
% scatter(k5x,k5y,50,'black','filled')
% scatter(k6x,k6y,50,'magenta','filled')

plot([0 0], [-5 20], 'k-');hold
plot([-5 20], [0 0], 'k-')

plot([k1x(a) k1x(b)], [k1y(a) k1y(b)], 'b-')
plot([k1x(a) k1x(c)], [k1y(a) k1y(c)], 'b-')
plot([k1x(a) k1x(d)], [k1y(a) k1y(d)], 'b-')
plot([k1x(b) k1x(e)], [k1y(b) k1y(e)], 'b-')
plot([k1x(b) k1x(f)], [k1y(b) k1y(f)], 'b-')
plot([k1x(c) k1x(e)], [k1y(c) k1y(e)], 'b-')
plot([k1x(c) k1x(d)], [k1y(c) k1y(d)], 'b-')
plot([k1x(f) k1x(e)], [k1y(f) k1y(e)], 'b-')
plot([k1x(f) k1x(d)], [k1y(f) k1y(d)], 'b-')

plot([k2x(a) k2x(b)], [k2y(a) k2y(b)], 'g-')
plot([k2x(a) k2x(c)], [k2y(a) k2y(c)], 'g-')
plot([k2x(a) k2x(d)], [k2y(a) k2y(d)], 'g-')
plot([k2x(b) k2x(e)], [k2y(b) k2y(e)], 'g-')
plot([k2x(b) k2x(f)], [k2y(b) k2y(f)], 'g-')
plot([k2x(c) k2x(e)], [k2y(c) k2y(e)], 'g-')
plot([k2x(c) k2x(d)], [k2y(c) k2y(d)], 'g-')
plot([k2x(f) k2x(e)], [k2y(f) k2y(e)], 'g-')
plot([k2x(f) k2x(d)], [k2y(f) k2y(d)], 'g-')

plot([k3x(a) k3x(b)], [k3y(a) k3y(b)], 'r-')
plot([k3x(a) k3x(c)], [k3y(a) k3y(c)], 'r-')
plot([k3x(a) k3x(d)], [k3y(a) k3y(d)], 'r-')
plot([k3x(b) k3x(e)], [k3y(b) k3y(e)], 'r-')
plot([k3x(b) k3x(f)], [k3y(b) k3y(f)], 'r-')
plot([k3x(c) k3x(e)], [k3y(c) k3y(e)], 'r-')
plot([k3x(c) k3x(d)], [k3y(c) k3y(d)], 'r-')
plot([k3x(f) k3x(e)], [k3y(f) k3y(e)], 'r-')
plot([k3x(f) k3x(d)], [k3y(f) k3y(d)], 'r-')

plot([k4x(a) k4x(b)], [k4y(a) k4y(b)], 'y-')
plot([k4x(a) k4x(c)], [k4y(a) k4y(c)], 'y-')
plot([k4x(a) k4x(d)], [k4y(a) k4y(d)], 'y-')
plot([k4x(b) k4x(e)], [k4y(b) k4y(e)], 'y-')
plot([k4x(b) k4x(f)], [k4y(b) k4y(f)], 'y-')
plot([k4x(c) k4x(e)], [k4y(c) k4y(e)], 'y-')
plot([k4x(c) k4x(d)], [k4y(c) k4y(d)], 'y-')
plot([k4x(f) k4x(e)], [k4y(f) k4y(e)], 'y-')
plot([k4x(f) k4x(d)], [k4y(f) k4y(d)], 'y-')

plot([k5x(a) k5x(b)], [k5y(a) k5y(b)], 'k-')
plot([k5x(a) k5x(c)], [k5y(a) k5y(c)], 'k-')
plot([k5x(a) k5x(d)], [k5y(a) k5y(d)], 'k-')
plot([k5x(b) k5x(e)], [k5y(b) k5y(e)], 'k-')
plot([k5x(b) k5x(f)], [k5y(b) k5y(f)], 'k-')
plot([k5x(c) k5x(e)], [k5y(c) k5y(e)], 'k-')
plot([k5x(c) k5x(d)], [k5y(c) k5y(d)], 'k-')
plot([k5x(f) k5x(e)], [k5y(f) k5y(e)], 'k-')
plot([k5x(f) k5x(d)], [k5y(f) k5y(d)], 'k-')

plot([k6x(a) k6x(b)], [k6y(a) k6y(b)], 'm-')
plot([k6x(a) k6x(c)], [k6y(a) k6y(c)], 'm-')
plot([k6x(a) k6x(d)], [k6y(a) k6y(d)], 'm-')
plot([k6x(b) k6x(e)], [k6y(b) k6y(e)], 'm-')
plot([k6x(b) k6x(f)], [k6y(b) k6y(f)], 'm-')
plot([k6x(c) k6x(e)], [k6y(c) k6y(e)], 'm-')
plot([k6x(c) k6x(d)], [k6y(c) k6y(d)], 'm-')
plot([k6x(f) k6x(e)], [k6y(f) k6y(e)], 'm-')
plot([k6x(f) k6x(d)], [k6y(f) k6y(d)], 'm-')
```

<strong><a name="osxHiddenFiles">OS X: Toggle visibility of hidden files in Finder</a></strong>
``` bash hello world
if [ "$1" == "ON" ];then
echo "Setting Finder to show hidden files"
defaults write com.apple.finder AppleShowAllFiles TRUE;killall Finder
else
	if [ "$1" == "OFF" ];then
	echo "Setting Finder to NOT show hidden files"
	defaults write com.apple.finder AppleShowAllFiles FALSE;killall Finder
	else
		echo "Give me parameter ON or OFF"
	fi
fi
```
