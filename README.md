Merge two sorted arrays without using extra space in Java
Here, in this page we will discuss the program to Merge two sorted arrays without using extra space in Java . We are given two sorted arrays. We need to merge these two arrays such that the initial numbers (after complete sorting) are in the first array and the remaining numbers are in the second array. Extra space allowed in O(1).

Program to Merge two sorted arrays without using Extra space in Java
it becomes extremely complicated when extra space is not permitted and it does not appear possible in less than O(m*n) worst-case time. Though further improvements are possible,
The idea is to start with the last element of ar2[] and search for it in ar1[]. If ar1[] has a greater element, we move the last element of ar1[] to ar2[]. To keep ar1[] and ar2[] sorted, we must place the last element of ar2[] in the correct position in ar1[]. For this, we can use the Insertion Sort type of insertion.
Program to Merge two sorted arrays
note
Java program program to merge two sorted arrays with O(1) extra space.
Algorithm
Iterate through all of ar2[] starting with the last element. Do the following for each element ar2[I].
Save the final element of ar1[i]: final = ar1[I]
Loop from the last element of ar1[] until ar1[j] is greater than ar2[I].
ar1[j+1] = ar1[j] / Advance element by one position j—
If any ar1[] element was moved or (j!= m-1)
ar1[j+1] = ar2[I]
ar2[i] = final
Code in JAVA
Run
import java.util.Arrays;
public
class Main {
    static int arr1[] = new int[]{1, 12, 9, 3, 17, 20};
    static int arr2[] = new int[]{2, 3, 8, 13};
    static void merge(int m, int n) {
        // Iterate through all elements of ar2[] starting from
        // the last element
        for (int i = n - 1; i >= 0; i--) {
            int j, last = arr1[m - 1];
            for (j = m - 2; j >= 0 && arr1[j] > arr2[i]; j--) arr1[j + 1] = arr1[j];
            // If there was a greater element
            if (j != m - 2 || last > arr2[i]) {
                arr1[j + 1] = arr2[i];
                arr2[i] = last;
            }
        }
    }
    // Driver method to test the above function
    public
    static void main(String[] args) {
        merge(arr1.length, arr2.length);
        System.out.print("After Merging First Array: ");
        System.out.println(Arrays.toString(arr1));
        System.out.print("Second Array:  ");
        System.out.println(Arrays.toString(arr2));
    }
}
Output
After Merging First Array: [1, 2, 12, 9, 3, 3]
Second Array: [8, 13, 17, 20]
Related Pages
Given an array which consists of only 0, 1 and 2

Move all the negative elements to one side of the array

Find the Union and Intersection of the two sorted arrays

Find Largest sum contiguous Subarray

Minimize the maximum difference between heights 

Method 2
The solution can be further optimised by observing that if the jth second array element is smaller than the ith first array element while traversing the two sorted arrays parallelly, then the jth element is to be included and replace some kth element in the first array. This observation aids us in developing the following algorithm.

1) Set i,j,k to 0,0,n-1, with n equal to the size of arr1.
2) Iterate through each element of arr1 and arr2 using two pointers I and j, respectively;
            if arr1[i] is less than arr2[j], 
2) Iterate through each element of arr1 and arr2 using two pointers I and j, respectively.

             If arr1[i] is less than arr2[j], increment I

            otherwise, swap arr2[j] and arr1[k].j should be increased, while k should be decreased.

3) Arrange arr1 and arr2 together.

Run
import java.util.Arrays;
public
class Main {
    static int arr1[] = new int[]{1, 12, 9, 3, 17, 20};
    static int arr2[] = new int[]{2, 3, 8, 13};
    static void merge(int m, int n) {
        // Iterate through all elements of ar2[] starting from
        // the last element
        for (int i = n - 1; i >= 0; i--) {
            int j, last = arr1[m - 1];
            for (j = m - 2; j >= 0 && arr1[j] > arr2[i]; j--) arr1[j + 1] = arr1[j];
            // If there was a greater element
            if (j != m - 2 || last > arr2[i]) {
                arr1[j + 1] = arr2[i];
                arr2[i] = last;
            }
        }
    }
    // Driver method to test the above function
    public
    static void main(String[] args) {
        merge(arr1.length, arr2.length);
        System.out.print("After Merging First Array: ");
        System.out.println(Arrays.toString(arr1));
        System.out.print("Second Array:  ");
        System.out.println(Arrays.toString(arr2));
    }
}
After Merging First Array: [1, 2, 3, 6, 8, 13]
Second Array: [0, 15, 19, 20]
Prime Course Trailer

Related Banners
Get PrepInsta Prime & get Access to all 200+ courses offered by PrepInsta in One Subscription

Get Prime
Login/Signup to comment


Palak Gupta
public static void mergetwosorted(int arr1[],int arr2[]){
int n=arr1.length;
int m=arr2.length;
int i=0;
int j=0;
while(iarr2[j]){
//swap the program
int temp=arr1[i];
arr1[i]=arr2[j];
arr2[j]=temp;
sortedarr2(arr2);

}
i++;
}
System.out.println(Arrays.toString(arr1)+Arrays.toString(arr2));
}
//This is a helping function of mergesorted array
public static void sortedarr2(int arr2[]){
for(int i=0;iarr2[i+1]){
int temp=arr2[i+1];
arr2[i+1]=arr2[i];
arr2[i]=temp;

}
}
} want to more solution so you can check my Github “https://github.com/Palakgupta2002”
