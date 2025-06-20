# Library-Management-using-c
A simple Library Management System written in C that allows users to manage book records efficiently. This project includes basic functionalities such as adding, deleting, searching, and issuing books.
#include <stdio.h>
#include <string.h>

struct Book {
    int id;
    char title[100];
    char author[100];
};

int main() {
    struct Book library[100];
    int choice, count = 0, i, searchId;

    while (1) {
        printf("\nLibrary Menu:\n");
        printf("1. Add Book\n2. Display Books\n3. Search Book by ID\n4. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);
        getchar(); // to consume newline

        switch (choice) {
            case 1:
                printf("Enter Book ID: ");
                scanf("%d", &library[count].id);
                getchar();
                printf("Enter Book Title: ");
                fgets(library[count].title, sizeof(library[count].title), stdin);
                printf("Enter Author Name: ");
                fgets(library[count].author, sizeof(library[count].author), stdin);
                count++;
                printf("Book added successfully!\n");
                break;

            case 2:
                printf("\nAll Books in Library:\n");
                for (i = 0; i < count; i++) {
                    printf("ID: %d | Title: %s | Author: %s", library[i].id, library[i].title, library[i].author);
                }
                break;

            case 3:
                printf("Enter Book ID to search: ");
                scanf("%d", &searchId);
                for (i = 0; i < count; i++) {
                    if (library[i].id == searchId) {
                        printf("Book Found!\nTitle: %sAuthor: %s", library[i].title, library[i].author);
                        break;
                    }
                }
                if (i == count) printf("Book not found.\n");
                break;

            case 4:
                printf("Exiting...\n");
                return 0;

            default:
                printf("Invalid choice! Try again.\n");
        }
    }

    return 0;
}
