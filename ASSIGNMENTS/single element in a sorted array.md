#include <stdio.h>

int singleNonDuplicate(int nums[], int n)
{
    int left = 0;
    int right = n - 1;

    while (left < right)
    {
        int mid = (left + right) / 2;

        if (mid % 2 == 1)
            mid--;

        if (nums[mid] == nums[mid + 1])
            left = mid + 2;
        else
            right = mid;
    }

    return nums[left];
}

int main()
{
    int nums[] = {1, 1, 2, 3, 3, 4, 4};
    int n = 7;

    printf("%d\n", singleNonDuplicate(nums, n));

    return 0;
} 

 <img width="142" height="57" alt="Screenshot 2026-10-22 at 9 48 46 PM" src="https://github.com/user-attachments/assets/1bda76c1-e99e-4ddb-a382-75504ad9472a" />
