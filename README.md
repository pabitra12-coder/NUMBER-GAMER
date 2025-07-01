# NUMBER-GAMER
Task-1


import java.util.Scanner;
import java.util.Random;

public class new_project {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Random random = new Random();
        int totalScore = 0;
        int round = 1;

        System.out.println(" Welcome to the Number Guessing Game!");

        boolean playAgain = true;
        while (playAgain) {
            int numberToGuess = random.nextInt(100) + 1; // 1 to 100
            int attemptsLeft = 7;
            boolean guessedCorrectly = false;

            System.out.println("\n Round " + round + ":");
            System.out.println("I'm thinking of a number between 1 and 100.");
            System.out.println("You have " + attemptsLeft + " attempts. Good luck!");

            while (attemptsLeft > 0) {
                System.out.print("Enter your guess: ");
                int userGuess = scanner.nextInt();

                if (userGuess == numberToGuess) {
                    System.out.println("Correct! You guessed the number.");
                    totalScore += attemptsLeft * 10; // Score based on attempts left
                    guessedCorrectly = true;
                    break;
                } else if (userGuess < numberToGuess) {
                    System.out.println("Too low!");
                } else {
                    System.out.println("Too high!");
                }
                attemptsLeft--;
                System.out.println("Attempts left: " + attemptsLeft);
            }

            if (!guessedCorrectly) {
                System.out.println("You're out of attempts! The number was: " + numberToGuess);
            }

            System.out.println("Your total score: " + totalScore);

            // Ask for next round
            System.out.print("Do you want to play another round? (yes/no): ");
            String response = scanner.next().toLowerCase();
            if (!response.equals("yes")) {
                playAgain = false;
                System.out.println(" Thanks for playing! Your final score: " + totalScore);
            }
            round++;
        }

        scanner.close();
    }
}
