# **Week 9 Lab Report** by Malcolm Park (Jooahn)

This weeks lab report will focus on writing a markdown file that is based on how
we can improve the lab activity from week 3's buggy files using jdb to set breakpoints
 throughout the files and answer the relevant questions regarding the variables, fields, 
and arguments.

## Part 1 - ArrayExamples.java
The raw Java code for ArrayExamples.java has a bug in all of the methods. 
The three methods are shown below.
```
  // Changes the input array to be in reversed order
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
  
  // Returns a *new* array with all the elements of the input array in reversed
  // order
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }
  
  // Averages the numbers in the array (takes the mean), but leaves out the
  // lowest number when calculating. Returns 0 if there are no elements or just
  // 1 element in the array
  static double averageWithoutLowest(double[] arr) {
    if(arr.length < 2) { return 0.0; }
    double lowest = arr[0];
    for(double num: arr) {
      if(num < lowest) { lowest = num; }
    }
    double sum = 0;
    for(double num: arr) {
      if(num != lowest) { sum += num; }
    }
    return sum / (arr.length - 1);
  }
```

### Testing First Method
> The first method is supposed to change and return the inputted array in reverse order.
> If we run a test with a singular number, the input does NOT induce a failure.
> However, if we run a test with a list with at least two indices, there is an error.

![FFFMN](https://user-images.githubusercontent.com/122580137/224846253-3c169a36-6a2d-4768-8039-757c807b203a.jpeg)
![FFFMY](https://user-images.githubusercontent.com/122580137/224846274-42a9ce57-fd1b-4c86-9c08-d8db9c8a7bc9.jpeg)


1. First loading the server to localhost:4000.
- <img width="300" alt="Screen Shot 2023-01-30 at 3 55 09 PM" src="https://user-images.githubusercontent.com/122580137/215623544-7e09227c-7ba9-40d5-b783-9191a4c896b8.png">
- This screenshot shows what happens when we first load the server. Only the words "Current String:" appear because we haven't
appended anything to the string instance variable yet.
2. Using `/add-message?s=Hello, my name is Malcolm`.
- <img width="300" alt="Screen Shot 2023-01-30 at 3 57 33 PM" src="https://user-images.githubusercontent.com/122580137/215623798-b32c2245-e3fd-4540-ba6d-122d6330add3.png">
- When we add the string value "Hello, my name is Malcolm", we see "Statement appended!".
- Now, if we move back to the starting url (http://localhost:4000/) we see that the instance variable has changed.
- <img width="300" alt="Screen Shot 2023-01-30 at 3 59 57 PM" src="https://user-images.githubusercontent.com/122580137/215624128-88999a69-9cd6-4f27-b09b-54dda4c9df6a.png">
3. Using `/add-message?s=I love to code in Java! I wonder what your favorite language is?`.
- Lets see if this works if we append a longer string as well.
- <img width="300" alt="Screen Shot 2023-01-30 at 4 04 00 PM" src="https://user-images.githubusercontent.com/122580137/215624587-ca157608-b12a-4963-90c6-1591832e7b72.png">
- When we add the string value "I love to code in Java! I wonder what your favorite language is?", we again see
"Statement appended!".
- Now if we move back to the starting url again (http://localhost:4000/) we see that the instance variable has changed.
- <img width="300" alt="Screen Shot 2023-01-30 at 4 05 32 PM" src="https://user-images.githubusercontent.com/122580137/215624744-4c74e829-fbbe-4611-9c14-5c214f6c29bb.png">
4. Using `/add-message?s=`
- This will show an edge case that represents a situation where we leave the appending message section blank.
- <img width="300" alt="image" src="https://user-images.githubusercontent.com/122580137/215628224-7c17eb69-aa64-4eba-a006-9551b58794a9.png">
- In this case, it returns "Message not filled" and indicates that the message section of the query is empty. It does not append
anything in this situation.


### Explanation of each screenshot
For both screenshots, the main method creates a URLHandler that manages the string instance variable, and then uses Server.java file
that we used in the lab of Week 2 to start a web server.
1. For the first and second screenshot, when we first load the server we call the method handleRequest. When we load the server, the 
if, else if, and else statements are run to append string values appropriately at the right condtions. The parameter for this
method is the url itself. By running the url of "localhost:4000/add-message?s=Hello, my name is Malcolm" and
"localhost:4000/add-message?s=I love to code in Java! I wonder what your favorite language is?", the method checks if the 
words "add-message" is contained in the url. If there is, the query of the url is split by the = sign, and the elements are 
added into a string array called partsOfQuery. The first element in this array will be "s", and the second element will be
 "Hello, my name is Malcolm", which is then appended to the instance variable statement with a new line (\n).

2. For the third screenshot, it is still the same when we first load the server, we call the method handleRequest. Since there,
 are the words "add-message", it will still pass on to the else if statement, but since the string array partsOfQuery will only
 have a length of one, it returns the statement "Message not filled" and the instance variable is not changed.

## Part 2
>The bugs that I chose from lab 3 is for the Array Methods case.
1. A failure-inducing input for the buggy program.
- <img width="300" alt="Screen Shot 2023-01-30 at 4 49 24 PM" src="https://user-images.githubusercontent.com/122580137/215630180-4689e5fc-0b01-4e44-8e92-e9c820877c32.png">
- This failure inducing input is an array of ints, {4, 5, 6, 7}. The correct output would be {7, 6, 5, 4} but the actual output is {7, 6, 6, 7}.<br><br>

2. An input that doesn't induce a failure.
- <img width="300" alt="Screen Shot 2023-01-30 at 4 53 11 PM" src="https://user-images.githubusercontent.com/122580137/215630670-810d370e-8633-418f-8541-32ab5525e1fa.png">
- This is an input that doesn't induce a failure. The input is an array of ints, {3}. The correct output would be {3} which coincides with the actual output.<br><br>

3. The symptom of running the tests.<br>
- <img width="300" alt="Screen Shot 2023-01-30 at 4 55 42 PM" src="https://user-images.githubusercontent.com/122580137/215631061-dc574ba8-2aa5-419c-900f-fab3b929dc0b.png"><br><br>

4. The bug.
- Before: ![Screen Shot 2023-02-13 at 12 21 03 PM](https://user-images.githubusercontent.com/122580137/218566832-545b7d35-6565-4a02-abe1-cccc69a63724.jpeg)
- After: <img width="300" alt="Screen Shot 2023-01-30 at 4 56 58 PM" src="https://user-images.githubusercontent.com/122580137/215631457-53472cef-0ba5-4d5e-b5c8-e7a23f2564ea.png">
- As it iterates through the array, only the first half of the array is successfully changed, and the second half only copies the already changed values from the first half. The second method makes the mistake of copying from the new array to the old array. The first fix addresses the issue because it makes a copy of the array firsthand and then copies the elements backwards so that the elements that are copied are not affected during the process. The second fix addresses the issue by just changing the empty array from being copied to the actual array we want copied.<br><br>


## Part 3
This part of the md file is to explain new terms and ideas I learned during the past weeks.
Though I always had a slim idea of what Symptoms, Bugs, and Failure-Inducing Inputs were, I 
learned what they actually meant in the CSE 15L class. It was also honestly very surprising 
to learn that errors do not necessarily mean bugs if the error message was intended from the 
start.
