# Introduction

The main objective of this repository is to explain how to pass each level of Linux bandit challenge. 

### Level 0

The goal of this level is for you to log into the game using SSH. The host to which you need to connect is bandit.labs.overthewire.org, on port 2220. The username is bandit0 and the password is bandit0. Once logged in, go to the Level 1 page to find out how to beat Level 1.

```markdown
1. Get into the server bandit0 at port 2220 using ssh bandit0@bandit.labs.overthewire.org -p 2220
2. Insert the password: bandit0
3. Go to level 1
```
![image](https://user-images.githubusercontent.com/44106858/109784919-8708fc00-7c46-11eb-9935-030723356da4.png)


### Level 0 -> 1

The password for the next level is stored in a file called readme located in the home directory
```markdown
1. ls inside home directory
2. Read the readme file using cat command

The password is boJ9jbbUNNfktd78OOpsqOltutMc3MY1
```
![image](https://user-images.githubusercontent.com/44106858/109909734-90937200-7ce1-11eb-9a4f-f4fee9f7e02f.png)


### Level 1
The password for the next level is stored in a file called - located in the home directory. Since the filename is '-', we need to provide the current directory of the file.
```markdown
1. ls to display existing file
2. use ./ or <- to read the file

The password is : CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9
```
![image](https://user-images.githubusercontent.com/44106858/109910513-3bf0f680-7ce3-11eb-915e-1265f09c9fbe.png)

### Level 2
The password for the next level is stored in a file called spaces in this filename located in the home directory. The file name contain space. So what we can do is put backslash in front of each word. Or just simply press  TAB button.
```markdown
1. ls to display existing file
2. cat spaces\ in\ this\ filename

The password is : UmHadQclWmgdLOKQ3YNgjWxGoRMb5luK
```
![image](https://user-images.githubusercontent.com/44106858/109910815-f2ed7200-7ce3-11eb-90de-a5d12ad2aaa2.png)

### Level 3
The password for the next level is stored in a hidden file in the inhere directory. Use command ls -la to display all files inside the directory including hidden file. To read hidden file, we need to put . infront of the file name to indicate that it is a hidden file.
```markdown
1 cd into inhere
2.ls -la to display all files
3.cat .hidden

The password is:pIwrPrtPN36QITSp3EQaw936yaFoFgAB
```
![image](https://user-images.githubusercontent.com/44106858/109911364-ea496b80-7ce4-11eb-8cf0-4a35b0ad90fe.png)

### Level 4
The password for the next level is stored in the only human-readable file in the inhere directory. Human-readable file means ASCII format. So we must find the file with ASCII format to get the password. We can use find command followed by file command to check the file type.
```markdown
1.cd into inhere
2.ls to display all the files
3. find -type f to select all files inside the directory and use xargs(extended argument) to add argument which is file to check the file type
4. read the output file which is -file07

The password is : koReBOKuIDDepwhWk7jZC0RTdopnAYKh
```
![image](https://user-images.githubusercontent.com/44106858/109912411-f5050000-7ce6-11eb-90f9-c7adf3c36795.png)

### Level 5
The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:
```markdown
human-readable
1033 bytes in size
not executable
```
We can use find command to find specific file. We can use command such below to find the file.
```markdown
find -type f -size 1033c ! -executable | xargs file
```
```markdown
- f is option for file
- 1033 is the size and c is for byte
- ! -executable is non-executable file
- file is to check the format of the file
```
![image](https://user-images.githubusercontent.com/44106858/109918966-d6a50180-7cf2-11eb-87f8-5232147619d3.png)
```markdown
The password is: DXjZPULLxYr17uwoI01bNLQbtFemEgo7
```

### Level 6
The password for the next level is stored somewhere on the server and has all of the following properties:
```markdown
owned by user bandit7
owned by group bandit6
33 bytes in size
```
To find file belong to other user and group, we can use -group (group_name) and -user (user_name). We can run command like this:
```markdown
find / -type f -user bandit7 -group bandit6 -size 33c 2>/dev/null
```
```markdown
/ : find files from entire system
-f : to find file type
-user : specify user
-group : specify group
-size : specify size
c : flag for byte
2> : refer to standard error stream (stderr)
/dev/null : suppress/ throw away the input type
```
![image](https://user-images.githubusercontent.com/44106858/109920998-099cc480-7cf6-11eb-98a9-71798ec74b0e.png)
```markdown
The password is : HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs
```

### Level 7
The password for the next level is stored in the file data.txt next to the word millionth.
What we can do is we read the data.txt and grep the word millionth. grep command is used to find specific word inside a text file.
```markdown
cat data.txt | grep millionth
```
![image](https://user-images.githubusercontent.com/44106858/109922166-ed9a2280-7cf7-11eb-9657-1371e3f398f8.png)
```markdown
The password is : cvX2JJa4CFALtqS87jk27qwqGhBM9plV
```

### Level 8
The password for the next level is stored in the file data.txt and is the only line of text that occurs only once. To find text that occurs only once, we can sort them out then find unique text using uniq -u command. -u is to print only unique text.
```
sort data.txt | uniq -u
```
![image](https://user-images.githubusercontent.com/44106858/109923676-115e6800-7cfa-11eb-96c0-791863f95679.png)

```
The password is : UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR
```

### Level 9
The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters. To read human-readable strings, we can use **strings** command. Then use **grep** command to find "=" sign.
```markdown
bandit9@bandit:~$ strings data.txt | grep =
```
![image](https://user-images.githubusercontent.com/44106858/109924334-15d75080-7cfb-11eb-8173-978154d4a4c8.png)
```
The password is : truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk
```

### Level 10
The password for the next level is stored in the file data.txt, which contains base64 encoded data.
To read the text, first we need to decode it by using **base64** command. For base64 command, there is an option -d which used for decode base64 encoded data. After that, we will get the password.
```
base64 -d data.txt
```
![image](https://user-images.githubusercontent.com/44106858/109924832-dc531500-7cfb-11eb-8539-3bbda5d2c2e9.png)
```
The password is : IFukwKGsFW8MOq3IRFqrxE1hxTNEbUPR
```

### Level 11
The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions. This case is referring to ROT 13. so the basic of ROT 13 is the normal alphabetic order changed from A-Z to N-AZ-M. So we need to change the alphabetic order by using **tr** command. **tr** stands for translate. Enable us to change certain pattern. We can run command such below.
```ls

cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```
![image](https://user-images.githubusercontent.com/44106858/109926008-6d76bb80-7cfd-11eb-8636-374be11ceb83.png)
```
The password is : 5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu
```

### Level 12 
The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed. To solve this, we can use gzip, bzip2 and tar command. First, create nre directory as recommended. Then, use **xxd -r** command to convert hexdump into binary file and save it into a file. The command is such below.
```
xxd -r data.txt > file
```
command to decompress gz/bz/tar file:
```
gz : gzip -d (filename)
bz : bzip2 -d (filename)
tar : tar -xvf (filename)
```
After that, we check the file type. if the file type is gzip, then we need to rename the file with .gz extension. If bzip2, then assign as .bz and if tar type, assign with .tar. The processes are repeated untill we gain the last file which is data8.bin. After the final decompression, we get an ASCII text format. Read the file and we get the password for next level.

![image](https://user-images.githubusercontent.com/44106858/109935397-83d64480-7d08-11eb-9dad-bf3058aa216b.png)
![image](https://user-images.githubusercontent.com/44106858/109935770-d4e63880-7d08-11eb-8fbc-8561e3dc0108.png)


```
The password is : 8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL
```
