------------------------------------------------------------------------------------------------
                             Bit Manipulation
------------------------------------------------------------------------------------------------

Count set bits in an integer	
-----------------------------------
Write an efficient program to count the number of 1s in the binary representation of an integer.
Examples : 

Input : n = 6
Output : 2
Binary representation of 6 is 110 and has 2 set bits

Input : n = 13
Output : 3
Binary representation of 13 is 1101 and has 3 set bits

1. Simple Method Loop through all bits in an integer, check if a bit is set and if it is, then increment the set bit count. See the program below. 


// C++ program to Count set
// bits in an integer
#include <bits/stdc++.h>
using namespace std;
 
/* Function to get no of set bits in binary
representation of positive integer n */
unsigned int countSetBits(unsigned int n)
{
    unsigned int count = 0;
    while (n) {
        count += n & 1;
        n >>= 1;
    }
    return count;
}
 
/* Program to test function countSetBits */
int main()
{
    int i = 9;
    cout << countSetBits(i);
    return 0;
}

Output : 
2
Time Complexity: O(logn) 
Auxiliary Space: O(1)

Recursive Approach:  

//cpp implementation of recursive approach to find the number of set bits in binary representation of positive integer n
#include <bits/stdc++.h>
using namespace std;
 
// recursive function to count set bits
int countSetBits(int n)
{
    // base case
    if (n == 0)
        return 0;
    else
        // if last bit set add 1 else add 0
        return (n & 1) + countSetBits(n >> 1);
}
 
// driver code
int main()
{
    int n = 9;
    // function calling
    cout << countSetBits(n);
    return 0;
}
 
Output : 
2
Time Complexity: O(log n)
Auxiliary Space: O(log n) for recursive stack space

2. Brian Kernighan’s Algorithm: 
Subtracting 1 from a decimal number flips all the bits after the rightmost set bit(which is 1) including the rightmost set bit. 
for example : 
10 in binary is 00001010 
9 in binary is 00001001 
8 in binary is 00001000 
7 in binary is 00000111 
So if we subtract a number by 1 and do it bitwise & with itself (n & (n-1)), we unset the rightmost set bit. If we do n & (n-1) in a loop and count the number of times the loop executes, we get the set bit count. 
The beauty of this solution is the number of times it loops is equal to the number of set bits in a given integer. 

1  Initialize count: = 0
2  If integer n is not zero
      (a) Do bitwise & with (n-1) and assign the value back to n
          n: = n&(n-1)
      (b) Increment count by 1
      (c) go to step 2
3  Else return count

// C++ program to Count set bits in an integer
#include <iostream>
using namespace std;
class gfg {
    /* Function to get no of set bits in binary
representation of passed binary no. */
public:
    unsigned int countSetBits(int n)
    {
        unsigned int count = 0;
        while (n) {
            n &= (n - 1);
            count++;
        }
        return count;
    }
};
/* Program to test function countSetBits */
int main()
{
    gfg g;
    int i = 9;
    cout << g.countSetBits(i);
    return 0;
}
Output : 
2
Example for Brian Kernighan’s Algorithm:  

   n =  9 (1001)
   count = 0

   Since 9 > 0, subtract by 1 and do bitwise & with (9-1)
   n = 9&8  (1001 & 1000)
   n = 8
   count  = 1

   Since 8 > 0, subtract by 1 and do bitwise & with (8-1)
   n = 8&7  (1000 & 0111)
   n = 0
   count = 2

   Since n = 0, return count which is 2 now.
Time Complexity: O(logn)
Auxiliary Space: O(1)

Recursive Approach:  

// CPP implementation for recursive approach to find the number of set bits using Brian Kernighan’s Algorithm
#include <bits/stdc++.h>
using namespace std;
 
// recursive function to count set bits
int countSetBits(int n)
{
    // base case
    if (n == 0)
        return 0;
    else
        return 1 + countSetBits(n & (n - 1));
}
 
// driver code
int main()
{
    // get value from user
    int n = 9;
 
    // function calling
    cout << countSetBits(n);
 
    return 0;
}

Output
2
Time Complexity: O(logn)
Auxiliary Space: O(log n)

Find the two non-repeating elements in an array of repeating elements	
--------------------------------------------------------------------------
Given an array in which all numbers except two are repeated once. (i.e. we have 2n+2 numbers and n numbers are occurring twice and remaining two have occurred once). Find those two numbers in the most efficient way.  

Method 1(Use Sorting) 
First, sort all the elements. In the sorted array, by comparing adjacent elements we can easily get the non-repeating elements. 

// C++ program for above approach
#include <bits/stdc++.h>
using namespace std;
 
/* This function sets the values of
*x and *y to non-repeating elements
in an array arr[] of size n*/
vector<int> get2NonRepeatingNos(int nums[], int n)
{
 
    sort(nums, nums + n);
 
    vector<int> ans;
    for (int i = 0; i < n - 1; i = i + 2) {
        if (nums[i] != nums[i + 1]) {
            ans.push_back(nums[i]);
            i = i - 1;
        }
    }
 
    if (ans.size() == 1)
        ans.push_back(nums[n - 1]);
 
    return ans;
}
 
/* Driver code */
int main()
{
    int arr[] = { 2, 3, 7, 9, 11, 2, 3, 11 };
    int n = sizeof(arr) / sizeof(*arr);
    vector<int> ans = get2NonRepeatingNos(arr, n);
    cout << "The non-repeating elements are " << ans[0]
         << " and " << ans[1];
}

Output

The non-repeating elements are 7 and 9
Time complexity: O(nLogn)
Auxiliary Space: O(1)

Method 2(Use XOR) 
Let x and y be the non-repeating elements we are looking for and arr[] be the input array. First, calculate the XOR of all the array elements. 

     xor = arr[0]^arr[1]^arr[2].....arr[n-1]
