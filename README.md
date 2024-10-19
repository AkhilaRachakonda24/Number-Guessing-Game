# Number-Guessing-Game
import java.util.Random;
import java.util.Scanner;

public class GuessTheNumber {
    
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Random random = new Random();
        int score = 0;
        int maxRounds = 3;
        int maxAttempts = 5;
        
        System.out.println("Welcome to the Guess the Number Game!");
        System.out.println("You have " + maxRounds + " rounds to play.");
        
        for (int round = 1; round <= maxRounds; round++) {
            System.out.println("\n--- Round " + round + " ---");
            int randomNumber = random.nextInt(100) + 1; // Random number between 1 and 100
            int attemptsLeft = maxAttempts;
            boolean hasGuessedCorrectly = false;

            while (attemptsLeft > 0) {
                System.out.print("Enter your guess (1-100): ");
                int userGuess = scanner.nextInt();
                attemptsLeft--;

                if (userGuess == randomNumber) {
                    System.out.println("Congratulations! You guessed the correct number.");
                    score += attemptsLeft + 1; // Points based on attempts left
                    hasGuessedCorrectly = true;
                    break;
                } else if (userGuess > randomNumber) {
                    System.out.println("The number is lower. Attempts left: " + attemptsLeft);
                } else {
                    System.out.println("The number is higher. Attempts left: " + attemptsLeft);
                }
            }

            if (!hasGuessedCorrectly) {
                System.out.println("Sorry, you didn't guess the number. It was: " + randomNumber);
            }
        }

        System.out.println("\nGame Over!");
        System.out.println("Your final score: " + score);
        scanner.close();
    }
}
