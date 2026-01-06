# OvertheWire\_Bandit

**OverTheWire: Bandit** is a widely acclaimed wargame designed as an entry-level introduction to the fundamentals of Linux security and command-line mastery. By guiding users through a series of increasingly difficult levels, the game teaches essential skills such as navigating the filesystem, manipulating data, and understanding network protocols. Its importance lies in its hands-on, practical approach to learning; rather than simply reading theory, players must apply critical thinking and real-world tools to solve problems. For anyone pursuing a career in the **broad IT landscape**, Bandit serves as a vital foundation, cultivating the technical fluency and analytical problem-solving skills required to navigate and manage modern computing environments.You can begin your journey at the OverTheWire Bandit homepage.

### Level 0

<figure><img src=".gitbook/assets/image (18).png" alt="" width="563"><figcaption></figcaption></figure>

Level 0--->1.

The password for the next level is stored in a file called **readme** located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game.

### Level 1 ---->2

<figure><img src=".gitbook/assets/image (19).png" alt=""><figcaption></figcaption></figure>

### Level 2---->3

The password for the next level is stored in a file called `--spaces in this filename--` located in the home directory

pswwd:MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx

<figure><img src=".gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>

### Level 3--->4

The password for the next level is stored in a hidden file in the inhere directory

<figure><img src=".gitbook/assets/image (21).png" alt=""><figcaption></figcaption></figure>

### Level 4--->5

The password for the next level is stored in the only human-readable file in the **inhere** directory. Tip: if your terminal is messed up, try the “reset” command.

<figure><img src=".gitbook/assets/image (22).png" alt=""><figcaption></figcaption></figure>

### Level 5--->6

The password for the next level is stored in a file somewhere under the **inhere** directory and has all of the following properties:

* human-readable
* 1033 bytes in size
* not executable

<figure><img src=".gitbook/assets/image (23).png" alt=""><figcaption></figcaption></figure>

```
pswd: HWasnxxxxxxxxxxxxxxxxxxxxxxxxxy20cvUa6EG
```

This command means:

* `find .` → search everything under here
* `-type f` → files only
* `-size 1033c` → exactly 1033 bytes
* `! -executable` → not executable
* `file {}` → check file type
* `grep ASCII` → human-readable

### Level 6--->7

The password for the next level is stored somewhere on the server and has all of the following properties:

owned by user bandit7\
owned by group bandit6\
33 bytes in size

```
pswd:morbNTxxxxxxxxxxxxxxxxxxdMaLnOlFVAaj
```

<figure><img src=".gitbook/assets/image (24).png" alt=""><figcaption></figcaption></figure>

| Part             | Meaning                       |
| ---------------- | ----------------------------- |
| `find /`         | Search the entire filesystem  |
| `-type f`        | Files only                    |
| `-user bandit7`  | Owned by user bandit7         |
| `-group bandit6` | Owned by group bandit6        |
| `-size 33c`      | Exactly 33 bytes              |
| `2>/dev/null`    | Hide permission denied errors |

### Level 7--->8

The password for the next level is stored in the file **data.txt** next to the word **millionth**

```
pswd:dfwxxxxxxxxxxxxxxxxxxxxxxxxxxLg7eEc
```

<figure><img src=".gitbook/assets/image (25).png" alt=""><figcaption></figcaption></figure>

### Level 8--->9

The password for the next level is stored in the file **data.txt** and is the only line of text that occurs only once

```
pswd: 4CKxxxxxxxxxxxxxxxxxxxxx0JM
```



<figure><img src=".gitbook/assets/image (26).png" alt=""><figcaption></figcaption></figure>

### Level 9--->10

The password for the next level is stored in the file **data.txt** in one of the few human-readable strings, preceded by several ‘=’ characters.

```
pswd:FGUW5xxxxxxxxxxxxxxxxxpfMiqey
```

<figure><img src=".gitbook/assets/image (27).png" alt=""><figcaption></figcaption></figure>

### Level 10--->11

The password for the next level is stored in the file **data.txt**, which contains base64 encoded data

```
pswd: dtR173fZKbxxxxxxxxxxxxxxnpNVj3qRr
```

