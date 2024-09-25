1. 
```
```avahi
bin
colord
cups
daemon
dbus
dhcpcd
dnsmasq
flatpak
ftp
fwupd
gdm
geoclue
git
gnome-remote-desktop
http
ilya
mail
nm-openconnect
nm-openvpn
nobody
nvidia-persistenced
openvpn
passim
polkitd
rabbitmq
root
rpc
rpcuser
rtkit
saned
systemd-coredump
systemd-journal-remote
systemd-journal-upload
systemd-network
systemd-oom
systemd-resolve
systemd-timesync
_talkd
transmission
tss
usbmux
uuidd```
```
\-`grep -o '^[^:]*' passwd | sort `


2.
```
255 reserved
145 nsh
144 aggfrag
143 ethernet
142 rohc

```
\-cat protocols | awk '{print $2, $1}' | sort -nr | head -n 5 

3.
```

+-----------------------+
| Hello from RTU MIREA! |
+-----------------------+

#!/bin/bash
message="Hello from RTU MIREA!"
msg_length=${#message}
top_bottom_border="+$(printf '%*s' $((msg_length + 2)) | tr ' ' '-')+"
echo "$top_bottom_border"
echo "| $message |"
echo "$top_bottom_border"
```

4.

```
balance
bool
ch
char
choice
choice2
cin
const
cout
digit
do
else
expression
false
for
getline
if
ignore
include
index
int
iostream
isBalancedBrackets
isBalancedBracketsIter
isBalancedBracketsRecursive
isDivisibleByDigits
isDivisibleByDigitsRec
length
main
n
number
originalNumber
return
std
string
true
while

grep -vE '^\s*//|/\*|\*/' main.cpp | grep -o -E '\b[a-zA-Z_][a-zA-Z0-9_]*\b' | sort -u
```

5.
```
#!/bin/bash
if [ -z "$1" ]; then
  echo "Usage: $0 <program>"
  exit 1
fi

PROGRAM=$1

if [ ! -f "$PROGRAM" ]; then
  echo "Error: $PROGRAM not found in the current directory."
  exit 1
fi

sudo cp "$PROGRAM" /usr/local/bin/
sudo chmod 755 /usr/local/bin/"$PROGRAM"

echo "$PROGRAM has been successfully copied"

---

Input:
touch 11; ./reg 11

Output:
11 has been successfully copied
```

6.
```
#!/bin/bash
for file in *.{c,js,py}; do
  if [[ -f "$file" ]]; then
    first_line=$(head -n 1 "$file")
    if [[ "$first_line" =~ ^[[:space:]]*//|^[[:space:]]*# ]]; then
      echo "There are comms in first str in $file."
    else
      echo "There are no comms in first str in $file ."
    fi
  fi
done

---

Input: 

./1_6 main.py

Output:

There are no comms in first str in $file .

```

7.

```
#!/bin/bash

find "$1" -type f -exec md5sum {} + | sort | uniq -w32 -dD

---

Input:

./1_7 /bin

Output:

<empty>

```

8.
```
#!/bin/bash
if [ -z "$1" ]; then
  echo "Usage: $0 <exp>"
  exit 1
fi

files=$(find . -name "*.$1")

tar -cvf archive.tar $files
echo "All files with .$1 archived in archive.tar"

---

Input:
./1_9 

Output:

```

9.

```
#!/bin/bash

if [ $# -ne 2 ]; then
  echo "Usage: $0 <imput file> <output file>"
  exit 1
fi

sed 's/    /\t/g' "$1" > "$2"
echo "replaced in $2"

---

Input:

nvim testt                                               ✔ 
touch testt_1                                    ✔  14s  
./1_8 testt testt_1                                      ✔ 
replaced in testt_1


Output:

replaced in testt_1
```

10.

```
#!/bin/bash

if [ -z "$1" ]; then
  echo "Usage: $0 <directory>"
  exit 1
fi
find "$1" -type f -empty -name "*.txt" -print


---

Input:

touch 111.txt                                             ✔ 
touch 112.txt                                             ✔ 
touch 113.txt                                             ✔ 
nvim 113.txt                                              ✔ 
./1_10 ~/confupr                                   ✔  6s  

Output:

/home/ilya/confupr/112.txt
/home/ilya/confupr/111.txt

```
