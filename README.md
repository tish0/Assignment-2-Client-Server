CST8277 Enterprise Application Programming
Assignment 2: Client/Server
Due Date: See Blackboard
• Due Date: see Blackboard for due date.
• Demo required in your own lab period. No Jar files are to be used for demo.
• Read the requirements carefully, if your program does not meet the requirements expect a loss of marks for the assignment, even though your program code runs without errors.
Lab Partner: Optional
• For this lab, you may work with a lab partner on the test plan portion and demonstration. (Optional)
• If demonstrating in lab, and passing in a shared test plan please place both you and your partner’s name at the top of the test plan. Each student should include this test plan document in their individual file upload.
Purpose:
In the first part of this exercise, you will compile and link a small C++ client and server to become familiar with compiling and linking outside the Java environment. Then we'll use our knowledge of Java syntax to make a small change to the C++ server, and recompile it. Because you know Java, you already know enough C++ to make some changes to a C++ program.
In the second part of this exercise we will work with client and server programs written in Java, but like the C++ programs from the first part. You'll make the same change to the Java server as you made to the C++ server, and then you'll go even further to use your knowledge of Java Multithreading to make the Java server multithreaded.
Part 1: Client/Server in C++
A. Compile and Link the given C++ code from the EchoServerAndAPI folder (see the Compiling and Linking section below). Then create a simple test plan, and begin your testing by testing the client and server running on the same computer. Use the computer name localhost and an application number (port) available on your computer (8080 or 8081 are often safe choices). Then, find a testing partner and test the programs by running the client and server on different machines (this situation should be added to your test plan if it's not there already). First run one partner's server on their machine, and connect with the other partner's client running on their machine. Then do the opposite, so that both servers have been tested with a different programmer's client running from a different machine.
B. You'll notice in Step A above that the Server as given will terminate after servicing just one client. Modify the server code so that the server can accept connections from multiple clients (only one at a time, one after the other - no multithreading needed). Recompile the Server, and test it again (be sure your test plan includes all the appropriate tests) with your testing partner, as you did in Step A.
C. Write a brief essay, in your own words, to explain the difference between preprocessing, compiling, and linking in C++. Look up the answer online and cite your sources using IEEE reference style.
Note:
• There is absolutely no need to add multithreading to the C++ program, just modify the code so that it handles more than one client sequentially.
Part 2: Multithreaded Server and Client in Java
A. Use the starter code within Eclipse, and read the code for the client and server to verify that you understand how the Java Networking code can connect two separate programs running in two different JVMs. To pass command line arguments to your Java programs, you will need to select Run As->Run Configurations... and select the Arguments tab in the resulting popup window.
B. Modify the Server to support more than one client (one after the other) as you did with the C++ Server. Test your Java Server as you did with the C++ version, and be sure your test plan includes running more than one client instance to attempt to simultaneously connect to the same server instance.
C. Use Multi-threading to make the Server support more than one client at a time. Use a separate class named ClientHandler that implements Runnable. Each instance of ClientHandler will interact with one client. Be sure there are no resource leaks in your programs - fix any resource leaks you can find. Note: Where possible use try-with-resources instead of a finally block with multiple close() statements. Also, redo the testing you performed in Part B with your modified Server.
D. In our Java network program, we are using Serialization to send objects between the client and server (Strings). If you were serializing your own class to pass it from client to server, e.g. class Sprite, why would using an explicit serialVersionUID be a good idea? You should read from the Effective Java book by Joshua Bloch to start looking for an answer, don’t forget to Cite your source using IEEE reference style.
Tip: Algonquin College Website  Current Students  Library  Beyond One Search Ebooks & Audiobooks  Safari (if on campus you access it directly, if off-campus you need your student number to log in)  Search: Effective Java Chapter 11: Serialization.
You might want to do general web searches for additional information as well.
Demonstration and Submission
Together with your partner (optional), demonstrate that you can run a server on one machine, and connect multiple clients to that server, with at least one of the clients on a different machine.
Submission Requirements
1. From Part I: screen shot of a successful compiler run of echoserver.cpp in a command line window. (Make sure your name is within the screen shot, see instructions below).
2. From Part I: your C++ server source file (echoserver.cpp).
3. From Part I: your essay on C++ preprocessor, compiler, linker
4. From Part II: your Java Project folder
5. From Part I and II: the simple test plan, and your essay on serialVersionUID.
Grading (10 points total)
Code C++ (4 points)
• Modified to handle multiple clients, in sequence (1 out of 4)
• Essay on C++ preprocessor, compiler, linker, with IEEE reference style to cite sources (1 out of 4)
• Screen shot, with your name, date, time within it of compiling EchoServer.cpp (1 out of 4)
• Test Plan (1 out of 4)
Code Java (5 Points)
• Server modified to handle multiple clients, in parallel, using multithreading (1 out of 5)
• Comment block at top of file(s), all classes, class-members have Javadoc comments (1 out of 5)
• Client and Server modified to not have resource leaks (1 out of 5)
• Short explanation of serialVersionUID and why use it (1 out of 5)
• Test Plan (1 out of 5)
Demo (2 Points)
• Demo in Lab of C++ and Java Programs (1 point each) Note: No Jar files allowed for demo.
C++ Compiling and Linking Instructions
Important:
• Visual Studio 2015 Community Edition does not install C++ support by default.
• If installing VS2015 for the first time, see these instructions
(You only need the ‘Common Tools for Visual C++ 2015’)
https://blogs.msdn.microsoft.com/vcblog/2015/07/24/setup-changes-in-visual-studio-2015-affecting-c-developers/
• If you have already installed VS2015 but did not add C++ support then open the control panel, select Programs and Features, and double click the Visual Studio setup program to run it again. Use the modify button and select to install the Common Tools for Visual C++ 2015.
Microsoft Windows
To compile the C++ api library, the client, and the server on MS Windows, we will use MS Visual Studio. You may use the full Visual Studio graphical IDE if you wish, but instructions for using the full graphical environment of Visual Studio are not provided here (they would involve many screenshots that might be out of date compared to the Visual Studio version you have). For this simple little C++ project, it's easier to use the Command Line.
First, invoke a development Command Line. In Windows 7, you can find this under Start->Microsoft Visual Studio 2012->Visual Studio Tools->Developer Command Prompt for VS2012 (adjust as necessary for other versions of Visual Studio).
In this Command Window, change to the API directory:
cd EchoServerAndAPI\api
Use the C++ compiler command (cl) to compile all of the C++ files there, using the following command line:
cl /c /DWIN32 *.cpp
We used the /c switch to tell the cl command that it should just create the object files and not try to make executable programs out of these files. If you have never heard of an "object file" you probably owe it to yourself to do a quick google for "object file" and find out what it is. We also used the /DWIN32 switch to define the WIN32 symbol during preprocessing so that anywhere in our C++ files where there is section of C++ code that has both LINUX and WIN32 versions of that piece of code, the WIN32 version of that piece of code is used.
Now, create a library out of those compiled files (*.obj) called api.lib using the following command line:
lib /out:api.lib *.obj
You now have the api.lib library, and you will not need to recompile it again as long as you don't change any of the C++ files in the API directory (and you're not expected to change those files!) This api.lib is a static library. In the past you may have encountered dynamic libraries, which have the .dll extension. You're now doing the same kinds of operations that are done to create Microsoft Windows itself (or Linux, or OSX, etc). Is that cool, or what?
Now change to the APPS directory:
cd ..\apps
Compile the echoclient.cpp file:
cl /c /DWIN32 echoclient.cpp
Compile the readln.cpp file:
cl /c /DWIN32 readln.cpp
Note: Use the following command before the next step: prompt Student Name $D $T $G ($D for date, $T for time, $G for greater-than, See: http://ss64.com/nt/prompt.html)
Use your own name instead of “Student Name” for example:
Compile the echoserver.cpp file
cl /c /DWIN32 echoserver.cpp
Note: Take a screen shot of compiling echoserver.cpp in the command window, which will now also document the date and time. Include this screenshot in your assignment submission.
(You can use prompt $P$G to turn the prompt back it’s default, or just re-open the terminal)
Now we will create the echoserver.exe program. We do this by linking the echoserver object module, echoserver.obj, with the api.lib library we created and the Microsoft Windows ws2_32.lib library, provided by Microsoft Windows itself, to create the echoserver.exe program. Libraries contain common functions that are used by many other different programs that need those functions. To link, we use the link command:
link /out:echoserver.exe echoserver.obj ..\api\api.lib ws2_32.lib
Now we link the echoclient program, which is split into two C++ files echoclient.cpp and readln.cpp. The linking creates the echoclient.exe program:
link /out:echoclient.exe echoclient.obj readln.obj ..\api\api.lib ws2_32.lib
You're finished building the programs. To run them as intended, you need to run the server first, having it listen to port 8080 for example (from the folder where echoserver.exe resides):
echoserver 8080
Run the clients, telling them which machine the server is running on, and which port to connect to (from the folder where echoclient.exe resides):
echoclient localhost 8080
or
echoclient 10.50.225.13 8080
etc...
Linux and Mac
The LINUX version of the code works for both Linux and Mac, and the basic process is the same as for Windows, but the commands have different names.
Modify Terminal Prompt Use: PS1="Student Name \d \t>"
Change Student Name to your actual name
Take a screen shot and pass this in as part of your assignment submission.
E.g. Unix
E.g. Mac
(when you re-open the terminal the default prompt will come back)
Compiling and Linking Instructions
cd EchoServerAndAPI/api
for f in *.cpp ; do gcc -DLINUX -c $f; echo $f done; done
ar -q libapi.a *.o
cd ../apps
g++ -DLINUX -o echoclient echoclient.cpp readln.cpp -L../api -lapi
g++ -DLINUX -o echoserver echoserver.cpp -L../api -lapi
Appendix Expected Format for Test Plan (Updated for Assignment 2)
Description
Pre-Conditions
Post-Conditions
Expected
Actual
Test Methodology
Notes
First Client can connect to server
Server is already running on port 8081
First Client connects to server
Client connects, sends “hello”, gets echo response of “hello” with additional information from server.
Matches
Run client and server enter hello and view response
Test boundary conditions:
Can the C++ server handle more than one C++ client, sequentially? Can the Multithreaded Java Server handle more than one client simultaneously? (Are there new threads created, one for each connecting client?) Etc.
Test Methodology can include “view output”, “use debugger”, use JVisualVM, JUnit test, Etc.
