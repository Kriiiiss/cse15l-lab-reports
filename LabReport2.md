# Lab Report 2 - Servers and SSH Keys

## Part 1

```
StringServer

import java.io.IOException;
import java.net.URI;

class Handler implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.
    int num = 0;
    String old_s = "";

    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            return String.format("Start Server");
        } else {
            if (url.getPath().contains("/add-message")) {
                String[] parameters = url.getQuery().split("=");
                if (parameters[0].equals("s")) {
                    num += 1;

                    if(old_s == ""){
                        old_s = String.format("%d. %s",num, parameters[1]);
                    } else {
                        old_s = old_s +"\n"+ String.format("%d. %s",num, parameters[1]);
                    }
                    
                    return old_s;
                }
            }
            return "404 Not Found!";
        }
    }
}

class StringServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}
```

After I start the server, I type "/add-message?s=Hello" at the end of the link. 

<img width="1209" alt="Screenshot 2023-10-22 at 01 21 34" src="https://github.com/Kriiiiss/cse15l-lab-reports/assets/147010005/3d6579ca-cdef-46ca-ab9a-f0d8a378f906">

then press "Enter"

<img width="1184" alt="Screenshot 2023-10-22 at 01 22 15" src="https://github.com/Kriiiiss/cse15l-lab-reports/assets/147010005/39a6c46a-438f-4270-8f3f-ae9886fd30a4">

* Firstly, the Class "StringServer" is called to start the Server. After that, I called the method "class Handler implements URLHandler" inside the main functuion.
  then the function "public String handleRequest(URI url)" will process my request if I add /add-message to the url.

* In the main funciton, the argument is the port number which is used to start the server. The value of this argument is 4000. In the function "handleRequest", the argument is
  "URI url". The value of my url is "https://0-0-0-0-4000-j0cdi736itkddfb8tohb3b288g.us.edusercontent.com" in the Edstem. In Class "URLHandler", I use **integer num** and **String old_s**
  to record my request. If I input the request "/add-message" and the query after it, the **parameters[1]** will record the string message. The **num** is to record the number of query I
  input and **old_s** is to record my previous input and output to the screen. The value of **num** is {1} and the **old_s** is {"Hello"}.
  
* The value **num** and **old_s** changed if I request to add message to the Server. **num** will count how many times I make a request and **old_s** will record all the message. 

<img width="1096" alt="Screenshot 2023-10-22 at 01 31 42" src="https://github.com/Kriiiiss/cse15l-lab-reports/assets/147010005/b930dcf8-1147-4e50-a73c-479eda51a08b">

then press "Enter"

<img width="1112" alt="Screenshot 2023-10-22 at 01 34 01" src="https://github.com/Kriiiiss/cse15l-lab-reports/assets/147010005/dfd648cb-8082-410c-89dc-5f1efe455c00">

* This step is follow by the previous step. The function "public String handleRequest(URI url)" will process my request if I add /add-message to the url.

* The function "handleRequest" will be called as same as the previous one. The **parameters[1]** will record my input string message. **num** will increment 1 since It is my second time
  process this request, so the value of **num** this time is 2. **old_s** will record the previous input and print with **parameters[1]** to the screen. The value of **old_s** is "1. Hello"
  and the **parameters[1]** is "How are you".

* The value **num** and **old_s** will change when I "/add-messge" to the Server. 


---
## Part 2

The path to the private key for my SSH key on my Computer.

<img width="483" alt="Screenshot 2023-10-22 at 16 18 31" src="https://github.com/Kriiiiss/cse15l-lab-reports/assets/147010005/5568ef01-ab7e-4105-9da3-ea3195cbab3c">

The path to the public key for my SSH key for login ieng6 in my account.

<img width="492" alt="Screenshot 2023-10-22 at 16 22 15" src="https://github.com/Kriiiiss/cse15l-lab-reports/assets/147010005/1cfa9dab-410d-48de-9472-8a21e4bd7875">

I don't need to enter my password when I login to the server. 

<img width="811" alt="Screenshot 2023-10-22 at 16 27 30" src="https://github.com/Kriiiiss/cse15l-lab-reports/assets/147010005/46f86ffe-d700-4413-8dfa-6a4b6888a488">

---
## Part 3

In this Lab, I have learned how to connect to the ieng6 Server and login without entering password. I understand the difference between local computer, EdStem, and ieng6 Server.
I know how to start a Server and process the request in the url on each terminal. Additionally, I have learned many commands: cat, mam, scp, ssh, curl. I can use these commands to 
work in my terminal. Moreover, I understand how to write a program for a server and work with it. I can "Search" and "Add" with this server. 
