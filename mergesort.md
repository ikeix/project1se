```cadence
void merge(int arr[], int L, int m, int R, int size)
{
    int i = L;
    int j = m + 1;
    int k = L;
    int *temp = new int[size];
    while (i <= m && j <= R) {
        if (arr[i] <= arr[j]) {
            temp[k] = arr[i];
            i++;
            k++;
        }
        else {
            temp[k] = arr[j];
            j++;
            k++;
        }
    }
    while (i <= m) {
        temp[k] = arr[i];
        i++;
        k++;
    }
    while (j <= R) {
        temp[k] = arr[j];
        j++;
        k++;
    }
    for (int p = L; p <= R; p++) {
        arr[p] = temp[p];
    }
}
void mergeSort(int arr[], int l, int R, int size)
{
    if (l < R) {
        int m = (l + R) / 2;
        mergeSort(arr, l, m, size);
        mergeSort(arr, m + 1, R, size);
        merge(arr, l, m, R, size);
    }
}
int main()
{
    cout << "Enter size of array: " << endl;
    int size;
    cin >> size;
    int *myarray = new int [size];
    cout << "Enter " << size << " integers in any order: " << endl;
    for (int i = 0; i < size; i++) {
        cin >> myarray[i];
    }
    cout << "Before Sorting" << endl;
    for (int i = 0; i < size; i++) {
        cout << myarray[i] << " ";
    }
    cout << endl;
    mergeSort(myarray, 0, (size - 1), size);
    cout << "After Sorting" << endl;
    for (int i = 0; i < size; i++) {
        cout << myarray[i] << " ";
    }
    cout << endl;
    system("pause");
    return 0;
}
```
