#include <stdio.h>

int main() {
    int a[50], n;
    int i, j, key;
    int shifts = 0;

    printf("Enter number of students: ");
    scanf("%d", &n);

    printf("Enter marks:\n");
    for (i = 0; i < n; i++) {
        scanf("%d", &a[i]);
    }

    for (i = 1; i < n; i++) {
        key = a[i];
        j = i - 1;

        while (j >= 0 && a[j] > key) {
            a[j + 1] = a[j];
            j--;
            shifts++;
        }

        a[j + 1] = key;

        printf("After pass %d: ", i);
        for (int k = 0; k < n; k++) {
            printf("%d ", a[k]);
        }
        printf("\n");
    }

    printf("Final sorted list: ");
    for (i = 0; i < n; i++) {
        printf("%d ", a[i]);
    }

    printf("\nTotal element shifts = %d\n", shifts);

    return 0;
}

<img width="315" height="216" alt="Screenshot 2026-10-02 at 2 24 19 PM" src="https://github.com/user-attachments/assets/9e4d3397-2d3c-4774-aa0f-bf01b04ae9a2" />
