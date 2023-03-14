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
- We can see that running the tests show that we have the error in line 14 of the test.
- Based on the information, we can identify that the root problem from ArrayExamples is that the method copies from itself as it is changing, thus only changing half of the array correctly.

<img width="400" alt="image" src="https://user-images.githubusercontent.com/122580137/224877859-69b8aabf-0743-4bde-b403-9c644366fd3d.png">

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
- Based on the information, we can identify that the root problem from ArrayExamples is that the method copies from the new empty copy of the array to the actual array we want to copy from. Just changing the location of these two arrays will correct the error.

<img width="400" alt="image" src="https://user-images.githubusercontent.com/122580137/224877896-92eba57a-9e7a-48ec-bff2-5007908c82a2.png">

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
- Based on the information, we can identify the root problem from ArrayExamples is that the method excludes all of the lowest numbers (if there are duplicate lowest numbers). We can fix this issue by changing the method so that the lowest number is only taken once from the sum.

<img width="400" alt="image" src="https://user-images.githubusercontent.com/122580137/224877944-d765ed70-59cc-4c71-9e2c-0b0cf81dbcc7.png">

## Part 2 - ListExamples.java
The raw Java code for ListExamples.java has a bug in all of the methods. 
The two methods are shown below.
```
  // Returns a new list that has all the elements of the input list for which
  // the StringChecker returns true, and not the elements that return false, in
  // the same order they appeared in the input list;
  static List<String> filter(List<String> list, StringChecker sc) {
    List<String> result = new ArrayList<>();
    for(String s: list) {
      if(sc.checkString(s)) {
        result.add(0, s);
      }
    }
    return result;
  }
  
  // Takes two sorted list of strings (so "a" appears before "b" and so on),
  // and return a new list that has all the strings in both list in sorted order.
  static List<String> merge(List<String> list1, List<String> list2) {
    List<String> result = new ArrayList<>();
    int index1 = 0, index2 = 0;
    while(index1 < list1.size() && index2 < list2.size()) {
      if(list1.get(index1).compareTo(list2.get(index2)) < 0) {
        result.add(list1.get(index1));
        index1 += 1;
      }
      else {
        result.add(list2.get(index2));
        index2 += 1;
      }
    }
    while(index1 < list1.size()) {
      result.add(list1.get(index1));
      index1 += 1;
    }
    while(index2 < list2.size()) {
      result.add(list2.get(index2));
      index1 += 1;
    }
    return result;
  }

```

### Testing First Method
> The first method is supposed to return a new ArrayList that has all the elements of the input ArrayList that returns true with the StringChecker.
> If we run the test with an empty list, the input does NOT induce a failure.
> However, if we run a test with a list with at least two indices, it does induce a failure.

| Testing with no failure | Testing with failure |
|---|---|
| <img width="300" alt="SFFMN" src="https://user-images.githubusercontent.com/122580137/224868919-9f6622ba-d3bc-438f-994f-80157e3b0ad9.jpeg"> | <img width="300" alt="SFFMY" src="https://user-images.githubusercontent.com/122580137/224868922-dc5f3c3e-bc15-48ac-a503-216a1f64d6e6.jpeg"> |
| <img width="300" alt="SFFMTN" src="https://user-images.githubusercontent.com/122580137/224869977-e2a62c44-f673-455d-8bc5-cba94a7d4ba7.jpeg"> | <img width="300" alt="SFFMTY" src="https://user-images.githubusercontent.com/122580137/224869771-0ca81d81-ba5b-48e1-851c-9282f3d41ab3.jpeg"> |

#### Using jdb to set a breakpoint.
- We can see that running the tests show that we have the error in line 31 of the test.
- Based on the information, we can identify the root problem from ListExamples is that the method continues to copy the element to the first index (index 0) of the new array. This will ultimately reverse the array. Switching the index from 0 to -1 will enable the elements to properly be copied.

<img width="400" alt="image" src="https://user-images.githubusercontent.com/122580137/224878242-98b033ab-6f49-4e50-9da3-04e5e450ca8d.png">


### Testing Second Method
> The second method is supposed to change and return the inputted array in reverse order, with a different new array.
> If we run a test with an empty array, the input does NOT induce a failure.
> However, if we run a test with a list with at least one index, there is an error.

| Testing with no failure | Testing with failure |
|---|---|
| <img width="300" alt="SFSMN" src="https://user-images.githubusercontent.com/122580137/224868920-544f20d7-5501-4079-bfe7-fd073f6736c9.jpeg"> | <img width="300" alt="SFSMY" src="https://user-images.githubusercontent.com/122580137/224868923-033b8e9d-9415-48a5-b9c8-f2536517624b.jpeg"> |
| <img width="300" alt="SFSMTN" src="https://user-images.githubusercontent.com/122580137/224869977-e2a62c44-f673-455d-8bc5-cba94a7d4ba7.jpeg"> | <img width="300" alt="SFSMTY" src="https://user-images.githubusercontent.com/122580137/224869773-4006d9bf-09d6-47b3-9566-d7b0679719ca.jpeg"> |

#### Using jdb to set a breakpoint.
- We can see that running the tests show that we have the error in line 31 of the test.
- Based on the information, we can identify the root problem from ListExamples is that the method added to the variable for the index of the first list when in fact it should be increasing the variable for the index of the second list.

<img width="400" alt="image" src="https://user-images.githubusercontent.com/122580137/224878490-9c7d4d20-d02f-45ba-8170-919fb2990b2c.png">

