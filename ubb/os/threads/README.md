#Threads
###Useful Links
- [Rares](http://www.cs.ubbcluj.ro/~rares/course/os/res/lab_examples/thr/)
- [Alina Calin](https://www.cs.ubbcluj.ro/~alinacalin/SO/)
- [Mihai Suciu](https://www.cs.ubbcluj.ro/~mihai-suciu/)
- [Daniel](https://www.cs.ubbcluj.ro/~daniel/so/)

###Practical Processes and Threads
1. *Suciu* Sa se scrie un program care primeste ca si argumente nume de programe urmate de argumente. Numele unui program este de separat de ultimul argument al progrmaului precedent prin -. Programul va rula programele primilte ca argumente cu parametrii corespunzatori in procese fiu simultane folosing apelurile sistem exec. In cazul in care apelul exec esaueaza, se va raporta un mesaj de eroare si codul de eroare.
Ex: `./aprog /bin/ls /etc - /usr/bin/wc /etc/passwd - /bin/grep aa /etc/passwd`
    - **FILE: `cacat.c`**

2. *Grebla(?)* Implement two processes in C that communicate through PIPE. Process A sends a string to process B, B eliminates maximum 3 vowels from it and sends it back to A, which eliminates also maximum 3 vowels, and sends it back to B and so on. The processes stop when they either receive or send a string that does not contain vowels.
    - **FILE: `vowel.c`**

4. *Greba* Se creeaza un subproces. Se creeaza 2 thread-uri in subproces. Threadurile citesc cate un numar (alternativ) si il aduna la o suma. Se repeta cat timp suma < 100. Din subproces, se transmite printr-un pipe rezultatul la procesul principat. Procesul principal afiseaza rezultatul.
    - **FILE `grebla.c`**

5. Faci 10 procese. din fiecare 2 threaduri. fiecare thread genereaza random numere, si adauga la o suma threadurile genereaza alternativ t1, t2, t1, t2 pana cand ai generat 10 numere in total. si dupa aia, din subproces trimiti inapoi o structura care contine suma si pid-ul. mainul scrie PID-ul si suma procesului care a facut max
    - **FILE `tamas.c`**

6. Creezi un subproces care creeaza 10 threaduri si in thread se genereaza numere random pana cand is cel putin 5 intre 1-300, 5 intre 301-600, 5 intre 601-900, si la final trimiti cate s-au generat din fiecare in procesul principal prin fifo.
    - **FILE `varan.c`** - The moment when you compile a reptile

7. Implementati un program C care are un tablou global de 10 int-uri numti "suma\_dupa\_rest". Programul va crea 7 threaduri, ficare dintre ele generand 100 de numere aleatoare. Fiecare numar va fi adunat la elemntul tabloului "suma\_dupa\_rest" corespunzator restului impartirii numarluliu la 10. Folositi mecanismele de sincronizare necesare pentru a asigura aclcularea corecta a sumelor.
    - **FILE `dana.c`**


###Test - 25 min
Username impar:

1. Sa se scrie un program care primeste numere intregi ca si argumente in linia de comanda. Pentru fiecare argument, programul lanseaza un thread   care verifica daca numarul e divizibil cu 2, 3, 5 sau 7, afiseaza rezultatul    in caz afirmativ si incrementeaza una din variabilele globale comune ce contorizeaza    cate numere sunt divizibile cu 2, 3, 5 sau 7.   Programul principal afiseaza rezultatul final obtinut (cate numere sunt divizibile   cu 2, 3, 5 sau 7) si se termina.

EX: ./program1  2 3 4 5 6 11
    Divizibile cu 2: 3
    Divizibile cu 3: 2
    Divizibile cu 5: 1
    Divizibile cu 7: 0

Username par:

2. Sa se scrie un program care creeaza 7 thread-uri si are 3 variabile globale ce contorizeaza numerele cu o cifra, cu doua cifre sau mai mari.   Fiecare thread va genera numere aleatoare intre 0 si 1000, si in functie de numarul obtinut   incrementeaza contorul globasl corespunzator si printeaza valoarea obtinuta. Thread-urile se opresc cand   s-au generat cel putin 5 numere din fiecare categorie. Programul principal afiseaza cele 3 variabile  globale si apoi se termina.

EX: ./prog2
    Numere generate: 2 45 760 4 9 609 76 107 56 425 39 5 78 999 549 8
    1 cifra: 5
    2 cifre: 5
    mai mari: 6

###Projects
1. Implement a program that writes a number between 0 and 9 in a global variable and then creates 10 threads. Each thread will check the global variable and if its value is the order number of the thread (given from main at creation time), the thread writes in the global variable another number between 0 and 9 (different than its own). The program ends when the global variable is changed 20 times.
    - **FILE: cosmin.c**

2. Calculate the sum of the elements in a bidimensional matrix, using a separate thread to calculate the sum of each row. The main thread adds up these sums printing the final result.
    - **FILE: robert.c**

3. Implement a program that creates two threads. The threads will print their ID (pthread_self) 10 times and then stop. Insure that the printed IDs alternate always (ie A, B, A, B, ...)
    - **FILE: serg.c**

4. Implement a program that gets as arguments a file name followed by words. For each word, create a separate thread that counts its appearances in the given file.  Print out the sum of the appearances of all words.
    - **FILE: andra.c - personal implementation**
    - **FILE: stana.c - Andra Stana's implementation (ugly, right?)**

###Extra
1.  Write a program that creates 4 threads and had 3 global variables v5, v2, v3. Each thread generates a random number and:
    - if the number is multiple of 2 increments v2
    - if the number is multiple of 3 increments v3
    - if the number is multiple of 5 increments v5

    The number can be a multiple of more numbers (ex. for 10 we will increment both V2 and V5). Threads print the generated numbers and stop when 30 numbers have been generated. The main program prints the 3 global variables.
    - **FILE: var.c**

2. Write a program that creates threads and increments a global variable n=0 with the values from a struct given as argument to each thread until it is greater than 20. The struct contains for each thread 2 random numbers generated in the main program.
    - **FILE: inc.c**

3. Write a C program that receives as arguments file names and processes them simultaneously using threads. The program transforms the files so that all words will begin with a capital letter. The modified files (containing the first letter words capitalized) will have the same name as the original files and will end woth the number N (N is the thread id). You will create a thread for each file.
    - **FILE: suciu.c**

###Instructions
-   For compiling, run the following command in a terminal:
    -   `gcc -Wall -pthread cosmin.c`
-   This command will compile the file cosmin.c and if everything is good, it will create an executable file a.out on the current directory.
-   Now just run the exectubale file as follows
    -   `./a.out`
-   If you want to check your program for memory leaks run:
    -   `valgrind ./a.out` and carefully read everything