All the bits that are set in xor will be set in one non-repeating element (x or y) and not in others. So if we take any set bit of xor and divide the elements of the array in two sets – one set of elements with same bit set and another set with same bit not set. By doing so, we will get x in one set and y in another set. Now if we do XOR of all the elements in the first set, we will get the first non-repeating element, and by doing same in other sets we will get the second non-repeating element. 

Let us see an example.
   arr[] = {2, 4, 7, 9, 2, 4}
1) Get the XOR of all the elements.
     xor = 2^4^7^9^2^4 = 14 (1110)
2) Get a number which has only one set bit of the xor.   
   Since we can easily get the rightmost set bit, let us use it.
     set_bit_no = xor & ~(xor-1) = (1110) & ~(1101) = 0010
   Now set_bit_no will have only set as rightmost set bit of xor.
3) Now divide the elements in two sets and do xor of         
   elements in each set and we get the non-repeating 
   elements 7 and 9. Please see the implementation for this step.
Approach : 
Step 1: Xor all the elements of the array into a variable sum thus all the elements present twice in an array will get removed as for example, 4 = “100” and if 4 xor 4 => “100” xor “100” thus answer will be “000”. 
Step 2: Thus in the sum the final answer will be 3 xor 5 as both 2 and 4 are xor with itself giving 0, therefore sum = “011” xor “101” i.e sum = “110” = 6. 
Step 3: Now we will take 2’s Complement of sum i.e (-sum) = “010”. 
Step 4: Now bitwise And the 2’s of sum with the sum i.e “110” & “010” gives the answer “010” (Aim for bitwise & is that we want to get a number that contains only the rightmost set bit of the sum). 
Step 5: bitwise & all the elements of the array with this obtained sum, 2 = “010” & “010” = 2, 3 = “011” & “010” = “010” , 4 = “100” & “010” = “000”, 5 = “101” & “010” = “000”. 
Step 6: As we can see that the bitwise & of 2,3 > 0 thus they will be xor with sum1 and bitwise & of 4,5 is resulting into 0 thus they will be xor with sum2. 
Step 7: As 2 is present two times so getting xor with sum1 two times only the result 3 is being stored in it and As 4 is also present two times thus getting xor with sum2 will cancel it’s value and thus only 5 will remain there.

Implementation: 

// C++ program for above approach
#include <bits/stdc++.h>
using namespace std;
 
/* This function sets the values of
*x and *y to non-repeating elements
in an array arr[] of size n*/
void get2NonRepeatingNos(int arr[], int n, int* x, int* y)
{
    /* Will hold Xor of all elements */
    int Xor = arr[0];
 
    /* Will have only single set bit of Xor */
    int set_bit_no;
    int i;
    *x = 0;
    *y = 0;
 
    /* Get the Xor of all elements */
    for (i = 1; i < n; i++)
        Xor ^= arr[i];
 
    /* Get the rightmost set bit in set_bit_no */
    set_bit_no = Xor & ~(Xor - 1);
 
    /* Now divide elements in two sets by
    comparing rightmost set bit of Xor with bit
    at same position in each element. */
    for (i = 0; i < n; i++) {
 
        /*Xor of first set */
        if (arr[i] & set_bit_no)
            *x = *x ^ arr[i];
        /*Xor of second set*/
        else {
            *y = *y ^ arr[i];
        }
    }
}
 
/* Driver code */
int main()
{
    int arr[] = { 2, 3, 7, 9, 11, 2, 3, 11 };
    int n = sizeof(arr) / sizeof(*arr);
    int* x = new int[(sizeof(int))];
    int* y = new int[(sizeof(int))];
    get2NonRepeatingNos(arr, n, x, y);
    cout << "The non-repeating elements are " << *x
         << " and " << *y;
}
 
Output
The non-repeating elements are 7 and 9
Time Complexity: O(n) 
Auxiliary Space: O(1)

Method 3(Use Maps)

In this method, we simply count frequency of each element. The elements whose frequency is equal to 1 is the number which is non-repeating. The solution is explained below in the code-

// C++ program for Find the two non-repeating elements in
// an array of repeating elements/ Unique Numbers 2
 
#include <bits/stdc++.h>
using namespace std;
 
/* This function prints the two non-repeating elements in an
 * array of repeating elements*/
 
void get2NonRepeatingNos(int arr[], int n)
{
    /*Create map and calculate frequency of array
       elements.*/
 
    map<int, int> m;
    for (int i = 0; i < n; i++) {
        m[arr[i]]++;
    }
 
    /*Traverse through the map and check if its second
      element that is the frequency is 1 or not. If this is
      1 than it is the non-repeating element print it.It is
      clearly mentioned in problem that all numbers except
      two are repeated once. So they will be printed*/
 
    cout << "The non-repeating elements are ";
    for (auto& x : m) {
        if (x.second == 1) {
            cout << x.first << " ";
        }
    }
}
 
/* Driver code */
int main()
{
    int arr[] = { 2, 3, 7, 9, 11, 2, 3, 11 };
    int n = sizeof(arr) / sizeof(arr[0]);
    get2NonRepeatingNos(arr, n);
}

Output
The non-repeating elements are 7 9 
Time Complexity: O(nlogn) 
Auxiliary Space: O(n)

Method 4(Use Sets):

In this method, We check if the element already exists, if it exists we remove it else we add it to the set.

Approach:

Step 1: Take each element and check if it exists in the set or not. If it exists go to step-3. If it doesn’t exist go to step-2.

Step 2: Add the element to the set and go to step-4.

Step 3: Remove the element from the set and go to step-4.

Step 4: Print the elements of the set.

Implementation:
// C++ program to find 2 non repeating elements
// in array that has pairs of numbers
#include <bits/stdc++.h>
using namespace std;
 