<figure><img src=".gitbook/assets/image (28).png" alt=""><figcaption></figcaption></figure>

### Level 11--->12

The password for the next level is stored in the file **data.txt**, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions

```
pswd: 7x16WxxxxxxxxxxxxTyj9Q4
```

<figure><img src=".gitbook/assets/image (29).png" alt=""><figcaption></figcaption></figure>

`tr 'A-Za-z' 'N-ZA-Mn-za-m'` decodes text scrambled with ROT13, a simple letter shift where each letter is replaced by the one 13 positions later in the alphabet. Uppercase and lowercase letters are shifted; numbers, symbols, and spaces stay the same. Running it on a file reveals hidden messages or passwords, and running it twice restores the original text.

### Level 12--->13

The password for the next level is stored in the file **data.txt**, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work. Use mkdir with a hard to guess directory name. Or better, use the command “mktemp -d”. Then copy the datafile using cp, and rename it using mv (read the manpages!)

```
pswd: FO5dwFsc0cbaIiH0h8J2exxxxxxxDwAn
```

<figure><img src=".gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

<figure><img src=".gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>



<figure><img src=".gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

<figure><img src=".gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

After creating a temporary directory, identify the file type to begin the decompression process. You will need to decompress the data step-by-step; while this process is repetitive, it provides excellent practice for handling various archive formats. Below is a summary of the commands you will use.

&#x20;Repeat the ProcessNow you have a new file (likely `data`) as shown the images above . You must run `file` on it again. You will encounter several compression formats. Use these commands as needed:

* **If it's Bzip2:**\
  `bzip2 -d filename` (or rename to `.bz2` first)
* **If it's Tar:**\
  `tar -xf filename`
* **If it's Gzip again:**\
  `mv filename filename.gz` then `gunzip filename.gz`





### Level 13--->14

The password for the next level is stored in /etc/bandit\_pass/bandit14 and can only be read by user bandit14. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level. Look at the commands that logged you into previous bandit levels, and find out how to use the key for this level.

You can dwonload the key by running the command and the file will be saved to your host machine. If that dosent work you can manually copy and paste the encoded key to your host machine.

```
scp -P 2220 bandit13@bandit.labs.overthewire.org:~/sshkey.private .
```

* **`scp`**: The **S**ecure **C**opy **P**rotocol command. It is used to transfer files between hosts on a network using SSH for data transfer and authentication.
* **`~/sshkey.private`**: The specific **path and name of the file** you want to copy.
  * The tilde (`~`) is a shortcut for the user's **home directory**.
  * **`.` (the dot)**: The **destination** on your local machine. A single dot represents your **current working directory** (wherever your terminal is currently "located").&#x20;

The image below shows the output.

<figure><img src=".gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

Set the Correct PermissionsSSH will refuse to use a private key if the file permissions are "too open" (i.e., other users on your computer can read it). You must restrict access to only yourself: bash

```
chmod 600 sshkey.private
```

<figure><img src=".gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

The output above shows that the file permissions for the private key are incorrect. For security reasons, it is highly recommended that you are the only one with permission to read and write to this file.

After logging in, you can go to /etc/bandit\_pass/bandit14  to check for the password&#x20;

<figure><img src=".gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

```
pswd: MU4VWexxxxxxxxxxxxxxxxxxxh7lDCPvS
```

### Level 14--->15

The password for the next level can be retrieved by submitting the password of the current level to **port 30000 on localhost**.

```
pswd: 8xCjnmxxxxxxxxxxxxx4M2tKJQo
```

<figure><img src=".gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

{% include ".gitbook/includes/untitled.md" %}

### Level 15--->16

The password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL/TLS encryption.

Helpful note: Getting “DONE”, “RENEGOTIATING” or “KEYUPDATE”? Read the “CONNECTED COMMANDS” section in the manpage.

Run the command below and enter your current password to retrieve the credentials for the next level

```
openssl s_client -connect localhost:30001
```

<figure><img src=".gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

```
pswd : kSkvxxxxxxxxRy0Dx
```



### Level 16--->17

