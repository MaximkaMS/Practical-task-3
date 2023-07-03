# Practical-task-3
#include <stdio.h>

long long countNumbers(int r) {
    if (r < 1) {
        return 0;
    }

    long long dp[r + 1][2];
    // dp[i][0] - кількість чисел із i розрядів, остання цифра яких є 5
    // dp[i][1] - кількість чисел із i розрядів, остання цифра яких є 9

    dp[1][0] = 1;
    dp[1][1] = 1;

    for (int i = 2; i <= r; i++) {
        dp[i][0] = dp[i - 1][0] + dp[i - 1][1];
        dp[i][1] = dp[i - 1][0];
    }

    long long totalNumbers = dp[r][0] + dp[r][1];

    return totalNumbers;
}

int main() {
    int r;
    printf("Введіть кількість розрядів (р): ");
    scanf("%d", &r);

    long long result = countNumbers(r);

    printf("Кількість чисел із %d розрядів: %lld\n", r, result);

    return 0;
}
