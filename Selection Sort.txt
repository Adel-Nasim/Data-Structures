#include <iostream>
#include<algorithm>
using namespace std;
void selectionSort(int arr[], int n)
{
	int minIdx;
	                               //0  1  2  3  4  5
	for (int i = 0; i < n - 1; i++)//60 40 50 30 10 20
	{	
		minIdx = i;//4
    
		for (int j = i + 1; j < n; j++)
			if (arr[j] > arr[minIdx])
				minIdx = j;
	            swap(arr[minIdx], arr[i]);
	
	}
}
/*
//\\//\\//\\//\\//\\Recursive//\\//\\//\\//\\//\\//\\
int minIndex(int a[], int i, int j)
{
	if (i == j)
		return i;

	int k = minIndex(a, i + 1, j);

	return (a[i] < a[k]) ? i : k;
}



void recurSelectionSort(int a[], int n, int index = 0)
{

	if (index == n)
		return;

	int k = minIndex(a, index, n - 1);

	if (k != index)
		swap(a[k], a[index]);

	recurSelectionSort(a, n, index + 1);
}

*/


void print(int arr[], int size)
{

	for (int i = 0; i < size; i++)
		cout << arr[i] << " ";
	cout << endl;

}

int main()
{
	int arr[] = { -60, 0, 50, 30, 10,20 };
	int n = sizeof(arr) / sizeof(arr[0]);//6*4=24  /  4
	selectionSort(arr, n);
   //recurSelectionSort(arr, n);
	cout<<"Array After Selection Sort : \n";
	print(arr, n);

	return 0;
	}