// Method to print the 2 non repeating elements in an array
void print2SingleNumbers(int nums[], int n)
{
 
    // Create a Map Set to store the numbers
    multiset<int> set;
 
    /*Iterate through the array and check if each
    element is present or not in the set. If the
  element is present, remove it from the array
  otherwise add it to the set*/
 
    for (int i = 0; i < n; i++) {
        auto it = set.find(nums[i]);
        if (it != set.end())
            set.erase(it);
        else
            set.insert(nums[i]);
    }
 
    /*Since there will only be 2 non-repeating elements
  we can directly print them*/
    cout << "The 2 non repeating numbers are : "
         << *set.begin() << " " << *next(set.begin(), 1);
}
 
// Driver code
int main()
{
    int nums[] = { 2, 3, 7, 9, 11, 2, 3, 11 };
    int n = sizeof(nums) / sizeof(nums[0]);
    print2SingleNumbers(nums, n);
}
 
Output
The 2 non repeating numbers are : 7 9
Time complexity: O(n) for given array of size n

Count number of bits to be flipped to convert A to B	
-----------------------------------------------------------
Given two numbers A and B. Write a program to count the number of bits needed to be flipped to convert A to B. 

Examples: 

Input: A = 10, B = 20
Output: 4
Explanation: Binary representation of A is 00001010
Binary representation of B is 00010100
We need to flip highlighted four bits in A to make it B.

Input: A = 7, B = 10
Output: 3
Explanation: Binary representation of A is 00000111
Binary representation of B is 00001010
We need to flip highlighted three bits in A to make it B.

Using the XOR operator:
To solve the problem follow the below idea:

Calculate (A XOR B), since 0 XOR 1 and 1 XOR 0 is equal to 1. So calculating the number of set bits in A XOR B will give us the count of the number of unmatching bits in A and B, which needs to be flipped

Follow the given steps to solve the problem:

Calculate the XOR of A and B
Count the set bits in the above-calculated XOR result
Return the count

// C++ program for the above approach
#include <bits/stdc++.h>
using namespace std;
 
// Function that count set bits
int countSetBits(int n)
{
    int count = 0;
    while (n > 0) {
        count++;
        n &= (n - 1);
    }
    return count;
}
 
// Function that return count of flipped number
int FlippedCount(int a, int b)
{
    // Return count of set bits in
    // a XOR b
    return countSetBits(a ^ b);
}
 
// Driver code
int main()
{
    int a = 10;
    int b = 20;
   
      // Function call
    cout << FlippedCount(a, b) << endl;
    return 0;
}

Output
4

Using built in function __builtin_popcount()

// C++ program to Count number of bits to be flipped to convert A into B
#include <iostream>
using namespace std;
 
// Driver code
int main()
{
    int a = 10;
    int b = 20;
   
      // Function call
    cout <<__builtin_popcount(a^b) << endl;
    return 0;
}
 
Output
4
Time Complexity: O(K) where K is the number of bits
Auxiliary Space: O(1) 


Using the AND operator:
To solve the problem follow the below idea:

Start comparing the bits in A and B, starting from the least significant bit and if (A & 1) is not equal to (B & 1) then the current bit needs to be flipped, as the value of bits is different at this position in both the numbers

Follow the given steps to solve the problem:

Declare variable flips equal to zero
Run a loop, while a is greater than zero and b is also greater than zero
Calculate values of (A AND 1) and (B AND 1)
If these values are not equal then increase the flip value by 1
Right shift a and b by 1
Return flips

// C++ program for the above approach
#include <iostream>
using namespace std;
 
int countFlips(int a, int b)
{
 
    // initially flips is equal to 0
    int flips = 0;
 
    // & each bits of a && b with 1 and store them if t1 and t2 if t1 != t2 then we will flip that bit
 
    while (a > 0 || b > 0) {
 
        int t1 = (a & 1);
        int t2 = (b & 1);
 
        if (t1 != t2) {
            flips++;
        }
        // right shifting a and b
        a >>= 1;
        b >>= 1;
    }
 
    return flips;
}
 
int main()
{
    int a = 10;
    int b = 20;
    cout << countFlips(a, b);
}

Output
4
Time Complexity: O(K) where K is the number of bits
Auxiliary Space: O(1)

Count total set bits in all numbers from 1 to n	
-----------------------------------------------------
Given a positive integer N, the task is to count the total number of set bits in binary representation of all numbers from 1 to N. 

Examples: 

Input: N = 3
Output:  4
Explanation: Numbers from 1 to 3: {1, 2, 3}
Binary Representation of 1: 01 -> Set bits = 1
Binary Representation of 2: 10 -> Set bits = 1
Binary Representation of 3: 11 -> Set bits = 2
Total set bits from 1 till 3 = 1 + 1 + 2 = 4

Input: N = 6
Output: 9

Input: N = 7
Output: 12

By converting each number into its Binary Representation:
The idea is to convert each number from 1 till N into binary, and count the set bits in each number separately.

Follow the steps below to understand how:

Traverse a loop from 1 to N
For each integer in 1 to N:
Convert the number to its binary representation
Add the count of 1s in the binary representation to the answer.
Return the total set bits count.

// A simple program to count set bits in all numbers from 1 to n.
#include <iostream>
using namespace std;
 
// A utility function to count set bits in a number x
unsigned int countSetBitsUtil(unsigned int x);
 
// Returns count of set bits present in all numbers from 1 to n
unsigned int countSetBits(unsigned int n)
{
    int bitCount = 0; // initialize the result
 
    for (int i = 1; i <= n; i++)
        bitCount += countSetBitsUtil(i);
 
    return bitCount;
}
 
// A utility function to count set bits in a number x
unsigned int countSetBitsUtil(unsigned int x)
{
    if (x <= 0)
        return 0;
    return (x % 2 == 0 ? 0 : 1) + countSetBitsUtil(x / 2);
}
 
// Driver program to test above functions
int main()
{
    int n = 4;
    cout << "Total set bit count is " << countSetBits(n);
    return 0;
}

