# DSA_Sequential_Search_p1
This C program generates an array  randomly  and performs a Sequential Search  to find a randomly selected key from the array. The program measures and displays both CPU time and wall clock time taken during the search.


#include <stdio.h>
#include <stdlib.h>
#include <time.h>

void Sequential_Search(int a[], int size, int Key) {
    printf("\nSearch for key: %d\n", Key);

    clock_t startClock = clock();
    time_t startTime = time(NULL);

    for (int i = 0; i < size; i++) {
    
        double elapsed = (double)(clock() - startClock) / CLOCKS_PER_SEC;

        printf("[%d] = %d  (%.3f sec )\n", i, a[i], elapsed);

        if (a[i] == Key) {
            printf("  MATCH FOUND!\n");

            clock_t endClock = clock();
            time_t endTime = time(NULL);

            double cpuTime = (double)(endClock - startClock) / CLOCKS_PER_SEC;
            double wallTime = difftime(endTime, startTime);

            printf("Key %d found at index %d\n", Key, i);
      
            printf("Start time: %s", ctime(&startTime));  
            printf("End time:   %s", ctime(&endTime));
            printf("CPU Time:   %.6f seconds\n", cpuTime);
            printf("Wall Time:  %.2f seconds\n", wallTime);
            return;
        }
    }

    printf("Key %d not found in the array.\n", Key);

}

int main() {
    int size = 10;
    int n = 1;  // number of searches
    int a[size];

    srand((unsigned int)time(NULL));

    printf("Generated Array:\n");
    for (int i = 0; i < size; i++) {
        a[i] = rand() % 1000 + 1;
        printf("[%d] = %d  (%.3f sec CPU elapsed)\n", i, a[i], (double)clock() / CLOCKS_PER_SEC);
    }

    for (int i = 1; i <= n; i++) {
        int key = a[rand() % size];
        Sequential_Search(a, size, key);
    }

    return 0;
}
