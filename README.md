Common elements in all row of a given matrix in C++
Here, in this page we will discuss the program to find the common elements in all row of a given matrix in C++ Programming language. We will discuss various methods to solve the given problem.

Common elements in all row of a given matrix in C++
Method Discussed :
Method 1 : Naive Approach
Method 2 : Using Hash-map
Let’s discuss them one by one in brief,

Method 1:
In this method we will check for every element that, if it is present in other rows or not.

Time and Space Complexity :
Time complexity: O(N*M)
Space complexity: O(1)
Method 1 : Code in C++
Run
#include <bits/stdc++.h>
using namespace std;
#define N 5

int findMaxValue(int mat[][N])
{
    int maxValue = INT_MIN;

    for (int a = 0; a < N - 1; a++)
    for (int b = 0; b < N - 1; b++)
        for (int d = a + 1; d < N; d++)
        for (int e = b + 1; e < N; e++)
            if (maxValue < (mat[d][e] - mat[a][b]))
                maxValue = mat[d][e] - mat[a][b];
 
    return maxValue;
}
 
int main()
{
int mat[N][N] = {
                { 1, 2, -1, -4, -20 },
                { -8, -3, 4, 2, 1 },
                { 3, 8, 6, 1, 3 },
                { -4, -1, 1, 7, -6 },
                { 0, -4, 10, -5, 1 }
            };
    cout << "Maximum Value is " << findMaxValue(mat);
 
    return 0;
}
Output :
Maximum Value is 18
Method 2:
Initially insert all elements of the first row in an map.
For every other element in remaining rows, we check if it is present in the map.
If it is present in the map and is not duplicated in current row, we increment count of the element in map by 1, else we ignore the element.
If the currently traversed row is the last row, we print the element if it has appeared m-1 times before.
Time and Space Complexity :
Time complexity: O(M*N)
Space complexity: O(N)
Method 2 : Code in C++
Run
#include <bits/stdc++.h>
using namespace std;
#define M 4
#define N 5
 
void printCommonElements(int mat[M][N])
{
    unordered_map<int, int> mp;
 
    for (int j = 0; j < N; j++)
        mp[mat[0][j]] = 1;
 
    for (int i = 1; i < M; i++)
    {
        for (int j = 0; j < N; j++)
        {
            if (mp[mat[i][j]] == i)
            {
                mp[mat[i][j]] = i + 1;
 
                if (i==M-1 && mp[mat[i][j]]==M)
                  cout << mat[i][j] << " ";
            }
        }
    }
}
 
int main()
{
    int mat[M][N] =
    {
        {10, 20, 10, 40, 80},
        {30, 70, 80, 50, 10},
        {80, 70, 70, 30, 10},
        {80, 10, 20, 70, 90},
    };
 
    printCommonElements(mat);
 
    return 0;
} 
Output :
80 10
