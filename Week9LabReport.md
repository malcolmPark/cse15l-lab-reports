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

| Testing with no failure | Testing with failure |
|---|---|
| <img width="300" alt="FFFMN" src="https://user-images.githubusercontent.com/122580137/224846253-3c169a36-6a2d-4768-8039-757c807b203a.jpeg"> | <img width="300" alt="FFFMY" src="https://user-images.githubusercontent.com/122580137/224846274-42a9ce57-fd1b-4c86-9c08-d8db9c8a7bc9.jpeg"> |
| <img width="300" alt="FFFMTN" src="https://user-images.githubusercontent.com/122580137/224853075-d0b90ea2-5201-46b0-93bd-50dbc6c8c379.jpeg"> | <img width="300" alt="FFFMTY" src="https://user-images.githubusercontent.com/122580137/224853078-0e197ae9-9f6f-446d-a50c-8d4d78c79f29.jpeg"> |

#### Using jdb to set a breakpoint.
- We can see that running the tests show that we have the error in line 9 of the test.
- 

### Testing Second Method
> The second method is supposed to change and return the inputted array in reverse order, with a different new array.
> If we run a test with an empty array, the input does NOT induce a failure.
> However, if we run a test with a list with at least one index, there is an error.

| Testing with no failure | Testing with failure |
|---|---|
| <img width="300" alt="FFSMN" src="https://user-images.githubusercontent.com/122580137/224857666-2b9586d7-2077-4636-88e8-282f6858bd6d.jpeg"> | <img width="300" alt="FFSMY" src="https://user-images.githubusercontent.com/122580137/224857668-eb2bc518-7392-4855-843a-c8df6349d6b0.jpeg"> |
| <img width="300" alt="FFSMTN" src="https://user-images.githubusercontent.com/122580137/224857874-9af0ee6d-55da-4f88-8bfa-137248579afa.jpeg"> | <img width="300" alt="FFSMTY" src="https://user-images.githubusercontent.com/122580137/224857877-50ff05ad-07eb-4fad-aac2-6e771e96a63b.jpeg"> |

#### Using jdb to set a breakpoint.
- We can see that running the tests show that we have the error in line 16 of the test.

### Testing Third Method
> The third method is supposed to average the numbers in an array but leaves out the lowest
> number in the array when it calculates the mean. If its an empty array or just one index, it will return 0.
> If we run a test with a singular number, the input does NOT induce a failure.
> However, if we run a test with a list with at least two indices, there is an error.

| Testing with no failure | Testing with failure |
|---|---|
| <img width="300" alt="FFTMN" src="https://user-images.githubusercontent.com/122580137/224860813-1f4a2f94-4727-4598-bd9c-cb1fbcdfd3a1.jpeg"> | <img width="300" alt="FFTMY" src="https://user-images.githubusercontent.com/122580137/224860817-15ad5639-dc63-4de2-bc19-563fc8ee5e4d.jpeg"> |
| <img width="300" alt="FFTMTN" src="https://user-images.githubusercontent.com/122580137/224861063-21d7b6f1-ca29-41f1-a0b0-11c6b0540dc6.jpeg"> | <img width="300" alt="FFTMTY" src="https://user-images.githubusercontent.com/122580137/224861062-60a1442e-dc90-4d7d-9272-5ebda2be4d67.jpeg"> |

#### Using jdb to set a breakpoint.
- We can see that running the tests show that we have the error in line 21 of the test.



