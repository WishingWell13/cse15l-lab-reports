## Part 1
Here is my code for my StringServer. It consists of the StringHandler and StringServer classes.

```
import java.io.IOException;
import java.net.URI;

class StringHandler implements URLHandler {
    // The string state on server
    String myString = "";

    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            return String.format("Current string: %s", myString);
        } 
        // else if (url.getPath().contains("/add-message")) {
        //     String[] parameters = url.getQuery().split("=");
        //     if (parameters[0].equals("s")) {
        //         myString += parameters[1] + "\n";
        //         return myString;
        //     }else{
        //          return "invalid query";
        //      }
        // }
        else if(url.getPath().equals("/clear")){
            myString = "";
            return "Cleared!";
        }
        else {
            System.out.println("Path: " + url.getPath() + url.getQuery());
            if (url.getPath().contains("/add-message")) {
                String[] parameters = url.getQuery().split("=");
                if (parameters[0].equals("s")) {
                    myString += parameters[1] + "\n";
                    return myString;
                }
            }
            return "404 Not Found!";
        }
    }
}

public class StringServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new StringHandler());
    }
}


```

Here, we call the default path (without any queries) in our handleRequest method in our StringHandler class. As we can see, we start out with an empty string. No fields change.
<img width="496" alt="image" src="https://user-images.githubusercontent.com/54158686/215242978-1ea0ef91-6980-46db-976e-281c86d46adb.png">

Next, we try adding the string "<string>" to the string list using the path /add-message. We can see that it is successfully appended. We call the same handleRequest method, but it goes to the else part of the if else statement. Relevant arguments include the s to denote that we are passing in a string, and the message after the equal sign which is what we add to the string. The myString field of my code is updated to contain the passed in string.
<img width="362" alt="image" src="https://user-images.githubusercontent.com/54158686/215243233-0d8868b2-322d-4a22-af51-d59e9a14e1c5.png">

We pass in hello again to test if we can add multiple strings in a row. We can! The relevant inputs are as before, but with the input being "hello" instead of "<string>".
<img width="331" alt="image" src="https://user-images.githubusercontent.com/54158686/215243319-c17d29e5-1217-4588-966c-c49a865e3810.png">



## Part 2
#### Failure inducing input:
This test inputs an array of length three into the ArrayExamples.reverseInPlace function. The tester is below.
```
@Test 
	public void testReverseInPlaceLongArr() {
    int[] input1 = { 3, 5, 9 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 9, 5, 3 }, input1);
    
	}

```

We get the following ***symptom:***
<img width="470" alt="image" src="https://user-images.githubusercontent.com/54158686/215160886-b567b082-331e-4529-9108-664caec01bf6.png">
At element 2 we expected the output to be 3 but got 9 instead. 3 was the first element of the array.

Originally, I thought none of the values were swapping. However, after some print statements, I found that the first value went to the third value correctly.

***Bug:*** Looking at the code again, I noticed that when index 0 is being accessed to overwrite index 2, index 0 is already overwritten, so the original value is lost. This is our bug!

To fix the code, we can make a temporary variable to store the value we are going to overwrite. Then, we can use that temporary variable to assign to the variable that we just used to swap at the beginning (arr[arr.length - i - 1]). Finally, we cut the loop in half, since we are replacing values from both the beginning and end of the loop in each repetition.

Original code:

```
// Changes the input array to be in reversed order
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      # ------
      # NOTICE: arr[0[ will be overwritten! So we can't access it later.
      # ------
      arr[i] = arr[arr.length - i - 1];
    }
  }

```

Fixed Code:
```
static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length/2; i += 1) {
      int temp = arr[i];
      arr[i] = arr[arr.length - i - 1];
      arr[arr.length - i - 1] = temp;
    }
  }

```


#### Non-failure inducing input:
This test inputs an array of length 1 to the ArrayExamples.reverseInPlace function. The tester is below. There are no symptoms.
```
@Test 
public void testReverseInPlace() {
    int[] input1 = { 3 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 3 }, input1);
}
```
	   
  
## Part 3
I leanred that you can make web servers in Java this week! Before, I thought Javascript, HTML, and CSS were the dedicated languages for web development, but this is not the case. Also, I learned about the difference between a web server, a web page, and a web site. A web server is the brain of an operation, handling requests for URLs with web pages. So it is the part that moves and stores data. A web page is a single page that displays what the web server does. A web site is a collection of linked web pages that users can use to trigger different commands within the web server.
	    
	    
	    
	    
