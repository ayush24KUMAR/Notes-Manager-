# Notes-Manager-
import java.io.*;
import java.util.*;

public class SimpleNotesManager {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String fileName = "notes.txt";

        while (true) {
            System.out.println("\n==== Simple Notes Manager ====");
            System.out.println("1. Add Note");
            System.out.println("2. View Notes");
            System.out.println("3. Exit");
            System.out.print("Choose option: ");
            int choice = sc.nextInt();
            sc.nextLine();  // clear the newline

            if (choice == 1) {
                System.out.print("Enter note: ");
                String note = sc.nextLine();
                try {
                    FileWriter fw = new FileWriter(fileName, true); // append mode
                    fw.write(note + "\n");
                    fw.close();
                    System.out.println("Note saved.");
                } catch (IOException e) {
                    System.out.println("Error saving note.");
                }

            } else if (choice == 2) {
                System.out.println("\nYour Notes:");
                try {
                    File file = new File(fileName);
                    Scanner reader = new Scanner(file);
                    while (reader.hasNextLine()) {
                        System.out.println("- " + reader.nextLine());
                    }
                    reader.close();
                } catch (FileNotFoundException e) {
                    System.out.println("No notes found.");
                }

            } else if (choice == 3) {
                System.out.println("Goodbye!");
                break;
            } else {
                System.out.println("Invalid choice. Try again.");
            }
        }

        sc.close();
    }
}
