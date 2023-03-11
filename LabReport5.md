

### Bug #1: Invalid Class Name & Extra `java` Argument
While running my tester on the completely correct implementation, I was still getting errors. 

<img width="465" alt="image" src="https://user-images.githubusercontent.com/54158686/224471924-072f0074-ff2d-486c-b34e-2ae180c2c102.png">


When I checked the results.txt file, I noticed that I got this odd output.

<img width="709" alt="image" src="https://user-images.githubusercontent.com/54158686/224471323-4bdad5c1-cba9-4006-91bc-b0876065b852.png">

Originally, I thought it was about file conflicts due to "invalid class name". So I added some extra statements to make sure I got rid of old folders. However, that did not fix it.

` rm -rf student-submission 
  mkdir student-submission `
  
When that did not fix my issue, I noticed the third bullet point of "no runnable tests." So I went back to my JUnit line, and noticed I accidently was also running the    `ListExamples` file instead of just the `TestListExamples` file, so it looked like this: 
`java -cp $CPATH org.junit.runner.JUnitCore TestListExamples ListExamples >results.txt` 

Removing the `ListExamples` part fixed the code for me so it looked like this: 
`java -cp $CPATH org.junit.runner.JUnitCore TestListExamples >results.txt`
 
Then the code started working!

<img width="479" alt="image" src="https://user-images.githubusercontent.com/54158686/224471900-3ed4df27-5428-4f01-aa92-120299e28242.png">