Output
Total set bit count is 5
Time Complexity: O(N*log(N)), where N is the given integer and log(N) time is used for the binary conversion of the number.
Auxiliary Space: O(1).

Method 2 (Simple and efficient than Method 1) 
If we observe bits from rightmost side at distance i than bits get inverted after 2^i position in vertical sequence. 
for example n = 5; 
0 = 0000 
1 = 0001 
2 = 0010 
3 = 0011 
4 = 0100 
5 = 0101
Observe the right most bit (i = 0) the bits get flipped after (2^0 = 1) 
Observe the 3rd rightmost bit (i = 2) the bits get flipped after (2^2 = 4) 
So, We can count bits in vertical fashion such that at i’th right most position bits will be get flipped after 2^i iteration;


#include <bits/stdc++.h>
using namespace std;
 
// Function which counts set bits from 0 to n
int countSetBits(int n)
{
    int i = 0;
 
    // ans store sum of set bits from 0 to n
    int ans = 0;
 
    // while n greater than equal to 2^i
    while ((1 << i) <= n) {
 
        // This k will get flipped after
        // 2^i iterations
        bool k = 0;
 
        // change is iterator from 2^i to 1
        int change = 1 << i;
 
        // This will loop from 0 to n for
        // every bit position
        for (int j = 0; j <= n; j++) {
 
            ans += k;
 
            if (change == 1) {
                k = !k; // When change = 1 flip the bit
                change = 1 << i; // again set change to 2^i
            }
            else {
                change--;
            }
        }
 
        // increment the position
        i++;
    }
 
    return ans;
}
 
// Main Function
int main()
{
    int n = 17;
    cout << countSetBits(n) << endl;
    return 0;
}
Output
35
Time Complexity: O(k*n) 
where k = number of bits to represent number n 
k <= 64

Program to find whether a no is power of two	
------------------------------------------------
Given a positive integer n, write a function to find if it is a power of 2 or not

Examples: 

Input : n = 4
Output : Yes
Explanation: 22 = 4

Input : n = 32
Output : Yes
Explanation: 25 = 32

A simple method for this is to simply take the log of the number on base 2 and if you get an integer then the number is the power of 2

// C++ Program to find whether a no is a power of two
#include <bits/stdc++.h>
using namespace std;
 
// Function to check if x is power of 2
bool isPowerOfTwo(int n)
{
    if (n == 0)
        return false;
 
    return (ceil(log2(n)) == floor(log2(n)));
}
 
// Driver code
int main()
{
    // Function call
    isPowerOfTwo(31) ? cout << "Yes" << endl
                     : cout << "No" << endl;
    isPowerOfTwo(64) ? cout << "Yes" << endl
                     : cout << "No" << endl;
 
    return 0;
}
 
Output
No
Yes
Time Complexity: O(1)
Auxiliary Space: O(1)

Using the division operator

Another solution is to keep dividing the number by two, i.e, do n = n/2 iteratively. In any iteration, if n%2 becomes non-zero and n is not 1 then n is not a power of 2. If n becomes 1 then it is a power of 2. 

// C++ program for the above approach
#include <bits/stdc++.h>
using namespace std;
 
/* Function to check if x is power of 2*/
bool isPowerOfTwo(int n)
{
    if (n == 0)
        return 0;
    while (n != 1) {
        if (n % 2 != 0)
            return 0;
        n = n / 2;
    }
    return 1;
}
 
// Driver code
int main()
{
    // Function call
    isPowerOfTwo(31) ? cout << "Yes\n" : cout << "No\n";
    isPowerOfTwo(64) ? cout << "Yes\n" : cout << "No\n";
    return 0;
}
Output
No
Yes
Time Complexity: O(log N)
Auxiliary Space: O(1)

// C++ program for above approach
#include <bits/stdc++.h>
using namespace std;
 
// Function which checks whether a number is a power of 2
bool powerOf2(int n)
{
    // base cases
    // '1' is the only odd number which is a power of 2(2^0)
    if (n == 1)
        return true;
 
    // all other odd numbers are not powers of 2
    else if (n % 2 != 0 || n == 0)
        return false;
 
    // recursive function call
    return powerOf2(n / 2);
}
 
// Driver Code
int main()
{
    int n = 64; // True
    int m = 12; // False
 
    // Function call
    if (powerOf2(n) == 1)
        cout << "True" << endl;
 
    else
        cout << "False" << endl;
 
    if (powerOf2(m) == 1)
        cout << "True" << endl;
 
    else
        cout << "False" << endl;
}
Output
True
False
Time Complexity: O(log N)
Auxiliary Space: O(log N)

By checking the count of set bits:
To solve the problem follow the below idea:

All power of two numbers has only a one-bit set. So count the no. of set bits and if you get 1 then the number is a power of 2. Please see Count set bits in an integer for counting set bits.

// C++ program of the above approach
#include <bits/stdc++.h>
using namespace std;
 
/* Function to check if x is power of 2*/
bool isPowerOfTwo(int n)
{
    /* First x in the below expression is for the case when x is 0 */
    int cnt = 0;
    while (n > 0) {
        if ((n & 1) == 1) {
            cnt++;
        }
        n = n >> 1; // keep dividing n by 2 using right
                    // shift operator
    }
 
    if (cnt == 1) { // if cnt = 1 only then it is power of 2
        return true;
    }
    return false;
}
 
// Driver code
int main()
{
    // Function call
    isPowerOfTwo(31) ? cout << "Yes\n" : cout << "No\n";
    isPowerOfTwo(64) ? cout << "Yes\n" : cout << "No\n";
    return 0;
}
Output
No
Yes
Time complexity: O(N)
Auxiliary Space: O(1)

Find whether a given number is a power of 2 using the AND(&) operator:
To solve the problem follow the below idea:

If we subtract a power of 2 numbers by 1 then all unset bits after the only set bit become set; and the set bit becomes unset.
For example for 4 ( 100) and 16(10000), we get the following after subtracting 1 
3 –> 011 
15 –> 01111

