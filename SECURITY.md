# Security Policy

## Supported Versions

| Version | Supported          |
| ------- | ------------------ |
| <=latest   | :white_check_mark:|


## Reporting a Vulnerability

To report a vulnerability, please follow these steps:

1. Submit a detailed report via email to [security@yourproject.com](mailto:security@yourproject.com).
2. You can expect an initial response acknowledging receipt of your report within 48 hours.
3. Our security team will investigate the reported vulnerability promptly.
4. If the vulnerability is accepted, we will provide updates on the progress of the fix and notify you when it's resolved.
5. If the vulnerability is declined, we will provide a rationale for our decision and any necessary guidance.

## Title: Report on Stack Overflow Vulnerability in C/sorting/binary_insertion_sort.c

**Abstract:**
This report highlights a stack overflow vulnerability in the `binary_insertion_sort.c` file within the `C/sorting` directory. The vulnerability leads to a segmentation fault when executing the program with certain input sizes. Additionally, it is observed that when compiled with O2/O3 optimization flags, the program runs indefinitely without terminating.

**1. Introduction:**
The `binary_insertion_sort.c` file contains an implementation of the binary insertion sort algorithm in the C programming language. However, it has been discovered that the program encounters a segmentation fault and an infinite loop in specific scenarios, indicating potential stack overflow vulnerabilities and optimization-related issues.

**2. Vulnerability Description:**
The stack overflow vulnerability arises due to insufficient stack space allocation during the sorting process. As the binary insertion sort algorithm recursively calls itself, it relies on the stack to store intermediate values and function calls. If the size of the input array is large or the recursion depth becomes significant, the stack may overflow, resulting in a segmentation fault.

**3. Reproduction Steps:**
To reproduce the issue, follow these steps:
a. Compile the `binary_insertion_sort.c` file using the GCC compiler:
```
gcc binary_insertion_sort.c
```
b. Execute the compiled program:
```
./a.out
```
c. When prompted, enter the size of the array and provide the corresponding elements.
```sh
Enter size of array:
50
Enter the elements of the array
10 81 36 5 96 13 61 56 83 20 63 91 37 56 64 92 20 88 13 27 96 74 69 81 39 72 48 57 35 3 59 32 58 9 18 34 1 64 72 32 95 86 38 31 60 79 99 59 45 76
Original array: 10 81 36 5 96 13 61 56 83 20 63 91 37 56 64 92 20 88 13 27 96 74 69 81 39 72 48 57 35 3 59 32 58 9 18 34 1 64 72 32 95 86 38 31 60 79 99 59 45 76
zsh: segmentation fault (core dumped)  ./a.out
```
d. Observe the segmentation fault error message indicating a program crash.
![image](https://github.com/TheAlgorithms/C/assets/118088443/a5d706b1-b47a-4f34-9ecd-747226d334b1)
And, if compile with O2/O3, it runs without stop.
![image](https://github.com/TheAlgorithms/C/assets/118088443/35e30528-9469-4479-a1c3-40bb6eccaed3)

**4. Impact:**
The stack overflow vulnerability has the following potential impact:
- Program crash: The vulnerability leads to a segmentation fault, causing the program to terminate abruptly.
- Denial of Service: An attacker may exploit this vulnerability to repeatedly crash the program, resulting in a denial of service condition.

**5. Mitigation:**
To address the stack overflow vulnerability, the following steps are recommended:
a. Increase stack size: Allocate a larger stack size to handle larger input arrays and deeper recursion levels. This can be achieved by adjusting compiler or linker options or using platform-specific techniques.
b. Implement iterative sorting: Consider modifying the algorithm to use an iterative approach instead of recursion, eliminating the reliance on the stack.
c. Input validation: Implement proper input validation to ensure that the input array size is within acceptable limits.
d. Error handling: Enhance error handling mechanisms to handle exceptional conditions gracefully and prevent crashes.

**6. Optimization-related Issue:**
The observed behavior of the program running indefinitely when compiled with O2/O3 optimization flags suggests a potential issue with the optimization process. Further investigation and analysis are required to understand the root cause and implement necessary fixes.

**7. Conclusion:**
The stack overflow vulnerability identified in the `binary_insertion_sort.c` file can lead to program crashes and potential denial of service conditions. Additionally, the observed optimization-related issue requires attention to ensure the program terminates correctly. By implementing the recommended mitigation measures and addressing the optimization-related issue, developers can enhance the stability, security, and performance of the code.

**8. References:**
[Provide any references or sources consulted during the analysis, if applicable.]

Please note that this report is based on the information available up to September 2021, and further updates or developments may have occurred since then.
