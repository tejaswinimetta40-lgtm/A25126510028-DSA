#include <stdio.h>

int searchInsert(int nums[], int n, int target)
{
    int left = 0;
    int right = n - 1;

    while (left <= right)
    {
        int mid = left + (right - left) / 2;

        if (nums[mid] == target)
            return mid;
        else if (nums[mid] < target)
            left = mid + 1;
        else
            right = mid - 1;
    }

    return left;
}

int main()
{
    int nums[] = {1, 3, 5, 6};
    int n = 4;
    int target = 2;

    printf("%d\n", searchInsert(nums, n, target));

    return 0;
} 
<img width="104" height="50" alt="Screenshot 2026-10-22 at 9 46 48 PM" src="https://github.com/user-attachments/assets/32fc2e29-e405-4f69-abc3-4bf1aa19143e" />
