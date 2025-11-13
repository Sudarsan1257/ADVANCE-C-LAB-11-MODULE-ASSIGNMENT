# ADVANCE-C-LAB-11-MODULE-ASSIGNMENT
## EXP NO:21 C PROGRAM TO CREATE A FUNCTION TO FIND THE GREATEST NUMBER
## Aim:
To write a C program to create a function to find the greatest number

## Algorithm:
1.	Include the necessary header #include <stdio.h>.
2.	Use a series of if and else if statements to compare the values and return the maximum among them.
3.	Declare variables n1, n2, n3, n4, and greater to store user input and the result.
4.	Use scanf to take four integers as input.
5.	Call the max_of_four function with the input integers and store the result in the greater variable
 
## Program:
```
#include <stdio.h>

// Function to find the greatest number among four integers
int max_of_four(int n1, int n2, int n3, int n4) {
    int max;

    if (n1 >= n2 && n1 >= n3 && n1 >= n4) {
        max = n1;
    }
    else if (n2 >= n1 && n2 >= n3 && n2 >= n4) {
        max = n2;
    }
    else if (n3 >= n1 && n3 >= n2 && n3 >= n4) {
        max = n3;
    }
    else {
        max = n4;
    }

    return max;
}

int main() {
    int n1, n2, n3, n4, greater;

    // Taking four integers as input
    printf("Enter four integers: ");
    scanf("%d %d %d %d", &n1, &n2, &n3, &n4);

    // Call the function and store the result
    greater = max_of_four(n1, n2, n3, n4);

    // Display the result
    printf("The greatest number among %d, %d, %d, and %d is: %d\n", n1, n2, n3, n4, greater);

    return 0;
}

```

## Output:
<img width="491" height="243" alt="image" src="https://github.com/user-attachments/assets/749635e3-f0a6-45fe-a544-347328d4fd95" />


## Result:
Thus, the program  that create a function to find the greatest number is verified successfully.


 
## EXP NO:22 C PROGRAM TO PRINT THE MAXIMUM VALUES FOR THE AND, OR AND  XOR COMPARISONS
## Aim:
To write a C program to print the maximum values for the AND, OR and XOR comparisons

## Algorithm:
1.	Define a function calculate_the_max that takes two integers n and k as parameters.
2.	Declare variables a, o, and x to store the maximum values for AND, OR, and XOR operations, respectively.
3.	Use nested loops to iterate through pairs of integers (i, j) from 1 to n.
4.	Within the loops, check conditions for AND, OR, and XOR operations and update the corresponding maximum values (a, o, x).
5.	Declare variables n and k to store user input.
6.	Use scanf to take two integers as input.
7.	Call the calculate_the_max function with input values.
 
## Program:
```
#include <stdio.h>

// Function to calculate maximum values for AND, OR, and XOR
void calculate_the_max(int n, int k) {
    int a = 0, o = 0, x = 0;  // Variables to store maximum values

    // Nested loops to iterate through pairs (i, j)
    for (int i = 1; i <= n; i++) {
        for (int j = i + 1; j <= n; j++) {
            int and_val = i & j;
            int or_val  = i | j;
            int xor_val = i ^ j;

            // Update maximum values if within limit k
            if (and_val > a && and_val < k) {
                a = and_val;
            }
            if (or_val > o && or_val < k) {
                o = or_val;
            }
            if (xor_val > x && xor_val < k) {
                x = xor_val;
            }
        }
    }

    // Print the results
    printf("Maximum AND value less than %d: %d\n", k, a);
    printf("Maximum OR value less than %d: %d\n", k, o);
    printf("Maximum XOR value less than %d: %d\n", k, x);
}

int main() {
    int n, k;

    // Take user input
    printf("Enter two integers (n and k): ");
    scanf("%d %d", &n, &k);

    // Call the function
    calculate_the_max(n, k);

    return 0;
}
```

## Output:
<img width="454" height="248" alt="image" src="https://github.com/user-attachments/assets/2d1a964a-a44d-44c0-988b-d3b37d5b60fb" />


