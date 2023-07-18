// ---------------------------------------------------------------------------
// File name:   arrayCalculator.cpp
// Assign ID:   PROG8a
//
// Due Date:    8/3/2021 at 11:00 pm 
//
// Purpose:     Implement a menu-driven array calculator.
//
// Author:      hallD241 Daylen Hall 
// ---------------------------------------------------------------------------

#include <cstdlib>
#include <iostream>
#include <fstream>
#include <iomanip>
using namespace std;
#include "arrayCalculatorFunctions.h"

// --------------------------------------------------------------
// Display the menu and read user's selection.
// --------------------------------------------------------------
void Show_Menu()
{
   char Choice;   // User menu selection.
   cout << endl << endl;
   cout << "+===========================================+" << endl;
   cout << "| *********    ARRAY CALCULATOR   ********* |" << endl;
   cout << "+ ----------------------------------------- +" << endl;
   cout << "|   l) Load array A from keyboard           |" << endl;
   cout << "|   L) Load array B from file               |" << endl;
   cout << "|   S) Save array C to file                 |" << endl;
   cout << "|   V) View array content                   |" << endl;
   cout << "|   v) View array A in reverse order        |" << endl;
   cout << "|   s) Compute sum of values in array B     |" << endl;
   cout << "|   m) Determine min value in array A       |" << endl;
   cout << "|   M) Determine max value in array B       |" << endl;
   cout << "|   A) Compute array sum, C = A + B         |" << endl;
   cout << "|   F) Search for a value in array A        |" << endl;
   cout << "|                                           |" << endl;
   cout << "|   P) Find position of a value in array A  |" << endl;
   cout << "|   C) Count #times value occurs in array B |" << endl;
   cout << "|   c) Copy array A contents into array B   |" << endl;
   cout << "|   E) Check equivalance of arrays A and B  |" << endl;
   cout << "|   O) Sort array A into ascending order    |" << endl;
   cout << "|   o) Sort array B into descending order   |" << endl;
   cout << "|                                           |" << endl;
   cout << "|   Q) QUIT (turn off)                      |" << endl;
   cout << "+ ----------------------------------------- +" << endl;
   cout << "|      (c) 2022, hallD241, Daylen Hall     |" << endl;
   cout << "+===========================================+" << endl;

}// Show_Menu


//--------------------------------------------------------------
// Determine the operation, then perform.
//--------------------------------------------------------------
void Perform_Calculation(char Choice,int arraySize,int A[],int B[],int C[])
{
    bool found;       // Flag indicating search found the desired value.
    int position;     // Array position where a value is found.
    char arrayN;      // Name of array -- A, B or C.
    string fileN;     // Name of file containing array B.
    int key;          // Value to search for in array.
    int foundAt;      // Position at which a search value is found.

    switch (Choice)
    {
       case 'l': // Load array A from keyboard.
                 cout << "\nEnter " << arraySize << " values for array A: ";
                 LoadArray(A, arraySize);
                 break;

       case 'L': // Load array B from a file.
                 cout << "\nEnter name of the file containing array B: ";
                 cin >> fileN;
                 LoadArray(fileN, B, arraySize);
                 break;


       case 'S': // Save array C to a file.
                 SaveArray(C, arraySize);
                 break;

       case 'A': // Add: C = A + B. 
                 AddArrays(A, B, C, arraySize);
                 break;

       case 'm': // Determine the minimum value in array A.
                 cout << endl << MinValue(A, arraySize) 
                      << " = MIN VALUE IN array A.\n";
                 break;

       case 'M': // Determine the maximum value in array B.
                 cout << endl << MaxValue(B, arraySize) 
                      << " = MAX VALUE IN array B.\n";
                 break;


       case 's': // Calculate the sum of the values in array B.
                 cout << endl << Sum(B, arraySize) 
                      << " = SUM OF VALUES in array B.\n";
                 break;

       case 'C': // Count frequency of value in array B.
                 cout << "\nEnter value to search for in array B: ";
                 cin >> key;
                 cout << key << " OCCURS " << Frequency(key, B, arraySize)
                 << " TIMES IN ARRAY B" << endl;
                 break;

       case 'F': // Find a value in array A.
                 cout << "\nEnter value to search for in array A: ";
                 cin >> key;
                 if (Search(key, A, arraySize))
                    cout << endl << key << " FOUND in array A." << endl;
                 else
                    cout << endl << key << " MISSING FROM array A." << endl;
                 break;


       case 'c': // Copy array A contents into B.
                 CopyArray(B, A, arraySize);
                 break;


       case 'P': // Find the position of a value in array A.
                 cout << "\nEnter value to search for in array A: ";
                 cin >> key;
                 foundAt = Position(key, A, arraySize);
                 cout << endl << key << " AT POSITION " << foundAt 
                      << " in array A." << endl;
                 break;

       case 'E': // Check equivalence of arrays A and B.
                 if ( EquivalentArrays(A,B,arraySize) )
                     cout << "\nGOOD NEWS, A==B\n";
                 else
                     cout << "\nSORRY, A!=B\n";

                 break;

       case 'O': // Sort array A into ascending order.
                 SortAscending(A, arraySize);
                 break;

       case 'o': // Sort array B into descending order.
                 SortDescending(B, arraySize);
                 break;


       case 'V': // View one of the arrays.
                 do
                 {
                    cout << "\nEnter name of the array to display [A, B or C]: ";
                    cin >> arrayN; 
                 }
                 while (arrayN != 'A' && arrayN != 'B' && arrayN != 'C');
                 if (arrayN == 'A') ShowArray("Array A: ", A, arraySize); 
                 if (arrayN == 'B') ShowArray("Array B: ", B, arraySize); 
                 if (arrayN == 'C') ShowArray("Array C: ", C, arraySize); 
                 break;

       case 'v': // View contents of array A, in reverse order.
                 ShowReversedArray("Array A reversed: ", A, arraySize); 
                 break;

       case 'Q': // Quit 
                 cout << endl << "Q: POWERING DOWN ..." << endl;
                 break;


       default:  // Bad Input.
                 cout << endl << "BAD MENU CHOICE." << endl;
                 break;

    }//end_switch

}// Perform_Calculation

int main()
{
    
    //----------------------------------------------------------------------
    // Declare variables for program.
    //----------------------------------------------------------------------
    char Choice;              // Menu choice.
    int A[20], B[20], C[20];  // Menu choice.
    int arraySize = -1;       // => uninitialized arrays.
    string throwaway;         // Input buffer purge.
    string numeral;           // Safe read of array size.

    //-| --------------------------------------------------------------
    //-| Read the array size from the keyboard.
    //-| --------------------------------------------------------------
    do
    {
       cout << endl << "\nEnter the SIZE of all the arrays [0-20]: ";
       cin >> arraySize;
    }
    while (arraySize < 0 || arraySize > 20);


    //-| --------------------------------------------------------------
    //-| Repeat until user enters 'Q' or 'q': 
    //-|
    //-|     1. Display the menu and read user's selection.
    //-|     2. Determine the operation, then perform.
    //-| --------------------------------------------------------------
    do 
    {
       Show_Menu();
       cout << "\nEnter Menu Choice: ";
       cin >> Choice;

       Perform_Calculation(Choice, arraySize, A, B, C);
    } 
    while (toupper(Choice) != 'Q');

    //-| --------------------------------------------------------------
    //-| Display copyright. 
    //-| --------------------------------------------------------------
    cout << "\n\n(c) 2022, hallD241 Daylen Hall\n\n";

    return 0;
}//main
