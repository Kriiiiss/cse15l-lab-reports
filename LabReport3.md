# Lab Report 3 - Bugs and Commands

## Part 1 - Bugs

```
#Original Code

public class ArrayExamples {

  // Changes the input array to be in reversed order
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
}
```

**1. A failure-inducing input for the buggy program, as a JUnit test and any associated code**

```
import static org.junit.Assert.*;
import org.junit.*;

public class ArrayTests {
    @Test
    public void testReverseInPlace1() {
	int[] input1 = {1,2,3};
	ArrayExamples.reverseInPlace(input1);
	assertArrayEquals(new int[]{3,2,1}, input1);
    }
}
```

**2. An input that doesn’t induce a failure, as a JUnit test and any associated code**

```
import static org.junit.Assert.*;
import org.junit.*;

public class ArrayTests {
    @Test
    public void testReverseInPlace2() {
        int[] input1 = { 3 };
        ArrayExamples.reverseInPlace(input1);
        assertArrayEquals(new int[]{ 3 }, input1);
    }
}
```

**3. The symptom, as the output of running the tests**

<img width="1073" alt="Screenshot 2023-11-04 at 15 08 21" src="https://github.com/Kriiiiss/cse15l-lab-reports/assets/147010005/ce1bc55e-f1bd-454c-9cf9-4960dcefac00">

**4. The bug, as the before-and-after code change required to fix it**

Before

```
static void reverseInPlace(int[] arr) {
  for(int i = 0; i < arr.length; i += 1) {
    arr[i] = arr[arr.length - i - 1];
  }
}
```

After

```
static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length/2; i += 1) {
      int temp;
      temp = arr[i];
      arr[i] = arr[arr.length - i - 1];
      arr[arr.length - i - 1] = temp;
    }
  }
```

The purpose of this code is to changes the input array to be in reversed order. For the first test, the output is {3,2,3} which means the index[0] is missing. For the second test, the output is {3} which is correct. I find that if the number of array is large than 1, the bug will appear. For this code, I find that I don't have to reverse each index in a for loop which would cause the already inverted index to invert again, causing an error. So I change the for loop to run arr.length/2 times. The second bug is that the code don't store the value of first half of the array and overwrite it. In this case, I create a veriable called temp to store the previous value so that the value will not be overwrite and assign to reversed index correctly.



## Part 2 - Researching Commands `grep`

Option 1 --- `-i`

```
% grep -i "apple" technical/biomed/*
technical/biomed/1468-6708-3-10.txt:        questions requiring large sample sizes and to grapple with
technical/biomed/1471-2105-3-12.txt:            This problem appears to lie in the JAVA applet included
technical/biomed/1471-2105-3-12.txt:            Moving an Apple-supplied "JAVA Accelerator for PowerPC"
technical/biomed/1471-2105-3-12.txt:            applet-generated graph may be problematic due to an
technical/biomed/1471-2105-3-12.txt:            applet incompatibility; capturing the graph as a
technical/biomed/1471-2121-2-11.txt:          Apple Power Mac 9600.
technical/biomed/1471-2121-2-18.txt:          camera and an Apple Macintosh computer for capturing
technical/biomed/1471-2202-2-5.txt:            http://rsb.info.nih.gov/nih-imageand an Apple Macintosh
technical/biomed/1471-2202-2-5.txt:            computer http://www.apple.com. If the criteria for
technical/biomed/1471-2458-3-11.txt:        fresh-pressed apple cider [ 28 ] . Other foodborne
technical/biomed/1472-6793-2-1.txt:            accelerated Power Mac 6100/66 computer (Apple Computer,
technical/biomed/1472-6793-2-1.txt:            7500/100 (Apple Computer, Cupertino, Ca). The system
technical/biomed/1472-6882-1-10.txt:          antibiotics and the ananase enzyme (from the pineapple 
technical/biomed/gb-2002-3-10-research0053.txt:          in pineapple (~70% to 
technical/biomed/gb-2002-3-12-research0077.txt:          the JAVA applet WebMol [ 35]. In this setting, the color
technical/biomed/gb-2003-4-8-r51.txt:            visualized using QuickPDB, a Java applet developed by
```

