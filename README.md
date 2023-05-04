#include <iostream>
using namespace std;

// function to heapify the tree
void heapify(int arr[], int n, int root)
{
   int largest = root;
    int a = 2 * root + 1;
    int b = 2 * root + 2;


    if (a < n && arr[a] > arr[largest])
        largest = a;


    if (b < n && arr[b] > arr[largest])
        largest = b;


    if (largest != root) {
        swap(arr[root], arr[largest]);


        heapify(arr, n, largest);
    }


}

// implementing heap sort
void heapSort(int arr[], int n)
{
   for (int j = n / 2 - 1; j >= 0; j--)
        heapify(arr, n, j);


    for (int j = n - 1; j >= 0; j--) {

        swap(arr[0], arr[j]);


        heapify(arr, j, 0);
    }

}

/* print contents of array */
void displayArray(int arr[], int n)
{
   for (int i=0; i<n; ++i)
   cout << arr[i] << " ";
   cout << "\n";
}

// main program
int main()
{
   int heap_arr[] = {4,17,3,12,9,6};
   int n = sizeof(heap_arr)/sizeof(heap_arr[0]);
   cout<<"Input array"<<endl;
   displayArray(heap_arr,n);

   heapSort(heap_arr, n);

   cout << "Sorted array"<<endl;
   displayArray(heap_arr, n);
}
