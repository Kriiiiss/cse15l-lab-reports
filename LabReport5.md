# Lab Report 5 - Putting it All Together 

## Part1 – Debugging Scenario

Scenario: I have a question that the output of my code is wrong. Since the output should be `[a, apple]` and my output is `[apple, a]`. I supposed that the output is reversed in order and I don't know how to change it. Could you give some idea of how to fix the problem?

<img width="519" alt="Screenshot 2023-12-02 at 22 26 47" src="https://github.com/Kriiiiss/cse15l-lab-reports/assets/147010005/8448dc34-6dec-4b64-9324-c1ac1a4e1bfe">

TA: For this question, you can check your code as you add strings to the result list. You can add a test case with 5 string to check if all the output is reversed. If yes, your code might be have some problem when adding a string to the list.

Student: I have tried with 5 string and all of them are reversed. So adding the string to the end of the list may be wrong.

<img width="706" alt="Screenshot 2023-12-02 at 22 33 51" src="https://github.com/Kriiiiss/cse15l-lab-reports/assets/147010005/89163b3d-1c58-4ea9-87e9-66bd1d7169fc">

File and directory structure

```
.
./ListExamplesTests.class
./.DS_Store
./.gitignore
./lib
./lib/junit-4.13.2.jar
./lib/hamcrest-core-1.3.jar
./ListExamples.class
./ListExamples.java
./test.sh
./ListExamplesTests.java
./StringChecker.class
```

File: ListExamples.java

```
import java.util.ArrayList;
import java.util.List;

interface StringChecker { boolean checkString(String s); }

class ListExamples {

  static List<String> filter(List<String> list, StringChecker sc) {
    List<String> result = new ArrayList<>();
    for(String s: list) {
      if(sc.checkString(s)) {
        result.add(0, s);
      }
    }
    return result;
  }
}
```

File: ListExamplesTests.java

```
import static org.junit.Assert.*;
import org.junit.*;
import java.util.*;
import java.util.ArrayList;


public class ListExamplesTests {
	@Test
  	public void testFilter() {
	    List<String> strs = new ArrayList<>();
	    strs.add("a");
	    strs.add("b");
	    strs.add("apple");
	    List<String> filtered = ListExamples.filter(strs, s -> s.charAt(0) == 'a');
	    assertEquals(Arrays.asList("a", "apple"), filtered);
	  }

	@Test
  	public void testFilter2() {
	    List<String> strs = new ArrayList<>();
	    strs.add("a");
	    strs.add("b");
	    strs.add("ama");
		strs.add("aba");
		strs.add("ada");
		strs.add("aca");
	    List<String> filtered = ListExamples.filter(strs, s -> s.charAt(0) == 'a');
	    assertEquals(Arrays.asList("a", "ama","aba", "ada", "aca"), filtered);
	  }
}
```

File: test.sh

```
javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java
java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests
```

The full command line (or lines) you ran to trigger the bug:
```
bash test.sh
```

I use JUnit to test my code. The symptom will appear when run Junit test. The output shows that my two tests fails so I can know that `result.add(0, s);` is wrong since this function is to add the string at beginning of the list. So I fix the problem `result.add(s);` The code is fixed as following.

```
class ListExamples {

  static List<String> filter(List<String> list, StringChecker sc) {
    List<String> result = new ArrayList<>();
    for(String s: list) {
      if(sc.checkString(s)) {
        result.add(s);
      }
    }
    return result;
  }
}
```

## Part2 - Reflection

In the second half of this quarter, I have learned how to use bash script to run all the test. It is a easy way to put all the command to this bash script and run them together. I also know how to use bash script to do some easy coding. The coolest thing is to experience how to be a Gradescope to Grade homework. Additionally, I have learned many command line to run my code, Including use `git` and `vim` to edit my file in terminal and upload to Github. The most interesting thing is to use webserver to create a file and connect to the local computer. I have learned a lot from this class and lab.