So, if a number n is a power of 2 then bitwise & of n and n-1 will be zero. We can say n is a power of 2 or not based on the value of n&(n-1). The expression n&(n-1) will not work when n is 0. To handle this case also, our expression will become n& (!n&(n-1)) (thanks to https://www.geeksforgeeks.org/program-to-find-whether-a-no-is-power-of-two/Mohammad for adding this case). 

// C++ program for the above approach
#include <bits/stdc++.h>
using namespace std;
 
/* Function to check if x is power of 2*/
bool isPowerOfTwo(int x)
{
    /* First x in the below expression is for the case when x is 0 */
    return x && (!(x & (x - 1)));
}
 
// Driver code
int main()
{
    // Function call
    isPowerOfTwo(31) ? cout << "Yes\n" : cout << "No\n";
    isPowerOfTwo(64) ? cout << "Yes\n" : cout << "No\n";
    return 0;
}
 
Output
No
Yes
Time Complexity: O(1)
Auxiliary Space: O(1)

Using the AND(&) and NOT(~) operator:
To solve the problem follow the below idea:

Another way is to use the logic to find the rightmost bit set of a given number and then check if (n & (~(n-1))) is equal to n or not

// C++ program of the above approach
#include <bits/stdc++.h>
using namespace std;
 
/* Function to check if x is power of 2*/
bool isPowerofTwo(long long n)
{
    if (n == 0)
        return 0;
    if ((n & (~(n - 1))) == n)
        return 1;
    return 0;
}
 
// Driver code
int main()
{
    // Function call
    isPowerofTwo(30) ? cout << "Yes\n" : cout << "No\n";
    isPowerofTwo(128) ? cout << "Yes\n" : cout << "No\n";
    return 0;
}
Output
No
Yes
Time complexity: O(1)
Auxiliary Space: O(1) 

Find whether a given number is a power of 2 using Brian Kernighan’s algorithm:
To solve the problem follow the below idea:

As we know that the number which will be the power of two have only one set bit , therefore when we do bitwise AND with the number which is just less than the number which can be represented as the power of (2) then the result will be 0 . 

Example : 4 can be represented as (2^2 ) , 
                (4 & 3)=0  or in binary (100 & 011=0)

// C++ program of the above approach
#include <bits/stdc++.h>
using namespace std;
 
/* Function to check if x is power of 2*/
bool isPowerofTwo(long long n)
{
    return (n != 0) && ((n & (n - 1)) == 0);
}
 
// Driver code
int main()
{
    // Function call
    isPowerofTwo(30) ? cout << "Yes\n" : cout << "No\n";
    isPowerofTwo(128) ? cout << "Yes\n" : cout << "No\n";
    return 0;
}
Output
No
Yes
Time Complexity: O(1) 
Auxiliary Space: O(1)

Find position of the only set bit	
--------------------------------------------
Given a number N having only one ‘1’ and all other ’0’s in its binary representation, find position of the only set bit. If there are 0 or more than 1 set bit the answer should be -1. Position of set bit ‘1’ should be counted starting with 1 from the LSB side in the binary representation of the number.

Examples:-

Input:
N = 2
Output:
2
Explanation:
2 is represented as "10" in Binary.
As we see there's only one set bit
and it's in Position 2 and thus the
Output 2.

Input:
N = 5
Output:
-1
Explanation:
5 is represented as "101" in Binary.
As we see there's two set bits
and thus the Output -1.
The idea is to start from the rightmost bit and one by one check value of every bit. Following is a detailed algorithm.
1) If number is power of two then and then only its binary representation contains only one ‘1’. That’s why check whether the given number is a power of 2 or not. If given number is not a power of 2, then print error message and exit.
2) Initialize two variables; i = 1 (for looping) and pos = 1 (to find position of set bit)
3) Inside loop, do bitwise AND of i and number ‘N’. If value of this operation is true, then “pos” bit is set, so break the loop and return position. Otherwise, increment “pos” by 1 and left shift i by 1 and repeat the procedure. 

// C++ program to find position of only set bit in a given number
#include <bits/stdc++.h>
using namespace std;
 
// A utility function to check whether n is a power of 2 or not.
int isPowerOfTwo(unsigned n)
{
    return n && (!(n & (n - 1)));
}
 
// Returns position of the only set bit in 'n'
int findPosition(unsigned n)
{
    if (!isPowerOfTwo(n))
        return -1;
 
    unsigned i = 1, pos = 1;
 
// Iterate through bits of n till we find a set bit i&n will be non-zero only when 'i' and 'n' have a set bit at same position
    while (!(i & n)) {
        // Unset current bit and set the next bit in 'i'
        i = i << 1;
 
        // increment position
        ++pos;
    }
 
    return pos;
}
 
// Driver program to test above function
int main(void)
{
    int n = 16;
    int pos = findPosition(n);
    (pos == -1) ? cout << "n = " << n << ", Invalid number" << endl : cout << "n = " << n << ", Position " << pos << endl;
 
    n = 12;
    pos = findPosition(n);
    (pos == -1) ? cout << "n = " << n << ", Invalid number" << endl : cout << "n = " << n << ", Position " << pos << endl;
 
    n = 128;
    pos = findPosition(n);
    (pos == -1) ? cout << "n = " << n << ", Invalid number" << endl : cout << "n = " << n << ", Position " << pos << endl;
 
    return 0;
}
 
Output : 
n = 16, Position 5
n = 12, Invalid number
n = 128, Position 8
Time Complexity: O(log2n), where n is the given number
Space Complexity: O(1)

Following is another method for this problem. The idea is to one by one right shift the set bit of the given number ‘n’ until ‘n’ becomes 0. Count how many times we shifted to make ‘n’ zero. The final count is the position of the set bit. 

// C++ program to find position of only set bit in a given number
#include <bits/stdc++.h>
using namespace std;
 
