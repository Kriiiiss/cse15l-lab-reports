# Lab Report 1 - Remote Access and FileSystem (Week 1)

## Command "cd"
* Share an example of using the command with no arguments.

   There is no output when command was run, it changes the directory.

   <img width="452" alt="cd1" src="https://github.com/Kriiiiss/cse15l-lab-reports/assets/147010005/9a816db4-cff0-4b5f-ac5c-b9e648c8c93b">
   
   When the current working directory is "/home" and then use command "cd", it doesn't change and still in directory "/home".
   
   <img width="406" alt="cd2" src="https://github.com/Kriiiiss/cse15l-lab-reports/assets/147010005/9006f6a2-b6fc-4017-8f61-67271ce4f8ad">

   When the current working directory is "/home/lecture1" and then use command "cd", it changes the directory to "/home".
   
   **cd** means “Change Directory”. It is used to switch the current working directory to the given path. In general, if there's no argument in this command, it means change working directory to the "/home".

   **No Error**
   
---
* Share an exmaple of using the command with a path to a directory as an argument.

   There is no output when command was run, it changes the directory.

   <img width="337" alt="cd3" src="https://github.com/Kriiiiss/cse15l-lab-reports/assets/147010005/41e14772-f993-4e37-bf77-0a15de78c441">

   When the current working directory is "/home" and then use command with a path to a directory "cd lecture1", it changes the directory to "/home/lecture1"
   
   **cd** means “Change Directory”. It is used to switch the current working directory to the given path. I use the command "cd lecture1" so I change the current directory "/home" to the path "/home/lecture1"

   **No Error**
   
---   
* Share an example of using the command with a path to a file as an argument.

   There is no output when command was run, it doesn't change the directory.

   <img width="507" alt="Screenshot 2023-10-07 at 16 05 54" src="https://github.com/Kriiiiss/cse15l-lab-reports/assets/147010005/a69aad63-ccd4-41cd-950f-fc5efaea8fa8">

   The current working directory is "home". 

   **cd** a command with a path to a file "cd /home/lecture1/Hello.java, it doesn't change the directory and shows error.

   **Error:** It is only used for Change Directory. It cannot be used to change to a file.


---
## Command "ls"
* Share an example of using the command with no arguments.

   <img width="309" alt="ls1" src="https://github.com/Kriiiiss/cse15l-lab-reports/assets/147010005/8ba83787-c0a3-4165-9460-3991acf2a76b">

   The current working directory is "/home".

   **ls** means “List”. It used to list the files and folders the given path. If there's no argument in this command, it shows the list for current directory. In my computer, it shows the folder "lecture1" and a file "URIMain.class".

   **No Error**

---
* Share an exmaple of using the command with a path to a directory as an argument.

   <img width="397" alt="ls2" src="https://github.com/Kriiiiss/cse15l-lab-reports/assets/147010005/88cfe63b-440c-4bb4-ba43-7e044da5e12f">

   The current working directory is "/home".

   **ls** means “List”. It used to list the files and folders the given path. When I use command "ls lecture1" it will shows all files and folders inside the folder "lecture1".

   **No Error**

---
* Share an example of using the command with a path to a file as an argument.

   <img width="445" alt="ls3" src="https://github.com/Kriiiiss/cse15l-lab-reports/assets/147010005/13a6fc0b-b3d8-4844-b643-874d4e63d5c0">

   The current working directory is "/home".

   **ls** means “List”. It used to list the files and folders the given path. When I use the command with a path to a file, it will output the path of the file. 

   **Error:** it doesn't show the list of files and folders since file is the smallest unit and there is no folder and file inside another file.


---
## Command "cat"
* Share an example of using the command with no arguments.
   
   <img width="234" alt="cat1" src="https://github.com/Kriiiiss/cse15l-lab-reports/assets/147010005/bf455a4d-6dae-4cf0-a03e-b7b3045e8d0d">

   The current working directory is "/home".

   **cat** means “Concatenate”. It used to print the contents of one or more files given by the paths. If there's no argument in this command, it doesn't have any output and it waits for an input from keyboard. I don't think it is an error because it requires additional instructions to complete.

   **No Error**

---
* Share an exmaple of using the command with a path to a directory as an argument.

   <img width="298" alt="cat2" src="https://github.com/Kriiiiss/cse15l-lab-reports/assets/147010005/eea1a630-9fd2-4656-9101-15aa09ad0d9a">

   The current working directory is "/home".

   **cat** is used to print the contents of one or more files given by the paths. When we use command with a path to a directory "cat lecture1", it will output that lecture1 is a Directory and it cannot print any content.

   **Error:** it is not a file and cat is only for showing the content of the file, so it cannot be used for a directory.
   
---
* Share an example of using the command with a path to a file as an argument.

   <img width="465" alt="cat3" src="https://github.com/Kriiiiss/cse15l-lab-reports/assets/147010005/52da1139-1d68-4379-a278-5ffd6ad71125">

   <img width="700" alt="cat4" src="https://github.com/Kriiiiss/cse15l-lab-reports/assets/147010005/398aefca-4267-4ab8-a36e-b1ce2f881e58">

   The current working directory is "/home".

   **cat** means “Concatenate”. It used to print the contents of one or more files given by the paths. When I use the command with a path to a file "cat lecture1/messages/en-us.txt", it will print the content inside the file "en-us.txt". If I use two argument with 2 path to a file "cat lecture1/messages/en-us.txt lecture1/messages/es-mx.txt", it will print two file sequently.

   **No Error**
   

   



   