The credentials for the next level can be retrieved by submitting the password of the current level to **a port on localhost in the range 31000 to 32000**. First find out which of these ports have a server listening on them. Then find out which of those speak SSL/TLS and which don’t. There is only 1 server that will give the next credentials, the others will simply send back to you whatever you send to it.

\
We will start by scanning for the ports using nmap using the following command&#x20;

```
nmap -sV localhost -p 31000-32000
```

When you run a standard scan, Nmap only tells you if a port is "open" and guesses the service based on the port number . Using `-sV` makes Nmap more active: it communicates with the open ports to determine exactly what service is running and what **version number** it is using.

<figure><img src=".gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

What to Ignore

* **Port 31046, 31691, 31960 (echo):** These are plain text services. Since the next level (17) requires an SSL connection, these will not work.
* **Port 31518 (ssl/echo):** Although this uses SSL, the service is labeled "echo." This means if you send it your password, it will simply repeat the password back to you instead of giving you the key.

What to Check (The Target)

*   **Port 31790 (ssl/unknown):** This is your primary target.

    * **Why?** It is using SSL, but Nmap cannot identify the specific service ("unknown"). In the Bandit labs, this usually indicates the service that is waiting for your password to provide the RSA private key for the next level.



```
openssl s_client -connect localhost:31790
```

After struggling to get the key my login key starts with "k" which keeps giving me KEY UPDATE back after doing some digging. Founf out that If your Bandit password starts with the letter k, OpenSSL mistakenly interprets the first character of your password as a command to update the keys instead of sending the character to the server. This was the output&#x20;

<p align="center"><img src=".gitbook/assets/image (11).png" alt=""> </p>

Fixed the issue with flag -quiet .&#x20;

```
openssl s_client -connect localhost:31790 -quiet
```

<figure><img src=".gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>

The result is a private SSH key. So, we create a file  put the key into and like in Level 14, we need to make sure that the file only has permissions for the user.





### Level17 --->18

There are 2 files in the homedirectory: passwords.old and passwords.new. The password for the next level is in passwords.new and is the only line that has been changed between passwords.old and passwords.new

NOTE: if you have solved this level and see ‘Byebye!’ when trying to log into bandit18, this is related to the next level, bandit19

<figure><img src=".gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>

```
pswd: x2gLTTjFwMOxxxxxxxxxxxxxKxfRqGlO
```

How to read this output:

* **`42c42`**: This means line **42** in the first file was **c**hanged to match line **42** in the second file.
* **`< x2gLTT...`**: The line starting with `<` belongs to the **first** file you listed (`passwords.new`).
* **`---`**: This is just a separator between the two files.
* **`> pGozC8...`**: The line starting with `>` belongs to the **second** file you listed (`passwords.old`).

### Level18--->19

There are 2 files in the homedirectory: passwords.old and passwords.new. The password for the next level is in passwords.new and is the only line that has been changed between passwords.old and passwords.new

NOTE: if you have solved this level and see ‘Byebye!’ when trying to log into bandit18, this is related to the next level, bandit19



While trying to login into level 18 you get kicked to out.As shown below&#x20;

<figure><img src=".gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>

* **The Problem:** The `.bashrc` file (a script that runs every time you log in) contains an `exit` or `logout` command.
* **The Fix:** SSH allows you to send commands directly or override the default login shell, which prevents that logout script from running.&#x20;

```
ssh bandit18@bandit.labs.overthewire.org -p 2220 cat readm
```

Executing the command above allows you to read the **readme** file. The password will be displayed once you provide your login credentials at the prompt.

```
pswd:cGWpMaKXxxxxxxxxx
```

### Level19 --->20

To gain access to the next level, you should use the setuid binary in the homedirectory. Execute it without arguments to find out how to use it. The password for this level can be found in the usual place (/etc/bandit\_pass), after you have used the setuid binary.

<figure><img src=".gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>

Since the binary lets you run commands as `bandit20`, you can use it to read the password file for the next level, which is normally restricted to you

<figure><img src=".gitbook/assets/image (17).png" alt=""><figcaption></figcaption></figure>

```
pswd: 0qXahxxxxxxxxxxxx
```
