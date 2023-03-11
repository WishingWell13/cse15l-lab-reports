# CSE 15L Lab Report 5: All About Lab 6 - The Grading Script
In lab 6, we created a testing script that takes a student-submitted ListExamples file and tests its implementation against our tester file using a bash script. I thought this was super interesting since I always wondered about how the grading was automated in CSE classes. In this report, I'll take you through my implementation of the script, some examples of it working, and some bugs I encountered along the way.

## Code Walkthrough

## Examples of Script Working
### Fully correct implementation
As shown below, we simply display that the user has scored 100% on the test cases!

<img width="470" alt="image" src="https://user-images.githubusercontent.com/54158686/224472399-22676a28-1c63-4195-b2c7-92667280af0e.png">

### Partially correct implementation


## Bugs
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

### Bug #2: if statement not working
This bug was a syntax error instead of a logic error! I learned that when writing `if [[ -f "ListExamples.java" ]]`, we could not have no spaces between the conidtional and the brackets (so we couldn't do `if [[-f "ListExamples.java"]]`. Why is this? I searched it up, and it turns out that the brackets are shorthand for writing the command `test`, as described [in this StackOverflow post!](https://stackoverflow.com/questions/9581064/why-should-there-be-spaces-around-and-in-bash).

## Full Bash Script
```
CPATH='.;lib/hamcrest-core-1.3.jar;lib/junit-4.13.2.jar'

rm -rf student-submission
mkdir student-submission
git clone $1 student-submission
echo 'Finished cloning'

cd student-submission

if [[ -f "ListExamples.java" ]]
then
    echo "File found"
else
    echo "File not found"
    exit 1
fi

cd ..

rm -rf mixed
mkdir mixed

cd student-submission
cp ListExamples.java ../mixed

cd ..
rm -rf student-submission


cp TestListExamples.java mixed

cp -r lib mixed

cd mixed

set +e

javac -cp $CPATH *.java 2>javac-errors.txt
if [[ $? -ne 0 ]]
then
    cat javac-errors.txt
else
    echo "Compile Success"
    java -cp $CPATH org.junit.runner.JUnitCore TestListExamples >results.txt
    # echo `grep -c "FAILURES!!!" results.txt`
    # echo `grep "FAILURES!!!" results.txt`
    

    if [[ `grep -c "FAILURES!!!" results.txt` -ne 0 ]]
    then
        echo "Grade is not 100%"
        RESULT_LINE=`grep "Tests run:" results.txt`
        COUNT=${RESULT_LINE:25:1}
        TOTAL=${RESULT_LINE:11:1}
        SCORE=$(( $TOTAL - $COUNT ))
        echo "Your Score is"
        echo "| Score: $SCORE/$TOTAL |"
    else
        echo "Grade is 100%"
    fi
fi

```