The command-line options `-i` is used to search a string in a txt file in whatever uppercase and lowercase. The example above shows that when we search a string "apple", the output shows the uppercase and lowercase "apple" which can help us search more relative information.

```
% grep -i "HaPPy" technical/plos/*  
technical/plos/journal.pbio.0020053.txt:        Administration unhappy. “Phage normally are very fragile, their tails break, so lot-to-lot
technical/plos/journal.pbio.0020140.txt:        mood of two people presented in a pair and, as much as possible, to select the ‘happy’
technical/plos/journal.pbio.0020140.txt:        person, who would then smile. Over time, the person with the ‘happy’ mood (who would smile
technical/plos/journal.pbio.0020164.txt:        happy—would not cross the scientific mind. Yet in biology we often pose “why” questions in
technical/plos/journal.pbio.0020262.txt:        are happy to be called dwarfs or little people, but midget is no longer an acceptable term.
technical/plos/journal.pbio.0030065.txt:        still tend to be unhappy. However, analyses have shown that this score is in the range of
technical/plos/journal.pbio.0030129.txt:        identities, we are happy to cooperate, subject to the permission of the reviewers. This can
technical/plos/pmed.0010052.txt:        Elliott professes to be unhappy about enhancement. What arguments does he present to
technical/plos/pmed.0020118.txt:        medical schools may not be producing doctors who are happy with the profession, or who fit
technical/plos/pmed.0020158.txt:        reports and their identities, we are happy to cooperate, subject to the permission of the
technical/plos/pmed.0020203.txt:        important study at this interface between biology and medicine, and will be happy to talk
technical/plos/pmed.0020209.txt:            an entire institution whose mission is to approve drugs and make industry happy.”
```

The command-line options `-i` is used to search a string in a txt file in whatever uppercase and lowercase. The example above shows that when we search a string "HaPPy", the output shows the uppercase and lowercase "happy" that can help us avoid case errors.


---
Option 2 --- `-l`

```
% grep -l "Pair" technical/biomed/*
technical/biomed/1471-2105-3-14.txt
technical/biomed/1471-2105-3-2.txt
technical/biomed/1471-2121-3-4.txt
technical/biomed/1471-2148-1-8.txt
technical/biomed/1471-2148-3-1.txt
technical/biomed/1471-2164-3-27.txt
technical/biomed/1471-2164-3-7.txt
technical/biomed/1471-2164-3-9.txt
technical/biomed/1471-2180-2-29.txt
technical/biomed/1471-2202-2-20.txt
technical/biomed/1471-2296-3-3.txt
technical/biomed/1472-6793-2-1.txt
technical/biomed/1472-6793-2-11.txt
technical/biomed/1472-6793-2-8.txt
technical/biomed/1472-6807-2-4.txt
technical/biomed/1475-2875-2-4.txt
technical/biomed/1476-4598-1-5.txt
technical/biomed/1477-7525-1-9.txt
technical/biomed/ar615.txt
technical/biomed/bcr45.txt
technical/biomed/cc2172.txt
technical/biomed/gb-2001-2-11-research0046.txt
technical/biomed/gb-2001-2-12-research0053.txt
technical/biomed/gb-2001-2-4-research0011.txt
technical/biomed/gb-2001-2-9-research0037.txt
technical/biomed/gb-2002-3-12-research0079.txt
technical/biomed/gb-2002-3-12-research0086.txt
technical/biomed/gb-2002-3-2-research0008.txt
technical/biomed/gb-2002-3-4-research0019.txt
technical/biomed/gb-2002-3-5-research0024.txt
technical/biomed/gb-2002-3-5-research0025.txt
technical/biomed/gb-2002-3-6-software0001.txt
technical/biomed/gb-2002-3-7-research0032.txt
technical/biomed/gb-2002-3-7-research0037.txt
technical/biomed/gb-2002-3-8-research0038.txt
technical/biomed/gb-2003-4-2-r14.txt
technical/biomed/gb-2003-4-3-r17.txt
technical/biomed/gb-2003-4-4-r24.txt
technical/biomed/gb-2003-4-7-r43.txt
```

