# Library-Management-System
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        String[] bookTitles = new String[100];
        String[] bookAuthors = new String[100];
        int[] bookIDs = new int[100];
        int count = 0;
        while (true) {
            System.out.println("\n Library Management System ");
            System.out.println("1. Add Book");
            System.out.println("2. Remove Book");
            System.out.println("3. Search Book");
            System.out.println("4. List All Books");
            System.out.println("5. Exit");
            System.out.print("Enter your choice: ");
            int choice = scanner.nextInt();
            scanner.nextLine();
            switch (choice) {
                case 1:
                    if (count < 100) {
                        System.out.print("Enter Book ID: ");
                        bookIDs[count] = scanner.nextInt();
                        scanner.nextLine(); 
                        System.out.print("Enter Book Title: ");
                        bookTitles[count] = scanner.nextLine();
                        System.out.print("Enter Book Author: ");
                        bookAuthors[count] = scanner.nextLine();
                        count++;
                        System.out.println("Book added successfully!");
                    } else {
                        System.out.println("Library is full!");
                    }
                    break;
                case 2:
                    System.out.print("Enter Book ID to remove: ");
                    int removeId = scanner.nextInt();
                    boolean found = false;
                    for (int i = 0; i < count; i++) {
                        if (bookIDs[i] == removeId) {
                            for (int j = i; j < count - 1; j++) {
                                bookIDs[j] = bookIDs[j + 1];
                                bookTitles[j] = bookTitles[j + 1];
                                bookAuthors[j] = bookAuthors[j + 1];
                            }
                            count--;
                            found = true;
                            System.out.println("Book removed successfully!");
                            break;
                        }
                    }
                    if (!found) {
                        System.out.println("Book with ID " + removeId + " not found!");
                    }
                    break;
                case 3:
                    System.out.print("Enter Book Title or ID to search: ");
                    String query = scanner.nextLine();
                    found = false;
                    for (int i = 0; i < count; i++) {
                        if (bookTitles[i].equalsIgnoreCase(query) || String.valueOf(bookIDs[i]).equals(query)) {
                            System.out.println("Book Found: ID=" + bookIDs[i] + ", Title=" + bookTitles[i] + ", Author=" + bookAuthors[i]);
                            found = true;
                            break;
                        }
                    }
                    if (!found) {
                        System.out.println("No book found matching the query!");
                    }
                    break;
                case 4:
                    if (count == 0) {
                        System.out.println("No books in the library.");
                    } else {
                        System.out.println("Listing all books:");
                        for (int i=0; i < count; i++) {
                            System.out.println("ID=" + bookIDs[i] + ", Title=" + bookTitles[i] + ", Author=" + bookAuthors[i]);
                        }
                    }
                    break;
                case 5:
                    System.out.println("Exiting the system. Goodbye!");
                    scanner.close();
                    return;
                default:
                    System.out.println("Invalid choice! Please try again.");
            }
        }
    }
}
