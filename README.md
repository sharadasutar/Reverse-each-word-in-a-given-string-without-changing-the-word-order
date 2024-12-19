# Reverse-each-word-in-a-given-string-without-changing-the-word-order
Write a function in C to reverse each word in a given string without changing the word order. The function should work within constrained memory limits, avoiding dynamic memory               allocation(e.g., malloc) and using only a limited number of additional variables. Assume that the string can fit within a standard fixed-length.
/*
   Name:SHARADA SUTAR
   Date:
   Description:Write a function in C to reverse each word in a given string without changing the word order. The function should work within constrained memory limits, avoiding dynamic memory
              allocation(e.g., malloc) and using only a limited number of additional variables. Assume that the string can fit within a standard fixed-length buffer, as is typical in embedded systems.
   Sample Input:"hello world"
   Sample Output:"olleh dlrow"

*/

#include <stdio.h>
#include <string.h>


//Function to reverse a segment of the string
void reverse(char* str, int start, int end)
{
    while(start < end)     //condition to check character upto end
    {
        char temp = str[start];           //store first string character to temp variable 
        str[start] = str[end];             //store end string segment to start string segment
        str[end] = temp;                 //store temp variable to end string segment
        start++;                          //increment start string segment
        end--;                     //decrement end string segment
    }
}


//Function to reverse each word in the string
void reverseEachWord(char* str)
{
    int start = 0;   // start index of a word

    int len = strlen(str);

    for(int i = 0; i <= len; i++)
    {
        //A word ends when we find a space or the null terminator
        if(str[i] == ' ' || str[i] == '\0') 
        {
            reverse(str, start, i - 1);   //Reverse the current word
            start = i + 1;                  //move to the next word
        }
    }
}

int main()
{
    /*
    char str[] = "hello world";     //Input string
        printf("Input: \"%s\"\n", str);

        */
    char str[256];    //Buffer to hold the input string
    printf("Enter a string: ");
    fgets(str, sizeof(str),stdin);    //safely read input from the user

    //Remove trailing newline character if present
    size_t len = strlen(str);
    if(len > 0 && str[len - 1] == '\n') 
    {
        str[len -1] = '\0';
    }



    reverseEachWord(str);    //Reverse each word in the string

    printf("Output: \"%s\"\n",str);
    return 0;
}
