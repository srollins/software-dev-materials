Exam 2 Review
=============

Following is a list of topics that may appear on Exam 2. *This list is subject to change.*

You may be asked to define a term; explain a concept; answer a short-answer, multiple choice, or true/false question about a concept; trace a block of code and describe its output; or implement a block of code.

There will be more programming/implementation questions on Exam 2 than there were on Exam 1.

### Topics

1. Object-oriented design of programs
2. Has-a relationship/aggregation
3. Static data members and methods
4. Interfaces
5. Comparable
6. Method overloading
7. Arrays - 1D, declaring and using
8. Arrays - 2D
9. Image Manipulation
10. Command line arguments
11. Subclasses - `super`, `extends`, `protected`, `abstract`
12. Class hierarchies
13. `final` data members, methods, classes
14. Late/dynamic binding
15. Polymorphism

### Practice Questions

Which of the following assignments are valid? Select all that apply.
 
```		
		a. Comparable c = new Comparable(5);
		b. String s = new Comparable(“Hello”);
		c. Comparable c = new Integer(9);
		d. None of the above
```

Which of the following are valid declarations of an array. Select all that apply.

```
		a. double[] scores = new double[10];
		b. String[] words = {"cat", "apple", "banana", "dog"};
		c. String[] words = new String[5];
		d. double[] numbers = new int[5];
```

True / False - A parent class that will be extended must be declared `abstract`.
 
What is the output of the following program?

```
		public class ArraysAndMethods {
   			public void absoluteValues(int[] numbers) {
   			   for(int i = 0; i < numbers.length; i++) {
      				if(numbers[i] < 0) {
                		numbers[i] = numbers[i] * -2;
            		}
        		} 
    		}
 		
 			public static void main(String[] args) {
      			int[] numbers = {4, -1, 5, 3, -9, 4, -4, 2};
        		ArraysAndMethods aam = new ArraysAndMethods();
		     	aam.absoluteValues(numbers);
      			System.out.println(numbers[numbers.length-2]);
			}	
		}
```	

This question asks you to implement a method for the StringList class as defined as in Lab 4. As a reminder, the class was defined with the following data members.

```
		public class StringList {

			//an array that maintains a list of String objects
			//the default initial size of the array is 10
			private String[] strings;

			//the number of valid String objects stored in the 
			//array of strings
			private int count;
		}
```

Implement a method `removeLast` that takes as input a `String` and removes the last occurrence of that `String` in the list. If the `String` does not appear in the list the method does nothing. You may not rely on any other methods of the class. The following shows the state of the instances variables before and after a call to `removeLast` with the input “cat”.

Before: 
`strings -> {“cat”, “dog”, “cat”, “bird”, “cat”, “alpaca”, null, null, null, null}, count=6`

After: 
`strings -> {“cat”, “dog”, “cat”, “bird”, “alpaca”, null, null, null, null, null}, count=5`

It is also fine if you leave the item at position 5 as “alpaca” as long as count is updated correctly.

Implement a method `bottomLeft` that takes as input a `Picture` object and returns a new `Picture` object containing only the bottom left portion of the original. Given an image of size 200x200 the method will return an image of size 100x100 containing the bottom left portion.