## Result:
Thus, the program to print the maximum values for the AND, OR and XOR comparisons
is verified successfully.


 
## EXP NO:23 C PROGRAM TO WRITE THE LOGIC FOR THE REQUESTS
## Aim:
To write a C program to write the logic for the requests

## Algorithm:
1.	Declare variables noshel and noque to store the number of shelves and the number of queries, respectively.
2.	Use scanf to take two integers as input for the number of shelves and queries.
3.	Declare a 2D array shelarr to represent shelves and books, and an array nobookarr to store the number of books on each shelf.
4.	Declare variables k and c to keep track of the book index and the total number of books.
5.	Use a for loop to iterate over the queries.
 
## Program:
```
#include <stdio.h>
#include <stdlib.h>

int main() {
    int noshel, noque;   // number of shelves and queries
    scanf("%d %d", &noshel, &noque);

    // 2D array to represent shelves and books
    int **shelarr = (int **)malloc(noshel * sizeof(int *));
    int *nobookarr = (int *)malloc(noshel * sizeof(int));

    // Initialize shelves with zero books
    for (int i = 0; i < noshel; i++) {
        shelarr[i] = NULL;
        nobookarr[i] = 0;
    }

    int k, c;  // variables for book index and total number of books

    // Process queries
    for (int q = 0; q < noque; q++) {
        int type;
        scanf("%d", &type);

        if (type == 1) {
            // Query type 1: Add a book to a shelf
            int shelf, pages;
            scanf("%d %d", &shelf, &pages);

            nobookarr[shelf]++;  // increase book count
            shelarr[shelf] = (int *)realloc(shelarr[shelf], nobookarr[shelf] * sizeof(int));
            shelarr[shelf][nobookarr[shelf] - 1] = pages;  // store book pages
        }
        else if (type == 2) {
            // Query type 2: Print number of pages in a book
            int shelf, book;
            scanf("%d %d", &shelf, &book);
            printf("%d\n", shelarr[shelf][book]);
        }
        else if (type == 3) {
            // Query type 3: Print number of books on a shelf
            int shelf;
            scanf("%d", &shelf);
            printf("%d\n", nobookarr[shelf]);
        }
    }

    // Free allocated memory
    for (int i = 0; i < noshel; i++) {
        free(shelarr[i]);
    }
    free(shelarr);
    free(nobookarr);

    return 0;
}

```

## Output:
<img width="480" height="553" alt="image" src="https://github.com/user-attachments/assets/14b923c3-8687-417b-8a2d-2606b0b9d8f6" />



## Result:
Thus, the program to write the logic for the requests is verified successfully.


 
## EXP NO:24 C PROGRAM PRINT THE SUM OF THE INTEGERS IN THE ARRAY.
## Aim:
To write a C program print the sum of the integers in the array.

## Algorithm:
1.	Declare a variable n to store the number of integers.
2.	Use scanf to take an integer n as input.
3.	Declare an array a of size n to store the integers.
4.	Declare a variable sum and initialize it to zero.
5.	Use a for loop to iterate n times:
6.	Use scanf to input each integer and add it to the sum.
7.	Print the final sum using printf.



## Program:
//type your code here

## Output:
//paste your output here

 


## Result:
Thus, the program prints the sum of the integers in the array is verified successfully.


 
## EXP NO 25: C PROGRAM TO COUNT THE NUMBER OF WORDS IN A      SENTENCE



## Aim:

To write a C program that counts the number of words in a given sentence.

## Algorithm:

1.	Input the sentence: Take a sentence from the user.
2.	Initialize a counter variable: This will keep track of the number of words.
3.	Process each character of the sentence:
o	Iterate through the sentence, checking each character.
o	If a character is not a space, it may belong to a word. If it's the first non-space character after a space or at the start, increment the word count.
4.	Handle spaces and punctuation: Skip over spaces, punctuation marks, and consider each word as a sequence of characters separated by spaces.
5.	Display the result: After processing the sentence, output the total word count.



## Program:
//type your code here

## Output:
//paste your output here



## Result:
Thus, the program that counts the number of words in a given sentence is verified 
successfully.
