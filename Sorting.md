# Sorting 

### 1.   WAP in C to sort an array of integers using Bubble sort. 

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

### 2.   WAP in C to sort an array of integers using Selection sort.

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

### 3.   WAP in C to sort an array of integers using Insertion sort. 

> Source Code

```c
#include <stdio.h>
void insertion_sort(int arr[], int size);

int main() {
    int arr[5]={80,30,24,35,22};
    insertion_sort(arr, 5);
    return 0;
}



void insertion_sort(int arr[], int size)
 {
    int temp, i, j;
    for (i = 1; i < size; i++) {
        temp = arr[i];
        j = i - 1;
        while (j >= 0 && arr[j] > temp) {
            arr[j + 1] = arr[j];
            j = j - 1;
        }
        arr[j + 1] = temp;
    }
    printf("\nInsertion Sort in Ascending Order :  ");
    for (i = 0; i < size; i++) {
        printf(" %d", arr[i]);
    }
}


```

<br>

### 4.   WAP in C to sort an array of integers using Quick sort. 

> Source Code

```c
#include<stdio.h>
void quick_sort(int arr[],int lb,int ub);
int partition(int arr[],int lb, int ub);

void swap(int *p,int *q) 
{ 
    int temp; 
    temp = *p; 
    *p = *q; 
    *q = temp; 
}

int main() { 
    int arr[5]={80,30,24,35,22}, num=5, i;

    quick_sort(arr,0,num-1); 
    printf("\n Quick Sort in Asending Oreder :  "); 
    for(i=0;i<num;i++) 
    { 
        printf(" %d",arr[i]); 
    } 
    return 0; 
} 


int partition(int arr[],int lb, int ub)
 { 
    int pivot = arr[lb]; 
    int start=lb,end=ub; 
    while(start<end) { 
        while(arr[start] <= pivot) 
            start++; 
        while(arr[end]>pivot) 
            end--; 
        if(start<end) 
            swap(&arr[start],&arr[end]); 
    } 
    swap(&arr[lb],&arr[end]); 
    return end; 
} 



void quick_sort(int arr[],int lb,int ub)
 { 
    if(lb<ub) { 
        int loc = partition(arr,lb,ub); 
        quick_sort(arr,lb,loc-1); 
        quick_sort(arr,loc+1,ub); 
    } 
}
```

<br>

### 5.   WAP in C to sort an array of integers using Merge sort. 

> Source Code

```c
#include<stdio.h>
void merge(int arr[],int mid,int low,int high);
void merging_sort(int arr[],int low, int high);


int main()
{
    
int arr[5]={80,30,24,35,22}, num=5, i;

merging_sort(arr,0,num-1);
printf("\n Merge Sort in Asending Oreder----> ");
for(i=0;i<num;i++)
{
printf("%d ",arr[i]);
}
return 0;
}





void merge(int arr[],int mid,int low,int high)
{
    int Temp_arr[high];
    int i = low, j = mid+1, k = low;
    while(i<=mid && j<=high)
    {
        if(arr[i] < arr[j])
        {
            Temp_arr[k] = arr[i];
            i++;
            k++;
        }
        else{
            Temp_arr[k] = arr[j];
            j++;
            k++;
        }
    }

while(i<=mid)
{
    Temp_arr[k] = arr[i];
    i++;
    k++;
}

while(j<=high)
{
    Temp_arr[k] = arr[j];
    k++;
    j++;
}

for(i = low; i<=high; i++)
{
    arr[i] = Temp_arr[i];
}
}





void merging_sort(int arr[],int low, int high)
{
    int mid;
    if(low < high)
    {
        mid = (low + high) / 2;
        merging_sort(arr,low,mid);
        merging_sort(arr,mid+1,high);
        merge(arr,mid,low,high);
    }
}

```

<br>

### 6.   WAP in C to sort an array of integers using Shell sort. 

> Source Code

```c
#include<stdio.h>
void shell_sort(int arr[],int size);


int main()
{
    int arr[5]={80,30,24,35,22};

    shell_sort(arr,5);
    return 0;
}




void shell_sort(int arr[],int size)
{
  int i,j,temp;
    for(int gap=size/2; gap>0; gap/=2)
    {
        for(i=gap; i<size; i++)
        {
            temp = arr[i];
            j=i;
            while(j>=gap && arr[j-gap]>temp)
            {
                arr[j] = arr[j-gap];
                j=j-gap;
            }
            arr[j] = temp;
        }
    }
printf("\n Shell Sort in Ascending Order :--> ");

for(i=0;i<size;i++)
{
printf("%d ",arr[i]);
}
}
```

<br>



