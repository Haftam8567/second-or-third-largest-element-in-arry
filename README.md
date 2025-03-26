# second-or-third-largest-element in arry
clude <iostream>

using namespace std;

int findKthLargest(int arr[], int n, int k) {
    if (n < k) {
        cout << "Array size is too small." << endl;
        return -1; 
    }

    int first = INT_MIN, second = INT_MIN, third = INT_MIN;

    
    for (int i = 0; i < n; i++) {
        if (arr[i] > first) {
            third = second;
            second = first;
            first = arr[i];
        } else if (arr[i] > second && arr[i] != first) {
            third = second;
            second = arr[i];
        } else if (arr[i] > third && arr[i] != second) {
            third = arr[i];
        }
    }

    if (k == 2) return second;
    if (k == 3) return third;

    return -1;  
}

int main() {
    int arr[] = {10, 5, 8, 12, 15};
    int n = sizeof(arr) / sizeof(arr[0]);

    cout << "Second largest: " << findKthLargest(arr, n, 2) << endl;
    cout << "Third largest: " << findKthLargest(arr, n, 3) << endl;

    return 0;
}
