## Speedrunning Lab 7: Step-by-step guide and tricks to speed up the process.

### 1. Setup Delete any existing forks of the repository you have on your account

Click on settings, and then scroll down to ```Delete this repository```.

![image](https://user-images.githubusercontent.com/54158686/221384000-dbf2da59-5e21-4adc-a462-2ba4092dc6ac.png)


![image](https://user-images.githubusercontent.com/54158686/221383993-bbd35735-6e7c-4849-a09a-5eacb7c9d69a.png)

Then, type in the confirmation message that you would like to delete the repository.
![image](https://user-images.githubusercontent.com/54158686/221384019-5ebfa32a-4cc2-4a83-b22b-096e2b702120.png)


### 2. Setup Fork the repository

Go to this link: [https://github.com/ucsd-cse15l-w23/lab7](https://github.com/ucsd-cse15l-w23/lab7)

Click on "fork".

![image](https://user-images.githubusercontent.com/54158686/221384141-a9140a88-a60a-46b8-8100-1ce4f391ce13.png)

Ignore the fields for now. Click "create fork".

![image](https://user-images.githubusercontent.com/54158686/221384151-002a2744-2d70-4ef7-8d24-de24ee0fed08.png)



### 3. The real deal Start the timer!

Here is a [Stopwatch](https://www.google.com/search?q=stopwatch&rlz=1C1ONGR_enUS984US984&sxsrf=AJOqlzXCzP6dtMq20b9HdFy_0bDV8K6Dvg%3A1677364545459&ei=QY36Y8DQG9vAkPIPwIan-A4) on google for you to use. Click on "start" using your mouse.

### 4. Log into ieng6
Type "ssh" followed by your login, like this:
```ssh cs15lwi23aon@ieng6.ucsd.edu <enter>``` 

![image](https://user-images.githubusercontent.com/54158686/220795730-5a191b9a-3acf-4f62-9a2a-eccd667004f5.png)

### 5. Clone your fork of the repository from your Github account
Copy the ssh link with _CTRL-C_, **not** the https link. It should look something like: **git@github.com:WishingWell13/lab7.git**

![image](https://user-images.githubusercontent.com/54158686/220795801-b3980059-5cfc-47b8-a8e9-07a30d8e4497.png)

Type ```git clone```, and then press _CTRL-V_, then \<Enter\> 

![image](https://user-images.githubusercontent.com/54158686/220796101-372e215e-2ba1-4bc1-83f7-f47554fbe7c9.png)


### 6. Run the tests, demonstrating that they fail

From [Week 3](https://ucsd-cse15l-w23.github.io/week/week3/), copy the commands for running JUNIT tests using _CTRL-C_.

![image](https://user-images.githubusercontent.com/54158686/220796849-b7482c7f-19b0-492f-b43a-b511f556eea3.png)

Click back onto the terminal. then click _CTRL-V_. Click \<Backspace\> 12 times until `ArrayExamples` is gone, then type `TestListExamples`. Then click _\<Enter\>_.

### 7. Edit the code file to fix the failing test
  
We can see that the code never terminates. This most likely means that we are incorrectly iterating something inside a while loop. Let us fix that.

First, type ```nano Li<tab>```. This will autocomplete to ```nano ListExamples.java```
  
![image](https://user-images.githubusercontent.com/54158686/221382014-8dbe2ed0-6777-4b58-a26f-0cc4afecbe7b.png)

A screen like this will pop up.

![image](https://user-images.githubusercontent.com/54158686/221382022-55140452-1f94-41c3-80ac-245230bb98cb.png)


Use _CTRL-W_ and type ```while(index2 < list2.size())```. Click _\<Down\> \<Down\>_ then _\<Right\>_ 8 times. Click _\<Delete\>_, and then type ```2```.

In the end, the code snipped should look as follows:
  
![image](https://user-images.githubusercontent.com/54158686/221382301-1997ecbd-6982-4fea-abd3-7afaabad2fc0.png)

Use _CTRL-O \<Enter\>_ to save your changes. Then, exit the terminal with _Ctrl-X_.


### 8. Run the tests, demonstrating that they now succeed
Click the <Up> Key until you see the commands we ran in test 6. 
First run `javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java` using <Enter>.
Then run `java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore TestListExamples` using <Enter>
  
The tests succeed!
  
![image](https://user-images.githubusercontent.com/54158686/221382656-b52f05d6-8967-4de4-b60f-e2cd4082f8ef.png)


### 9. Commit and push the resulting change to your Github account (you can pick any commit message!)
Type ```git add .``` Include the period in what you type.
Then type ```git commit -m "My Commit Message"```. Feel free to replace "My Commit Message" with any other message.

![image](https://user-images.githubusercontent.com/54158686/221382744-13417612-8d7f-424d-9305-a00add97a3dd.png)
  
Finally, type ```git push origin main```. We are done, and hopefully got a quick time!

![image](https://user-images.githubusercontent.com/54158686/221382773-0bc46725-7cc1-4307-a966-5facb5922915.png)


