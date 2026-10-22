#include <stdio.h>

int search(int nums[], int n, int target)
{
    int left = 0;
    int right = n - 1;

    while (left <= right)
    {
        int mid = left + (right - left) / 2;

        if (nums[mid] == target)
        {
            return mid;
        }
        else if (nums[mid] < target)
        {
            left = mid + 1;
        }
        else
        {
            right = mid - 1;
        }
    }

    return -1;
}

int main()
{
    int nums[] = {1, 3, 5, 7, 9};
    int n = 5;
    int target = 5;

    int result = search(nums, n, target);

    printf("%d\n", result);

    return 0;
} 

<img width="89" height="48" alt="Screenshot 2026-10-22 at 9 43 19 PM" src="https://github.com/user-attachments/assets/25041fde-5a45-4dac-845b-0b83542e0921" />
