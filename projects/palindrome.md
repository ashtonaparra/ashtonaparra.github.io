---
layout: project
type: project
image: img/tacoCat.jpg
title: "Palindrome checker"
date: 2023
published: true
labels:
  - String manipulation
  - Java
  - Project
summary: "A Java program that can identify if the users inputs are palindromes or not."
---

This Java program continuously checks if a given string is a palindrome by removing non-alphanumeric characters, ignoring case, and comparing the string forwards and backwards. The user can input multiple strings to check, and the program will keep running until "exit" is entered, at which point it terminates. If the string is a palindrome, the program displays a confirmation message, otherwise it informs the user that it's not a palindrome.

Here is the code if you are interested in the details:

```java
import java.util.Scanner;

public class PalindromeChecker {

    // Function to check if the input is a palindrome
    public static boolean isPalindrome(String input) {
        // Convert input to lowercase and remove non-alphanumeric characters
        String cleanedInput = input.replaceAll("[^a-zA-Z0-9]", "").toLowerCase();

        // Check if the cleaned string reads the same forwards and backwards
        int length = cleanedInput.length();
        for (int i = 0; i < length / 2; i++) {
            if (cleanedInput.charAt(i) != cleanedInput.charAt(length - i - 1)) {
                return false;
            }
        }
        return true;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        String input;

        // Continuous loop until the user types 'exit'
        while (true) {
            // Input from user
            System.out.println("Enter a string to check if it's a palindrome (or type 'exit' to quit): ");
            input = scanner.nextLine();

            // Exit condition
            if (input.equalsIgnoreCase("exit")) {
                System.out.println("Exiting the program.");
                break;
            }

            // Check and print the result
            if (isPalindrome(input)) {
                System.out.println("The input is a palindrome!");
            } else {
                System.out.println("The input is not a palindrome.");
            }
        }

        scanner.close();
    }
}

```
