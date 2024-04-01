# OTH-1203230037

Pinaringan Iman Santoso
1203230037 - INFORMATIKA

SOAL LATIHAN ASD - STRUCT DAN STACK

1. ASISTEN HERLOCK HOLMES
SOURCE CODE :

    #include <stdio.h>
    #include <stdlib.h>
    
    // Definisikan struktur node
    struct Node {
        char alphabet;
        struct Node* link;
    };
    
    int main() {
        // Inisialisasi semua node
        struct Node l1, l2, l3, l4, l5, l6, l7, l8, l9;
        // Mengisi data pada setiap node
        l1.link = NULL;
        l1.alphabet = 'F';
        l2.link = NULL;
        l2.alphabet = 'M';
        l3.link = NULL;
        l3.alphabet = 'A';
        l4.link = NULL;
        l4.alphabet = 'I';
        l5.link = NULL;
        l5.alphabet = 'K';
        l6.link = NULL;
        l6.alphabet = 'T';
        l7.link = &l4; // Menghubungkan l7 (N) ke l4 (I)
        l7.alphabet = 'N';
        l8.link = &l3; // Menghubungkan l8 (O) ke l3 (A)
        l8.alphabet = 'O';
        l9.link = &l8; // Menghubungkan l9 (R) ke l8 (O)
        l9.alphabet = 'R';
    
        // Starting point
        struct Node* current = &l3;
    
        // Traversal dari starting point hingga mencapai akhir
        while (current != NULL) {
            printf("%c", current->alphabet);
            current = current->link;
        }
    
        printf("\n");
    
        return 0;
    }

   OUTPUT :

   ![image](https://github.com/Santosyouknow/OTH-1203230037/assets/161540041/5c7e2211-4236-42b0-ba8b-869047f56378)

   PENJELASAN LENGKAP PROSES CODE TERSEBUT :

   Tentu, saya akan menjelaskan setiap baris kode secara lengkap:

  1. `#include <stdio.h>`: Baris ini adalah direktif preprosesor yang menginstruksikan kompiler untuk menyertakan file header `stdio.h`. File header ini diperlukan karena kita akan menggunakan fungsi `printf()` untuk mencetak output.
  
  2. `#include <stdlib.h>`: Direktif preprosesor kedua yang menyertakan file header `stdlib.h`. File header ini diperlukan karena kita akan menggunakan fungsi `malloc()` untuk alokasi memori.
  
  3. `struct Node { char alphabet; struct Node* link; };`: Ini adalah definisi struktur `Node` yang memiliki dua anggota, yaitu `alphabet` yang merupakan karakter dan `link` yang merupakan pointer ke node berikutnya dalam linked list.
  
  4. `int main() {`: Ini adalah awal dari fungsi `main()` yang merupakan titik masuk utama dari program C.
  
  5. `struct Node l1, l2, l3, l4, l5, l6, l7, l8, l9;`: Baris ini mendeklarasikan sembilan variabel bertipe `struct Node` yaitu `l1`, `l2`, ..., `l9`. Dengan demikian, kita telah membuat sembilan node.
  
  6. `l1.link = NULL; l1.alphabet = 'F';`: Inisialisasi node pertama (`l1`) dengan `link` yang menunjuk ke `NULL` (tidak ada koneksi) dan `alphabet` diisi dengan huruf `'F'`.
  
  7. Baris 6 hingga 9 melakukan hal yang sama dengan baris 6, yaitu melakukan inisialisasi pada masing-masing node dengan `link` yang menunjuk ke `NULL` dan mengisi `alphabet` dengan huruf yang sesuai.
  
  8. `l7.link = &l4; l7.alphabet = 'N';`: Di sini, kita menghubungkan node `l7` (huruf 'N') dengan node `l4` (huruf 'I') dengan cara menetapkan `link` dari `l7` menunjuk ke alamat dari `l4`. Ini sesuai dengan arah panah pada teka-teki.
  
  9. `l8.link = &l3; l8.alphabet = 'O';`: Kita menghubungkan node `l8` (huruf 'O') dengan node `l3` (huruf 'A') dengan cara yang sama seperti sebelumnya.
  
  10. `l9.link = &l8; l9.alphabet = 'R';`: Kita menghubungkan node `l9` (huruf 'R') dengan node `l8` (huruf 'O'), juga dengan cara yang sama.
  
  11. `struct Node* current = &l3;`: Kita mendefinisikan pointer `current` yang menunjuk ke node `l3`. Ini digunakan sebagai titik awal atau starting point untuk traversal.
  
  12. `while (current != NULL) {`: Ini adalah loop while yang akan dijalankan selama `current` tidak menunjuk ke `NULL`, yang menandakan akhir dari linked list.
  
  13. `printf("%c", current->alphabet);`: Di dalam loop, kita mencetak karakter yang disimpan di `current->alphabet`. Ini akan mencetak huruf yang ada di node saat ini.
  
  14. `current = current->link;`: Kita menggeser `current` ke node berikutnya dengan menetapkan `current` menjadi `current->link`, sehingga kita bisa melanjutkan traversal hingga mencapai akhir linked list.
  
  15. `printf("\n");`: Setelah traversal selesai, kita mencetak newline untuk membuat output lebih rapi.
  
  16. `return 0;`: Ini adalah akhir dari fungsi `main()` dan menandakan bahwa program telah selesai dijalankan dengan sukses.




2. SELESAIKAN SOAL HACKER RANK

   ![Screenshot 2024-03-31 213030](https://github.com/Santosyouknow/OTH-1203230037/assets/161540041/27bf6b34-3d67-4865-b79e-7fea3649df26)

   SOURCE CODE :
    
    #include <assert.h>
    #include <ctype.h>
    #include <limits.h>
    #include <math.h>
    #include <stdbool.h>
    #include <stddef.h>
    #include <stdint.h>
    #include <stdio.h>
    #include <stdlib.h>
    #include <string.h>
    
    char* readline();
    char* ltrim(char*);
    char* rtrim(char*);
    char** split_string(char*);
    
    int parse_int(char*);
    
    /*
     * Complete the 'twoStacks' function below.
     *
     * The function is expected to return an INTEGER.
     * The function accepts following parameters:
     *  1. INTEGER maxSum
     *  2. INTEGER_ARRAY a
     *  3. INTEGER_ARRAY b
     */
    
    int twoStacks(int maxSum, int a_count, int* a, int b_count, int* b) {
        int i = 0, j = 0;
        long long int sum = 0; // Menggunakan long long int untuk menangani jumlah yang besar
        int count = 0;
    
        // Mengambil elemen dari tumpukan pertama (a)
        while (i < a_count && sum + a[i] <= maxSum) {
            sum += a[i];
            i++;
            count++;
        }
    
        int maxCount = count; // Inisialisasi jumlah maksimum yang sudah diambil dari tumpukan pertama
    
        // Mengambil elemen dari tumpukan kedua (b) dengan mempertimbangkan elemen yang telah diambil dari tumpukan pertama (a)
        while (j < b_count && i >= 0) {
            sum += b[j];
            j++;
    
            // Mengurangi nilai elemen dari tumpukan pertama (a) sampai total sum menjadi kurang dari atau sama dengan maxSum
            while (sum > maxSum && i > 0) {
                i--;
                sum -= a[i];
            }
    
            // Memeriksa apakah jumlah elemen yang diambil dari kedua tumpukan lebih besar dari jumlah sebelumnya
            if (sum <= maxSum && i + j > maxCount) {
                maxCount = i + j;
            }
        }
    
        return maxCount; // Mengembalikan jumlah maksimum elemen yang dapat diambil dari kedua tumpukan
    }
    
    int main() {
        FILE* fptr = fopen(getenv("OUTPUT_PATH"), "w");
    
        int g = parse_int(ltrim(rtrim(readline())));
    
        for (int g_itr = 0; g_itr < g; g_itr++) {
            char** first_multiple_input = split_string(rtrim(readline()));
    
            int n = parse_int(*(first_multiple_input + 0));
    
            int m = parse_int(*(first_multiple_input + 1));
    
            int maxSum = parse_int(*(first_multiple_input + 2));
    
            char** a_temp = split_string(rtrim(readline()));
    
            int* a = malloc(n * sizeof(int));
    
            for (int i = 0; i < n; i++) {
                int a_item = parse_int(*(a_temp + i));
    
                *(a + i) = a_item;
            }
    
            char** b_temp = split_string(rtrim(readline()));
    
            int* b = malloc(m * sizeof(int));
    
            for (int i = 0; i < m; i++) {
                int b_item = parse_int(*(b_temp + i));
    
                *(b + i) = b_item;
            }
    
            int result = twoStacks(maxSum, n, a, m, b);
    
            fprintf(fptr, "%d\n", result);
        }
    
        fclose(fptr);
    
        return 0;
    }
    
    char* readline() {
        size_t alloc_length = 1024;
        size_t data_length = 0;
    
        char* data = malloc(alloc_length);
    
        while (true) {
            char* cursor = data + data_length;
            char* line = fgets(cursor, alloc_length - data_length, stdin);
    
            if (!line) {
                break;
            }
    
            data_length += strlen(cursor);
    
            if (data_length < alloc_length - 1 || data[data_length - 1] == '\n') {
                break;
            }
    
            alloc_length <<= 1;
    
            data = realloc(data, alloc_length);
    
            if (!data) {
                data = '\0';
    
                break;
            }
        }
    
        if (data[data_length - 1] == '\n') {
            data[data_length - 1] = '\0';
    
            data = realloc(data, data_length);
    
            if (!data) {
                data = '\0';
            }
        } else {
            data = realloc(data, data_length + 1);
    
            if (!data) {
                data = '\0';
            } else {
                data[data_length] = '\0';
            }
        }
    
        return data;
    }
    
    char* ltrim(char* str) {
        if (!str) {
            return '\0';
        }
    
        if (!*str) {
            return str;
        }
    
        while (*str != '\0' && isspace(*str)) {
            str++;
        }
    
        return str;
    }
    
    char* rtrim(char* str) {
        if (!str) {
            return '\0';
        }
    
        if (!*str) {
            return str;
        }
    
        char* end = str + strlen(str) - 1;
    
        while (end >= str && isspace(*end)) {
            end--;
        }
    
        *(end + 1) = '\0';
    
        return str;
    }
    
    char** split_string(char* str) {
        char** splits = NULL;
        char* token = strtok(str, " ");
    
        int spaces = 0;
    
        while (token) {
            splits = realloc(splits, sizeof(char*) * ++spaces);
    
            if (!splits) {
                return splits;
            }
    
            splits[spaces - 1] = token;
    
            token = strtok(NULL, " ");
        }
    
        return splits;
    }
    
    int parse_int(char* str) {
        char* endptr;
        int value = strtol(str, &endptr, 10);
    
        if (endptr == str || *endptr != '\0') {
            exit(EXIT_FAILURE);
        }
    
        return value;
    }

   * TAMBAHAN VISUALISASI JIKA INPUTAN DI RUBAH MAKA

     Tentu, mari kita jelaskan lebih lengkap dan benar.

Input:
```
1
5 4 11
4 5 2 1 1
3 1 1 2
```

Langkah-langkah:

1. **Inisialisasi Tumpukan (Stacks):**
   - Inisialisasi tumpukan pertama (Stack A) dengan elemen:
     ```
     4 5 2 1 1
     ```
   - Inisialisasi tumpukan kedua (Stack B) dengan elemen:
     ```
     3 1 1 2
     ```

2. **Pengambilan Elemen dari Stack A:**
   - Lakukan pengambilan elemen dari Stack A sampai jumlahnya melebihi `maxSum` atau hingga Stack A kosong:
     - Ambil elemen 4. Total sum menjadi 4.
     - Ambil elemen 5. Total sum menjadi 9.
     - Ambil elemen 2. Total sum menjadi 11.

3. **Pengambilan Elemen dari Stack B:**
   - Setelah mengambil semua elemen dari Stack A yang memenuhi kriteria, lakukan pengambilan elemen dari Stack B satu per satu sambil mempertimbangkan total sum:
     - Ambil elemen 3. Total sum menjadi 14.
     - Ambil elemen 1. Total sum menjadi 15.
     - Ambil elemen 1. Total sum menjadi 16.
     - Ambil elemen 2. Total sum menjadi 18.

4. **Pemeriksaan Kembali Total Sum:**
   - Total sum sekarang telah melebihi `maxSum`. Oleh karena itu, perlu dilakukan pengurangan elemen dari Stack A untuk memastikan bahwa total sum tidak melebihi `maxSum`.

5. **Pengurangan Elemen dari Stack A:**
   - Lakukan pengurangan elemen dari Stack A satu per satu hingga total sum tidak melebihi `maxSum`:
     - Hapus elemen 2 dari Stack A. Total sum menjadi 16.
     - Total sum masih melebihi `maxSum`, lanjutkan pengurangan:
       - Hapus elemen 1 dari Stack A. Total sum menjadi 15.
     - Sekarang total sum tidak melebihi `maxSum`, maka pengurangan dihentikan.

6. **Hasil Akhir:**
   - Setelah mengambil dan mengurangi elemen dari kedua Stack, hasil akhirnya adalah:
     ```
     Stack A: 4 5
     Stack B: 3 1 1
     ```
     Total elemen yang diambil dari kedua Stack adalah 5.

Dalam proses ini, strategi yang digunakan adalah mengambil elemen dari Stack A sebanyak mungkin sampai total sum melebihi `maxSum`, kemudian mempertimbangkan elemen dari Stack B sambil memastikan total sum tidak melebihi `maxSum`, dan terakhir melakukan pengurangan dari Stack A jika diperlukan untuk memastikan total sum tidak melebihi `maxSum`.


