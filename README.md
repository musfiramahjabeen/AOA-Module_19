# AOA-Module19

## Day 1 - Time and Space Complexity
### Write a python program to print the following pattern
```py
/*
5 4 3 2 1
5 4 3 2
5 4 3
5 4
5
/*
n=int(input())
k=n
for i in range(0,n):
    for j in range(i,n):
        print(k,end=" ")
        k=k-1
    k=n
    print()
```
### Write a python program to print the following pattern based on the given input.
```py
/*
1
2 2
3 3 3
4 4 4 4
5 5 5 5 5
/*
def pattern(n):
    for i in range(1,n):
        for j in range(0,i):
            print(i,end=" ")
        print()
n=int(input())
pattern(n)
```
### Write a Python Program to print the fibonacci series upto n_terms using Recursion.
```py
def recursive_fibonacci(n):
    if n<=1:
        return n
    return recursive_fibonacci(n-1)+recursive_fibonacci(n-2)

 
n_terms = int(input())
 
if n_terms <= 0:
  print("Invalid input ! Please input a positive value")
else:
  print("Fibonacci series:")
for i in range(n_terms):
    print(recursive_fibonacci(i))
```

## Day 2 - Merge Sort
### Write a python program to implement merge sort using iterative approach on the given list of  float values.
```py
def Merge_Sort(S):
    if len(S)<=1:
        return S
    mid=len(S)//2
    left=Merge_Sort(S[:mid])
    right=Merge_Sort(S[mid:])
    return merge(left,right)
    
def merge(left,right):
    sorted_array=[]
    i=j=0
    while(i<len(left) and j<len(right)):
        if left[i]<right[j]:
            sorted_array.append(left[i])
            i+=1
        else:
            sorted_array.append(right[j])
            j+=1
    sorted_array.extend(left[i:])
    sorted_array.extend(right[j:])
    return sorted_array
    
n=int(input())
S=[eval(input()) for i in range(n)]
print("The Original array is: ",S)
sorted_array=Merge_Sort(S)
print("Array after sorting is: ",sorted_array)
```
### Write a python program for the implementation of merge sort on the given list of values.
```py
def mergeSort(s):
    if len(s)<=1:
        return s
    mid=len(s)//2
    left=mergeSort(s[:mid])
    right=mergeSort(s[mid:])
    return merge(left,right)

def merge(left,right):
    i=j=0
    sorted_array=[]
    while i<len(left) and j<len(right):
        if left[i]<right[j]:
            sorted_array.append(left[i])
            i=i+1
        else:
            sorted_array.append(right[j])
            j=j+1
    sorted_array.extend(left[i:])
    sorted_array.extend(right[j:])
    return sorted_array

n=int(input())
s=[eval(input()) for i in range(n)]
res=mergeSort(s)
print("Given array is")
for i in range(n):
    print(s[i],end=" ")
print()
print("Sorted array is")
for i in range(n):
    print(res[i],end=" ")
print()
```
### Write a Python Program to find minimum number of swaps required to sort an array given by the user.
```py
def minSwaps(arr):
    temp=sorted(arr)
    pos={}
    for i in range(len(arr)):
        pos[arr[i]]=i
    swap=0
    for i in range(len(arr)):
        if temp[i]!=arr[i]:
            ind=pos[temp[i]]
            arr[i],arr[ind]=arr[ind],arr[i]
            pos[arr[i]]=i
            pos[arr[ind]]=ind
            swap+=1
    print(swap)
    ######### Add your code here #############3
arr = []  #[1, 5, 4, 3, 2]
n=int(input())
for i in range(n):
    arr.append(int(input()))
```
## Day 3 - Quick Sort
### Write a python program to implement the quick sort using recursion.
```py
def partition(arr,low,high):
    pivot = arr[high]
    print("pivot: ",pivot)
    i= low-1
    for j in range(low,high):
        if(arr[j] <=pivot):
            i+=1
            arr[i],arr[j] = arr[j],arr[i]
    arr[i+1],arr[high] = arr[high],arr[i+1]
    return i+1

def quickSort(arr,low,high):
    if(low<high):
        pi = partition(arr,low,high)
        quickSort(arr,low,pi-1)
        quickSort(arr,pi+1,high)

n = int(input())
arr = []
for i in range(n):
    arr.append(int(input()))
quickSort(arr,0,n-1)
print(arr)
```
### Write a python program to implement quick sort on the given array values.
```py
def qsort(L):
    if L == []:
        return []
    pivot = L[0:1]
    left = qsort([x for x in L[1:] if x < L[0]])
    right = qsort([x for x in L[1:] if x >= L[0]])
    print("left: ",left)
    print("right: ",right)
    return left + pivot + right

list1=[]
n=int(input())
for i in range(n):
    list1.append(int(input()))
print(qsort(list1))
```
### Write a Python program to sort unsorted numbers using Multi-key quicksort
```py
def quick_sort_3partition(sorting: list, left: int, right: int) -> None:
    if right <= left:
        return
    a = i = left
    b = right
    pivot = sorting[left]
    while i <= b:
        if sorting[i] < pivot:
            sorting[a], sorting[i] = sorting[i], sorting[a]
            a += 1
            i += 1
        elif sorting[i] > pivot:
            sorting[b], sorting[i] = sorting[i], sorting[b]
            b -= 1
        else:
            i += 1
    quick_sort_3partition(sorting, left, a - 1)
    quick_sort_3partition(sorting, b + 1, right)

def three_way_radix_quicksort(sorting: list) -> list:
    quick_sort_3partition(sorting, 0, len(sorting) - 1)
    return sorting

nums = []  # [4, 3, 5, 1, 2]
n = int(input())
for i in range(n):
    nums.append(int(input()))
print("Original list:")
print(nums)
print("After applying Random Pivot Quick Sort the said list becomes:")
sorted_nums = three_way_radix_quicksort(nums)
print(sorted_nums)
```
## Day 4 - Linear & Binary Search
### Write a python program to search an element in the given sorted using iterative binary search.
```py
def binarySearch(arr,left,right,target):
    while left<=right:
        mid=(left+right)//2
        if arr[mid]==target:
            return mid
        elif arr[mid]<target:
            left=mid+1
        elif arr[mid]>target:
            right=mid-1
    return -1
n=int(input())
arr=[int(input()) for i in range(n)]
x=int(input())
res=binarySearch(arr,0,len(arr)-1,x)
if res!=-1:
    print("Element is present at index ",res)
else:
    print("Element is not present in array")
```
### Write a python program to implement linear search on the given tuple.
```py
n=int(input())
tup=tuple(eval(input())for i in range(n))
target=int(input())
for i in range(len(tup)):
    if tup[i]==target:
        print(f"Tuple: {target} found")
        break
else:
        print(f"Tuple: {target} not found")
```
### Write a python program for a search function with parameter list name and the value to be searched.
```py
def search(lst, value):
    if value in lst:
        return "Found"
    else:
        return "Not Found"

# Example usage:
if __name__ == "__main__":
    List = []
    n=int(input())
    for i in range(n):
        List.append(input())
    n1 = input()
    result = search(List, n1)
    print(result)
```