The command-line options `-l` only shows the file which contain string "Pair" exactly. We can only see how many files contain this string and don't care about how many string in one file.

```
% grep  -l "help" technical/911report/*
technical/911report/chapter-1.txt
technical/911report/chapter-10.txt
technical/911report/chapter-11.txt
technical/911report/chapter-12.txt
technical/911report/chapter-13.1.txt
technical/911report/chapter-13.3.txt
technical/911report/chapter-13.4.txt
technical/911report/chapter-13.5.txt
technical/911report/chapter-2.txt
technical/911report/chapter-3.txt
technical/911report/chapter-5.txt
technical/911report/chapter-6.txt
technical/911report/chapter-7.txt
technical/911report/chapter-8.txt
technical/911report/chapter-9.txt
technical/911report/preface.txt
```

The command-line options `-l` only shows the file which contain string "help". This will help us find which chapter contains the word "help".

---
Option 3 --- `-r`

```
% grep  -r "save" technical/911report/*
technical/911report/chapter-1.txt:    NORAD officials have maintained that they would have intercepted and shot down United 93. We are not so sure. We are sure that the nation owes a debt to the passengers of United 93. Their actions saved the lives of countless others, and may have saved either the Capitol or the White House from destruction.
technical/911report/chapter-13.4.txt:                Tenet called the supplemental appropriation "a lifesaver." See, for example, the
technical/911report/chapter-2.txt:                though Iraq's dictator, Saddam Hussein, had never had an Islamist agenda-save for
technical/911report/chapter-7.txt:                that they wanted to save money. They may also have been reconsidering the wisdom of
technical/911report/chapter-9.txt:                despite that knowledge to remain in an attempt to save additional lives. According
```

The command-line options `-r` shows the line in this file which can help us find how many lines contain "save" in this directory.

```
% grep  -r "AppLe" technical/911report/*
(The output is empty)
```

The command-line options `-r` shows the line in this file which can help us find how many lines contain "AppLe" in this directory. However, option `-r` can only find the string exactly "AppLe"with same uppercase and lower case. We can find the specific terminology in a text file.

---
Option 4 --- `-n`

```
% grep  -n "apple" technical/biomed/*
technical/biomed/1468-6708-3-10.txt:488:        questions requiring large sample sizes and to grapple with
technical/biomed/1471-2105-3-12.txt:316:            This problem appears to lie in the JAVA applet included
technical/biomed/1471-2105-3-12.txt:321:            applet-generated graph may be problematic due to an
technical/biomed/1471-2105-3-12.txt:322:            applet incompatibility; capturing the graph as a
technical/biomed/1471-2202-2-5.txt:540:            computer http://www.apple.com. If the criteria for
technical/biomed/1471-2458-3-11.txt:47:        fresh-pressed apple cider [ 28 ] . Other foodborne
technical/biomed/1472-6882-1-10.txt:192:          antibiotics and the ananase enzyme (from the pineapple 
technical/biomed/gb-2002-3-10-research0053.txt:439:          in pineapple (~70% to 
technical/biomed/gb-2002-3-12-research0077.txt:469:          the JAVA applet WebMol [ 35]. In this setting, the color
technical/biomed/gb-2003-4-8-r51.txt:355:            visualized using QuickPDB, a Java applet developed by
```

The command-line options `-n` shows the line number of each matched string "apple". It helps us find the line on which the string appears.

```
% grep  -n "File" technical/911report/*
technical/911report/chapter-13.2.txt:777:            133. FAA Audio File, Herndon Command Center, Boston Center position, line 5115,
technical/911report/chapter-13.3.txt:768:                of the FAA's Intelligence Case Files. The FBI analyst who worked on the 1998 tasking
technical/911report/chapter-13.3.txt:834:                FAA records, Intelligence Case File 98-96.
technical/911report/chapter-13.3.txt:1479:                Case File 98-0199B. A Saudi who had just completed pilot training, boarding a flight
technical/911report/chapter-13.5.txt:2751:                Eiffel Tower. FAA report, FAA Intelligence Case File 94-305, undated.
```

The command-line options `-n` shows the line number of each matched string "file". It helps us find the line on which the string appears.

**Reference**
https://en.wikibooks.org/wiki/Grep
