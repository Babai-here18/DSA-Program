# Sorting 

### 1.  WAP in C to sort an array of integers using Bubble sort. 

> Source Code

```c
 #include <stdio.h>
void bubble_sort(int arr[], int size);

int main() {
    int arr[5]={80,30,24,35,22};
    bubble_sort(arr, 5);
    return 0;
}


void bubble_sort(int arr[], int size)
 {
    int i, j, temp, flag;
    for (i = 0; i < size - 1; i++) {
        flag = 0;
        for (j = 0; j < size - 1 - i; j++) {
            if (arr[j] > arr[j + 1]) {
                temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
                flag = 1;
            }
        }

        if (flag == 0)
            break;
    }
    printf("\nBubble Sort in Ascending Order :  ");
    for (i = 0; i < size; i++) {
        printf(" %d", arr[i]);
    }
}
```

<br>

### 2.  WAP in C to sort an array of integers using Selection sort. . 

> Source Code

```c
#include <stdio.h>
void selection_sort(int arr[], int size);

int main() {

int arr[5]={80,30,24,35,22};
selection_sort(arr, 5);
return 0;

}


void selection_sort(int arr[], int size) 
{
    int i, min, j, temp;
    for (i = 0; i < size - 1; i++) {
        min = i;
        for (j = i + 1; j < size; j++) {
            if (arr[j] < arr[min])
                min = j;
        }
        if (min != i) {
            temp = arr[i];
            arr[i] = arr[min];
            arr[min] = temp;
        }
    }
    printf("\nSelection Sort method in Ascending Order : ");
    for (i = 0; i < size; i++) {
        printf(" %d", arr[i]);
    }
}

```

<br>