// A utility function to check whether n is power of 2 or not
int isPowerOfTwo(unsigned n)
{
    return n && (!(n & (n - 1)));
}
 
// Returns position of the only set bit in 'n'
int findPosition(unsigned n)
{
    if (!isPowerOfTwo(n))
        return -1;
 
    unsigned count = 0;
 
    // One by one move the only set bit to right till it reaches end
    while (n)
    {
        n = n >> 1;
 
        // increment count of shifts
        ++count;
    }
 
    return count;
}
 
// Driver code
int main(void)
{
    int n = 0;
    int pos = findPosition(n);
    (pos == -1) ? cout<<"n = "<<n<<", Invalid number\n" :
                    cout<<"n = "<<n<<", Position "<< pos<<endl;
 
    n = 12;
    pos = findPosition(n);
    (pos == -1) ? cout<<"n = "<<n<<", Invalid number\n" :
               cout<<"n = "<<n<<", Position "<< pos<<endl;
 
    n = 128;
    pos = findPosition(n);
    (pos == -1) ? cout<<"n = "<<n<<", Invalid number\n" :
                cout<<"n = "<<n<<", Position "<< pos<<endl;
 
    return 0;
}
 
Output : 
n = 0, Invalid number
n = 12, Invalid number
n = 128, Position 8
Time Complexity: O(log2n), where n is the given number
Space Complexity: O(1)

Copy set bits in a range	
----------------------------------------
Given two numbers x and y, and a range [l, r] where 1 <= l, r <= 32. The task is consider set bits of y in range [l, r] and set these bits in x also.
Examples : 

Input  : x = 10, y = 13, l = 2, r = 3
Output : x = 14
Binary representation of 10 is 1010 and 
that of y is 1101. There is one set bit
in y at 3'rd position (in given range). 
After we copy this bit to x, x becomes 1110
which is binary representation of 14.

Input  : x = 8, y = 7, l = 1, r = 2
Output : x = 11

Method 1 (One by one copy bits) 
We can one by one find set bits of y by traversing given range. For every set bit, we OR it to existing bit of x, so that the becomes set in x, if it was not set. Below is C++ implementation.

// C++ program to rearrange array in alternating
// C++ program to copy set bits in a given
// range [l, r] from y to x.
#include <bits/stdc++.h>
using namespace std;
 
// Copy set bits in range [l, r] from y to x.
// Note that x is passed by reference and modified by this function.
void copySetBits(unsigned &x, unsigned y,
                 unsigned l, unsigned r)
{
   // l and r must be between 1 to 32
   // (assuming ints are stored using 32 bits)
   if (l < 1 || r > 32)
      return ;
 
   // Traverse in given range
   for (int i=l; i<=r; i++)
   {
       // Find a mask (A number whose only set bit is at i'th position)
       int mask = 1 << (i-1);
 
       // If i'th bit is set in y, set i'th bit in x also.
       if (y & mask)
          x = x | mask;
   }
}
 
// Driver code
int main()
{
   unsigned x = 10, y = 13, l = 1, r = 32;
   copySetBits(x, y, l, r);
   cout << "Modified x is " << x;
   return 0;
}
Output
Modified x is 15
Time Complexity: O(r)
Auxiliary Space: O(1)

Method 2 (Copy all bits using one bit mask)
 
// C++ program to copy set bits in a given range [l, r] from y to x.
#include <bits/stdc++.h>
using namespace std;
 
// Copy set bits in range [l, r] from y to x.
//Note that x is passed by reference and modifiedby this function.
void copySetBits(unsigned &x, unsigned y,
                 unsigned l, unsigned r)
{
    // l and r must be between 1 to 32
    if (l < 1 || r > 32)
        return ;
 
    // get the length of the mask
    int maskLength = (1ll<<(r-l+1)) - 1;
 
// Shift the mask to the required position "&" with y to get the set bits at between l ad r in y
    int mask = ((maskLength)<<(l-1)) & y ;
    x = x | mask;
}
 
// Driver code
int main()
{
   unsigned x = 10, y = 13, l = 2, r = 3;
   copySetBits(x, y, l, r);
   cout << "Modified x is " << x;
   return 0;
}
Output
Modified x is 14
Time Complexity: O(1)
Auxiliary Space: O(1)

Divide two integers without using multiplication, division and mod operator	
-----------------------------------------------------------------------------
Given two integers say a and b. Find the quotient after dividing a by b without using multiplication, division, and mod operator.

Example: 

Input : a = 10, b = 3
Output : 3

Input : a = 43, b = -8
Output :  -5 

Approach: Keep subtracting the divisor from the dividend until the dividend becomes less than the divisor. The dividend becomes the remainder, and the number of times subtraction is done becomes the quotient. Below is the implementation of the above approach : 


// C++ implementation to Divide two integers without using multiplication,division and mod operator
#include <bits/stdc++.h>
using namespace std;
 
// Function to divide a by b and
// return floor value of the result
long long divide(long long dividend, long long int divisor)
{
 
    // Calculate sign of divisor i.e., sign will be negative only if either one of them is negative
    // otherwise it will be positive
    long long sign = ((dividend < 0) ^ (divisor < 0)) ? -1 : 1;
 
    // Update both divisor and dividend positive
    dividend = abs(dividend);
    divisor = abs(divisor);
 
    // Initialize the quotient
    long long quotient = 0;
    while (dividend >= divisor) {
        dividend -= divisor;
        ++quotient;
    }
 
    // Return the value of quotient with the appropriate sign.
    return quotient * sign;
}
 
// Driver code
int main()
{
    int a = -2147483648, b = -1;
    cout << divide(a, b) << "\n";
 
    a = 43, b = -8;
    cout << divide(a, b);
 
    return 0;
}
Output
3
-5
Time complexity : O(a/b) 
Auxiliary space : O(1)

Efficient Approach: Use bit manipulation in order to find the quotient. The divisor and dividend can be written as 

