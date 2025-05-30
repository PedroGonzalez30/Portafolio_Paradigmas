+++
date = '2025-02-21T08:44:04-08:00'
title = 'Practica1'
+++

# __PRACTICA 1__

## Elementos básicos de los lenguajes de programación

__Nombres:__
 Son identificadores utilizados para variables, funciones, tipos, estructuras, etc.
Variables: static_var, bss_var, book_t *library, member_t *members, int bookCount, etc.
Funciones: addBook(), displayBooks(), issueBook(), etc.
Tipos: book_t, member_t, genre_t.

__Marcos de activación__     
Sirve para invocar las funciones.

```C++
    const char* genreToString(genre_t genre);
    void addBook(book_t **library, int* count);
    book_t* findBookById(book_t *library, int bookID);
    void displayBooksRecursive(book_t *library);
    void displayBooks(book_t *library);
    void addMember(member_t **members, int *memberCount);
    void issueBook(book_t *library, member_t *members);
    void returnBook(book_t *library, member_t *members);
    void freeLibrary(book_t *library);
    void freeMembers(member_t *members);
    void saveLibraryToFile(book_t *library, const char *filename);
    void loadLibraryFromFile(book_t **library, int *bookCount, const char *filename);
    void saveMembersToFile(member_t *members, const char *filename);
    void loadMembersFromFile(member_t **members, int *memberCount, const char *filename);
    void displayMembers(member_t *members, book_t *library);
    void searchMember(member_t *members, book_t *library);
```

__Bloques de alcance__
Define el ámbito en el cual una variable es visible y accesible, el alcance puede ser local o global.

```C++
    void addBook(book_t **library, int* count ) {
    // Asignacion de memoria en el heap
    book_t *new_book = (book_t *)malloc(sizeof(book_t));
    if (!new_book) {
        printf("Error al asignar memoria para el nuevo libro.\n");
        return;
    }
    incrementHeapAllocations(new_book, sizeof(book_t));
    printf("Memoria asignada para un nuevo libro (ID: %d) en el heap\n", new_book->id);

    printf("\nIngresa ID del libro: ");
    scanf("%d", &new_book->id);

    printf("Ingresa titulo del libro: ");
    getchar();
    fgets(new_book->title, 100, stdin);
    new_book->title[strcspn(new_book->title, "\n")] = '\0';

    printf("Ingresa nombre del autor: ");
    fgets(new_book->author, 100, stdin);
    new_book->author[strcspn(new_book->author, "\n")] = '\0';

    printf("Ingresa el ano de publicacion: ");
    scanf("%d", &new_book->publication_year);

    printf("Ingresa el genero del libro (0: FICTION, 1: NON_FICTION, 2: SCIENCE, 3: HISTORY, 4: FANTASY, 5: BIOGRAPHY, 6: OTHER): ");
    int genre;
    scanf("%d", &genre);
    new_book->genre = (genre_t)genre;

    printf("Ingresa la cantidad de libros: ");
    scanf("%d", &new_book->quantity);

    new_book->next = *library;
    *library = new_book;
    (*count)++;

    printf("\nEl libro fue agregado exitosamente!\n");
    displayMemoryUsage();
}
```


__Administración de memoria__
Por ejemplo usar memoria dinámica.


```C++
while (!feof(file)) 
{
        book_t *new_book = (book_t *)malloc(sizeof(book_t));
        if (!new_book) {
            printf("Error al asignar memoria para el nuevo libro.\n");
            fclose(file);
            return;
        }
}
```



__Expresiones.__
Son combinaciones de variables, constantes, operadores y funciones que producen un valor.

```C++
  bookFound->quantity++;
```


__Comandos.__
Instrucciones que ejecutan acciones.

```C++
 printf("\nIngresa el ID del miembro: ");
    scanf("%d", &memberID);
```


__Control de secuencia:__
Orden en que se ejecutan las instrucciones
* __Selección;__ Se usan las instrucciones if y switch para tomar decisiones.

```C++
switch (choice) {
            case 1:
                addBook(&library, &bookCount);
                break;
            case 2:
                displayBooks(library);
                break;
}
```

* __Iteración;__ Se utilizan bucles while y for para repetir bloques de código
  
```C++
while (!feof(file)) {
        member_t *new_member = (member_t *)malloc(sizeof(member_t));
        if (!new_member) {
            printf("Error al asignar memoria para el nuevo miembro.\n");
            fclose(file);
            return;
        }
}
```

* __Recursión;__


```C++
void displayBooksRecursive(book_t *library) {
    if (!library) {
        return;
    }
    printf("\nID libro: %d\nTitulo: %s\nAutor: %s\nAno de publicacion: %d\nGenero: %s\nCantidad: %d\n",
        library->id, library->title, library->author, library->publication_year, genreToString(library->genre), library->quantity);
    displayBooksRecursive(library->next);
}
```

__Subprogramas__
Son subprogramas que realizan tareas específicas.


```C++
void displayBooks(book_t *library) {
    if (!library) {
        printf("\nNo hay libros disponibles.\n");
        return;
    }

    printf("\nLibros disponibles en biblioteca:\n");
    displayBooksRecursive(library);
    displayMemoryUsage();
}
```

__Tipos de datos.__
Definen el tipo de información que una variable puede almacenar.    
int, float, char, etc.


[PAGINA](https://pedrogonzalez30.github.io/Portafolio_Paradigmas/)