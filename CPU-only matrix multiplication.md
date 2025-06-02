```C
#include <stdio.h>

#define SIZE 3

void multiply_matrices(int M[SIZE][SIZE], int N[SIZE][SIZE], int P[SIZE][SIZE]) {
    for (int i = 0; i < SIZE; ++i) {
        for (int j = 0; j < SIZE; ++j) {
            P[i][j] = 0; // initialize result cell
            for (int k = 0; k < SIZE; ++k) {
                P[i][j] += M[i][k] * N[k][j];
            }
        }
    }
}

void print_matrix(int matrix[SIZE][SIZE]) {
    for (int i = 0; i < SIZE; ++i) {
        for (int j = 0; j < SIZE; ++j) {
            printf("%4d", matrix[i][j]);
        }
        printf("\n");
    }
}

int main() {
    int M[SIZE][SIZE] = {
        {1, 2, 3},
        {4, 5, 6},
        {7, 8, 9}
    };

    int N[SIZE][SIZE] = {
        {9, 8, 7},
        {6, 5, 4},
        {3, 2, 1}
    };

    int P[SIZE][SIZE]; // result matrix

    multiply_matrices(M, N, P);

    printf("Matrix M:\n");
    print_matrix(M);

    printf("\nMatrix N:\n");
    print_matrix(N);

    printf("\nProduct Matrix P = M * N:\n");
    print_matrix(P);

    return 0;
}
```