dividend = quotient * divisor + remainder

As every number can be represented in base 2(0 or 1), represent the quotient in binary form by using the shift operator as given below: 

Determine the most significant bit in the divisor. This can easily be calculated by iterating on the bit position i from 31 to 1.
Find the first bit for which divisor << i is less than dividend and keep updating the ith bit position for which it is true.
Add the result in the temp variable for checking the next position such that (temp + (divisor << i) ) is less than the dividend.
Return the final answer of the quotient after updating with a corresponding sign.
Below is the implementation of the above approach :  


// C++ implementation to Divide two integers without using multiplication,division and mod operator
#include <bits/stdc++.h>
using namespace std;
 
// Function to divide a by b and
// return floor value it
long long divide(long long dividend, long long divisor) {
 
  // Calculate sign of divisor i.e.,sign will be negative only if either one of them is negative otherwise it will be positive
  int sign = ((dividend < 0) ^
              (divisor < 0)) ? -1 : 1;
 
  // remove sign of operands
  dividend = abs(dividend);
  divisor = abs(divisor);
 
  // Initialize the quotient
  long long quotient = 0, temp = 0;
 
  // test down from the highest bit and accumulate the tentative value for valid bit
  for (int i = 31; i >= 0; --i) {
 
    if (temp + (divisor << i) <= dividend) {
      temp += divisor << i;
      quotient |= 1LL << i;
    }
  }
  //if the sign value computed earlier is -1 then negate the value of quotient
  if(sign==-1) quotient=-quotient;
   
  return quotient;
}
 
// Driver code
int main() {
  int a = -2147483648, b = -1;
  cout << divide(a, b) << "\n";
 
  a = 43, b = -8;
  cout << divide(a, b);
 
  return 0;
}
Output
 3
-5
Time complexity : O(log(a)) 
Auxiliary space : O(1)

Another Efficient Approach : Using the Logarithms

Basic Idea : a/b = e ln(a) / e ln(b) = e( ln(a) – ln(b) )

#include <bits/stdc++.h>
using namespace std;
long long int divide(long long int dividend, long long int divisor)
{
    if (dividend == 0)
        return 0;
    if (divisor == 0)
    {
        cout << "Division by 0 is impossible\n";
        return 0;
    }
 
// Calculate sign of answer i.e., Sign will be negative only if Either one of them is negative Otherwise it will be positive
    long long int sign = (dividend < 0) ^ (divisor < 0);
 
    // abs() : function used to get the absolute values
    dividend = abs(dividend);
    divisor = abs(divisor);
    if (divisor == 1)
        return ((sign == 0) ? dividend : -dividend);
 
    // log() : function used to get the logarithmic value of the entered value [Gives the natural log of the entered number]
    // exp() : Return the e^(entered value)
    long long int ans = exp(log(dividend) - log(divisor)) + 0.0000000001;
    /*
     adding 0.0000000001 to compensate for the precision errors
     like for a = 18 and b = -6,
     result after exponentiation will be 2.999999999...
     adding 0.0000000001, sets it right
    */
    return ((sign == 0) ? ans : -ans);
}
int main()
{
    int a = 10, b = 3;
    cout << divide(a, b) << '\n';
    a = 41, b = -8;
    cout << divide(a, b) << '\n';
    return 0;
}

Output
 3
-5

Calculate square of a number without using *, / and pow()	
-----------------------------------------------------------
Examples : 

Input: n = 5
Output: 25

Input: 7
Output: 49

Input: n = 12
Output: 144

A Simple Solution is to repeatedly add n to result. 

// Simple solution to calculate square without using * and pow()
#include <iostream>
using namespace std;
 
int square(int n)
{
    // handle negative input
    if (n < 0)
        n = -n;
 
    // Initialize result
    int res = n;
 
    // Add n to res n-1 times
    for (int i = 1; i < n; i++)
        res += n;
 
    return res;
}
 
// Driver code
int main()
{
    for (int n = 1; n <= 5; n++)
        cout << "n = " << n << ", n^2 = " << square(n)
             << endl;
    return 0;
}
Output
n = 1, n^2 = 1
n = 2, n^2 = 4
n = 3, n^2 = 9
n = 4, n^2 = 16
n = 5, n^2 = 25
Time Complexity: O(n)
Auxiliary Space: O(1)

Approach 2:

We can do it in O(Logn) time using bitwise operators. The idea is based on the following fact.

  square(n) = 0 if n == 0
  if n is even 
     square(n) = 4*square(n/2) 
  if n is odd
     square(n) = 4*square(floor(n/2)) + 4*floor(n/2) + 1 

Examples
  square(6) = 4*square(3)
  square(3) = 4*(square(1)) + 4*1 + 1 = 9
  square(7) = 4*square(3) + 4*3 + 1 = 4*9 + 4*3 + 1 = 49

How does this work? 

If n is even, it can be written as
  n = 2*x 
  n2 = (2*x)2 = 4*x2
If n is odd, it can be written as 
  n = 2*x + 1
  n2 = (2*x + 1)2 = 4*x2 + 4*x + 1
floor(n/2) can be calculated using a bitwise right shift operator. 2*x and 4*x can be calculated 

Below is the implementation based on the above idea. 


// Square of a number using bitwise operators
#include <bits/stdc++.h>
using namespace std;
 
int square(int n)
{
    // Base case
    if (n == 0)
        return 0;
 
    // Handle negative number
    if (n < 0)
        n = -n;
 
    // Get floor(n/2) using right shift
    int x = n >> 1;
 
    // If n is odd
    if (n & 1)
        return ((square(x) << 2) + (x << 2) + 1);
    else // If n is even
        return (square(x) << 2);
}
 
// Driver Code
int main()
{
    // Function calls
    for (int n = 1; n <= 5; n++)
        cout << "n = " << n << ", n^2 = " << square(n)
             << endl;
    return 0;
}
Output

