#include <stdio.h>

int main() {
    int a[50], n, key;
    int low, high, mid;
    int comparisons = 0;
    int found = 0;

    printf("Enter number of employee IDs: ");
    scanf("%d", &n);

    printf("Enter employee IDs in ascending order:\n");
    for (int i = 0; i < n; i++) {
        scanf("%d", &a[i]);
    }

    printf("Enter employee ID to search: ");
    scanf("%d", &key);

    low = 0;
    high = n - 1;

    while (low <= high) {
        mid = (low + high) / 2;
        comparisons++;

        if (a[mid] == key) {
            printf("Employee ID found at position %d\n", mid + 1);
            found = 1;
            break;
        }
        else if (key < a[mid]) {
            high = mid - 1;
        }
        else {
            low = mid + 1;
        }
    }

    if (found == 0) {
        printf("Employee ID not found\n");
    }

    printf("Number of comparisons = %d\n", comparisons);

    return 0;
}



<img width="363" height="153" alt="Screenshot 2026-10-02 at 1 51 15 PM" src="https://github.com/user-attachments/assets/73726dee-ce63-47a1-aae6-6118f3b13004" />
<img width="340" height="151" alt="Screenshot 2026-10-02 at 1 52 57 PM" src="https://github.com/user-attachments/assets/eed21b62-92a5-4c18-812d-463721fe750b" />


