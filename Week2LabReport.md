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

