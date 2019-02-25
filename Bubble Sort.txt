#include<iostream>
//#include<algorithm>
using namespace std;
void bubbleSort(int arr[], int n)
{
	bool flag = true; 
	int c = 0;
	for (int i = 0; i < n - 1; i++)
	{
		for (int j = 0; j < n - i - 1; j++)
		{
			if (arr[j] > arr[j + 1])
			{
				swap(arr[j], arr[j + 1]);
				flag = false;
			}
			c++;
		}
		if (flag == true)
			break;

	}
	cout << "# of rounds :" << c << endl;
}
/*
void bubbleSortRec(int arr[], int n)
{
	  
	if (n == 1)//base case
		return;

for (int i = 0; i < n - 1; i++)
		if (arr[i] > arr[i + 1])
		swap(arr[i], arr[i + 1]);
	
bubbleSortRec(arr, n - 1);
}
*/

void printArray(int arr[], int n)
{
	for (int i = 0; i < n; i++)
		cout << arr[i] << " ";
	cout << endl;
}



int main()
{

	int arr[] = { 30,20,40,5,60,2 };
	int n = sizeof(arr) / sizeof(arr[0]);//24/4=6
	bubbleSort(arr, n);
	//bubbleSortRec(arr, n);
	printArray(arr, n);
	return 0;

}