n = 1, n^2 = 1
n = 2, n^2 = 4
n = 3, n^2 = 9
n = 4, n^2 = 16
n = 5, n^2 = 25
Time Complexity: O(logn)
Auxiliary Space: O(1)

Approach 3:

For a given number `num` we get square of it by multiplying number as `num * num`. 
Now write one of `num` in square `num * num` in terms of power of `2`. Check below examples.

Eg: num = 10, square(num) = 10 * 10 
                          = 10 * (8 + 2) = (10 * 8) + (10 * 2)
    num = 15, square(num) = 15 * 15 
                          = 15 * (8 + 4 + 2 + 1) = (15 * 8) + (15 * 4) + (15 * 2) + (15 * 1)

Multiplication with power of 2's can be done by left shift bitwise operator.
Below is the implementation based on the above idea. 


// Simple solution to calculate square without using * and pow()
#include <iostream>
using namespace std;
 
int square(int num)
{
    // handle negative input
    if (num < 0) num = -num;
 
    // Initialize result
    int result = 0, times = num;
 
    while (times > 0)
    {
        int possibleShifts = 0, currTimes = 1;
 
        while ((currTimes << 1) <= times)
        {
            currTimes = currTimes << 1;
            ++possibleShifts;
        }
 
        result = result + (num << possibleShifts);
        times = times - currTimes;
    }
 
    return result;
}
 
// Driver code
int main()
{
    // Function calls
    for (int n = 10; n <= 15; ++n)
        cout << "n = " << n << ", n^2 = " << square(n) << endl;
    return 0;
}

Output
n = 10, n^2 = 100
n = 11, n^2 = 121
n = 12, n^2 = 144
n = 13, n^2 = 169
n = 14, n^2 = 196
n = 15, n^2 = 225
Time Complexity: O(logn)
Auxiliary Space: O(1)

Power Set	
------------------------------------------------
Power Set: Power set P(S) of a set S is the set of all subsets of S. For example S = {a, b, c} then P(s) = {{}, {a}, {b}, {c}, {a,b}, {a, c}, {b, c}, {a, b, c}}.
If S has n elements in it then P(s) will have 2n elements

Example: 

Set  = [a,b,c]
power_set_size = pow(2, 3) = 8
Run for binary counter = 000 to 111

Value of Counter            Subset
   000                    -> Empty set
   001                    -> a
   010                    -> b
   011                    -> ab
   100                    -> c
   101                    -> ac
   110                    -> bc
   111                    -> abc

Algorithm: 

Input: Set[], set_size
1. Get the size of power set
      powet_set_size = pow(2, set_size)
2  Loop for counter from 0 to pow_set_size
    (a) Loop for i = 0 to set_size
         (i) If ith bit in counter is set
                Print ith element from set for this subset
   (b) Print separator for subsets i.e., newline

Method 1:
For a given set[] S, the power set can be found by generating all binary numbers between 0 and 2n-1, where n is the size of the set. 
For example, for the set S {x, y, z}, generate all binary numbers from 0 to 23-1 and for each generated number, the corresponding set can be found by considering set bits in the number.

// C++ program for the above approach
#include <bits/stdc++.h>
using namespace std;
 
// Function to print all the power set
void printPowerSet(char* set, int set_size)
{
    // Set_size of power set of a set with set_size
    // n is (2^n-1)
    unsigned int pow_set_size = pow(2, set_size);
    int counter, j;
 
    // Run from counter 000..0 to 111..1
    for (counter = 0; counter < pow_set_size; counter++) {
        for (j = 0; j < set_size; j++) {
            // Check if jth bit in the counter is set
            // If set then print jth element from set
            if (counter & (1 << j))
                cout << set[j];
        }
        cout << endl;
    }
}
 
/*Driver code*/
int main()
{
    char set[] = { 'a', 'b', 'c' };
    printPowerSet(set, 3);
    return 0;
}
 
Output
a
b
ab
c
ac
bc
abc
Time Complexity: O(n2n)
Auxiliary Space: O(1)

Method 2: (sorted by cardinality)

In auxiliary array of bool set all elements to 0. That represent an empty set. Set first element of auxiliary array to 1 and generate all permutations to produce all subsets with one element. Then set the second element to 1 which will produce all subsets with two elements, repeat until all elements are included.

// C++ program for the above approach
#include <bits/stdc++.h>
using namespace std;
 
// Function to print all the power set
void printPowerSet(char set[], int n)
{
    bool *contain = new bool[n]{0};
     
    // Empty subset
    cout << "" << endl;
    for(int i = 0; i < n; i++)
    {
        contain[i] = 1;
        // All permutation
        do
        {
            for(int j = 0; j < n; j++)
                if(contain[j])
                    cout << set[j];
            cout << endl;
        } while(prev_permutation(contain, contain + n));
    }
}
 
/*Driver code*/
int main()
{
    char set[] = {'a','b','c'};
    printPowerSet(set, 3);
    return 0;
}
 
Output
a
b
c
ab
ac
bc
abc
Time Complexity: O(n2n)
Auxiliary Space: O(n)

Method 3:

We can use backtrack here, we have two choices first consider that element then don’t consider that element. 

#include <bits/stdc++.h>
using namespace std;
 
void findPowerSet(char* s, vector<char> &res, int n){
        if (n == 0) {
            for (auto i: res)
              cout << i;
            cout << "\n";
            return;
             
        }
         res.push_back(s[n - 1]);
         findPowerSet(s, res, n - 1);
         res.pop_back();                   
         findPowerSet(s, res, n - 1);
    }
     
void printPowerSet(char* s, int n){
    vector<char> ans;
    findPowerSet(s, ans, n);
}
 
 
int main()
{
    char set[] = { 'a', 'b', 'c' };
    printPowerSet(set, 3);
    return 0;
}
Output
cba
cb
ca
c
ba
b
a
Time Complexity: O(n2^n)
Space Complexity: O(n)
