Download Link: https://assignmentchef.com/product/solved-lab-3-cmput-398
<br>
<h1>Objective</h1>

In this lab you will implement a parallel merge.

This lab will be submitted as one zipped file through <a href="https://eclass.srv.ualberta.ca/portal/">eclass</a><a href="https://eclass.srv.ualberta.ca/portal/">.</a> Details for submission are at the end of the lab.

<h1>The Algorithm</h1>

Given inputs A and B as follows:

A = [0 2 4 10] B = [1 5 7 9]

C should be the following:

C = [0 1 2 4 5 7 9 10]

To merge the two arrays in parallel we need to find what index each element should be in C. The following table shows the index in C each element should be.

<table width="384">

 <tbody>

  <tr>

   <td width="157">A’s index in C</td>

   <td width="57">0</td>

   <td width="56">2</td>

   <td width="57">3</td>

   <td width="57">7</td>

  </tr>

  <tr>

   <td width="157">A</td>

   <td width="57">0</td>

   <td width="56">2</td>

   <td width="57">4</td>

   <td width="57">10</td>

  </tr>

  <tr>

   <td width="157">B</td>

   <td width="57">1</td>

   <td width="56">5</td>

   <td width="57">7</td>

   <td width="57">9</td>

  </tr>

  <tr>

   <td width="157">B’s index in C</td>

   <td width="57">1</td>

   <td width="56">4</td>

   <td width="57">5</td>

   <td width="57">6</td>

  </tr>

 </tbody>

</table>

How can we calculate the correct index? Let’s look at the 4 in A. We know it has two elements that come before it based of its index in A. Let i denote the index of the 4 in A. Now we need to find how many elements come before it in B. To do this we can run binary search. Doing this we realize one element comes before it. Let j be the index the value, in this example it’s 4, should be placed in B. Therefore, in this example we have the following:

i = 2 j = 1 A[i] = 4

C[i+j] = 4

The same algorithm can be applied to the elements in B.

If you need materials on Binary Search, a good article can be found at <a href="https://www.khanacademy.org/computing/computer-science/algorithms/binary-search/a/binary-search">https://www.khanacademy.org/computing/computer</a><a href="https://www.khanacademy.org/computing/computer-science/algorithms/binary-search/a/binary-search">–</a><a href="https://www.khanacademy.org/computing/computer-science/algorithms/binary-search/a/binary-search">science/algorithms/binary</a><a href="https://www.khanacademy.org/computing/computer-science/algorithms/binary-search/a/binary-search">search/a/binary</a><a href="https://www.khanacademy.org/computing/computer-science/algorithms/binary-search/a/binary-search">–</a><a href="https://www.khanacademy.org/computing/computer-science/algorithms/binary-search/a/binary-search">search</a>

<h1>Instructions: Parallel Merge with Binary Search</h1>

Edit the code where the TODOs are specified and perform the following:

<ul>

 <li>Implement the parallel merge kernel</li>

 <li>Implement a binary search routine on the GPU</li>

</ul>

The parallel merge kernel will be given two input arrays A and B. Your goal is to merge the two input arrays and produce an output array C. You can assume the following:

<ul>

 <li>A and B are both size N</li>

 <li>C is size 2N</li>

 <li>Both A and B are sorted arrays</li>

</ul>




The binary search routine is used as a helper function for the parallel merge kernel.

<h1>Instructions: Parallel Merge with Linear/Sequential Search</h1>

Now, implement a simple sequential search algorithm in the last TODO and replace the call to your binary search in merge sort kernel with sequential search.

After you make sure both your merge with binary search and with sequential search are correct by running the tests, do a performance analysis using NSIGHT to compare the run time of Merge using Binary Search and Merge using sequential search on <strong>test case 19</strong>. Save the screenshots of that show run times of the two algorithms to files “binary.png” and “sequential.png” in the Submission folder. Then, answer the question: which of them run faster and why? Put it in the Submission folder with the file name “compare.txt”.

The crop shows what you should put in NSIGHT:

<strong>Arguments</strong>: -e output.raw -i input0.raw,input1.raw -o myOutput.raw -t integral_vector




<h1>Local Setup Instructions</h1>

Steps:

<ol>

 <li>Download “Lab3.zip”.</li>

 <li>Unzip the file.</li>

 <li>Open the Visual Studios Solution in Visual Studios 2013.</li>

 <li>Build the project. Note the project has three configurations.

  <ol>

   <li>Debug</li>

   <li>Submission</li>

  </ol></li>

</ol>

But make sure you have the “Submission” configuration selected when you finally submit.

<ol start="5">

 <li>Run the program by pressing the following button:</li>

</ol>







Running the “Submission” configuration from Visual Studios will throw a runtime error as there are no arguments being passed.

<h1>Testing</h1>

While working on the lab you can test your code by running the program with the “Debug” configuration selected. This will run one of the tests located in “Dataset/Test”. You can also run the test script after you build with the “Submission” configuration selected. For more information, read the README located in the zip.

Note that in tests 0 to 9 the input arrays A and B don’t intersect. However, in tests 10 to 19 the input arrays A and B can intersect. This can give you a hint to what might be going wrong if you are only passing the first 10 tests.

<h1>Questions</h1>

<ol>

 <li>How many times is the binary search called? EXPLAIN.</li>

 <li>Does this algorithm in the current state work if A and B are not sorted? EXPLAIN.</li>

 <li>What is the best-case complexity of a merge algorithm written on the CPU? EXPLAIN.</li>

 <li>What common sorting algorithm could benefit from having a parallel merge?</li>

 <li>If arrays A and B don’t have unique elements or the intersect of A and B is not empty. Is there an issue with doing the exact same process with A as B or vice versa? If so what is the issue and how do you fix it?</li>

</ol>


